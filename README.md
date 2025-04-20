# BAI-TAP-5
VU LAN_K225480106036_Trigger on mssql


## SUBJECT: Trigger on mssql

A. Trình bày lại đầu bài của đồ án PT&TKHT:
1. Mô tả bài toán của đồ án PT&TKHT, 
   đưa ra yêu cầu của bài toán đó
2. Cơ sở dữ liệu của Đồ án PT&TKHT :
   Có database với các bảng dữ liệu cần thiết (3nf),
   Các bảng này đã có PK, FK, CK cần thiết
 
B. Nội dung Bài tập 05:
1. Dựa trên cơ sở là csdl của Đồ án
2. Tìm cách bổ xung thêm 1 (hoặc vài) trường phi chuẩn
   (là trường tính toán đc, nhưng thêm vào thì ok hơn,
    ok hơn theo 1 logic nào đó, vd ok hơn về speed)
   => Nêu rõ logic này!
3. Viết trigger cho 1 bảng nào đó, 
   mà có sử dụng trường phi chuẩn này,
   nhằm đạt được 1 vài mục tiêu nào đó.
   => Nêu rõ các mục tiêu 
4. Nhập dữ liệu có kiểm soát, 
   nhằm để test sự hiệu quả của việc trigger auto run.
5. Kết luận về Trigger đã giúp gì cho đồ án của em.

HƯỚNG DẪN CÁCH LÀM:

Hướng dẫn làm phần A: 
 - Chỉ cần nêu ra y/c của đồ án.
 - Không cần chụp quá trình làm ra db, tables.
 - Chỉ cần đưa ra db gồm các bảng nào,
   mỗi bảng có các trường nào, kiểu dữ liệu nào,
   và pk, fk, ck của các bảng.

Hướng dẫn làm phần B:
1. Sv tạo repo mới trên github, cho phép truy cập public.
2. Tạo file Readme.md, đầu file để thông tin cá nhân sv.
3. Tiếp theo đưa phần A vào file Reame.md .
3. Các thao tác làm trên csdl bằng phần mềm ssms.
4. Chụp ảnh màn hình quá trình làm.
5. Paste ngay vào Readme.md, 
   rồi gõ mô tả ảnh này làm gì, nhập gì, hay đạt được điều gì...
6. Có thể thêm những nhận xét hoặc kết luận
   cho việc bản thân đã hiểu rõ thêm về 1 vấn đề gì đó.
7. Lặp lại các step 4 5 6 cho đến khi hoàn thành yêu cầu của phần B.
8. Xuất các file sql chứa cấu trúc và data, up lên cùng repo.
9. Link đến repo cần mở được trực tiếp nội dung, 
   Paste link này vào file excel online ghim trên nhóm.
   Thầy sẽ dùng tool để check các link này.

DEADLINE: 23H59:59 NGÀY 23/04/2025

p/s:
 - Sv được phép tham khảo mọi nguồn, nhưng phải tự làm lại.
 - Đọc thêm nội quy học tập để biết các chế tài.
 - Đã đến lúc khẳng định bản thân và toả sáng!
 - Chỗ nào vướng mắc cứ share lên nhóm để cùng tháo gỡ.

## PHẦN A
## Phân tích thiết kế hệ thống mua bán hàng của một siêu thị WINMART

![image](https://github.com/user-attachments/assets/29b3e918-2a82-46de-84e3-3d706c0d484a)

![image](https://github.com/user-attachments/assets/342ecc69-3af6-405b-b2e3-9c6284ad8dcc)

### PHẦN B

**Trigger cập nhật tổng giá trị hóa đơn**

![image](https://github.com/user-attachments/assets/03f450bf-408b-4878-bce3-5e4ca9579123)

Go: kết thúc các hàng trước đó. Câu lệnh phía sau sẽ được thực hiện tiếp

CREATE TRIGGER trg_CapNhat_TongGiaHD: tạo một trigger mới tên là **trg_CapNhat_TongGiaHD**

![image](https://github.com/user-attachments/assets/04b8afeb-2086-4f22-8e62-d5021c80a6ae)

ON ChiTietHoaDon: Trigger này áp dụng cho bảng **ChiTietHoaDon**

AFTER INSERT, UPDATE, DELETE: Trigger sẽ kích hoạt sau khi thực hiện thêm/xóa/cập nhật trên bảng này.

![image](https://github.com/user-attachments/assets/8b43c177-1ba1-4cde-b4e1-f769b62586b7)

Mở đầu khối sử lý chính của trigger

![image](https://github.com/user-attachments/assets/7cb5f787-e473-4981-b739-f30861238c3e)

Cập nhật cột **TongGiaHD** của bảng **HoaDon**

Lấy tổng **ThanhTien** Từ bảng **ChiTietHoaDon** cho từng **MaHD** tương ứng.

![image](https://github.com/user-attachments/assets/827b812c-c377-4029-a2ff-d4a973f7799c)

FROM HoaDon hd: Áp dụng trên bảng **HoaDon** lấy bích danh là **hd**

 WHERE hd.MaHD IN (...): Chỉ cập nhật các hóa đơn có **MaHD** nằm trong các bản ghi được chèn vào **inserted** hoặc xóa bản ghi **deleted**

 (inserted),(Deleted) : Hai bảng tạm hệ thống tự tạo khi trigger khích hoạt.

 ![image](https://github.com/user-attachments/assets/b9331180-3d93-48d7-ba8a-c34b4fa1dd73)

 kết thúc khối trigger 

**Nhập dữ liệu có kiểm soát, nhằm để test sự hiệu quả của việc trigger auto run.**

 ![image](https://github.com/user-attachments/assets/cdaba389-bdb7-4966-a51d-efaaa9d48584)

INSERT INTO NhanVien (MaNV, TenNV, ChucVu)

VALUES : chèm thêm dữ liệu nhân viên vào bảng **NhanVien** muốn chèn bao nhiêu người tùy thích nhưng có chọn lọc.

![image](https://github.com/user-attachments/assets/150f47a0-e9e6-4f72-a113-0185675eed33)

INSERT INTO KhachHang (MaKH, TenKH, SoDienThoai, DiemTichLuy)

VALUES : Chèn thêm dữ liệu khách hàng mới vào bảng **KhachHang** Gồm mã KH và tên, số điện thoại, điểm tích lũy.

![image](https://github.com/user-attachments/assets/8014240a-d351-4cd2-b464-71be6bd711de)

INSERT INTO SanPham (MaSP, TenSP, DonGia, SoLuongTon)

VALUES : chèn thêm dữ liệu Sản Phẩm cho hệ thống bán hàng.

![image](https://github.com/user-attachments/assets/8703178f-224d-494b-8924-d9b0f41db256)

Chèn dữ liệu của hóa đơn mới. Với ban đầu **TongGiaHD** đặt là (O)

![image](https://github.com/user-attachments/assets/819750e1-07ec-4bcf-a555-c81ba54cda79)

Với mỗi dòng: chọn mã hóa đơn, mã sản phẩm, số lượng và đơn giá cụ thể.

Trigger sẽ tự động tính **ThanhTien=SoLuong*DonGia** và cập nhật lại giá trị của hóa đơn trước đó với **MaHD** tương ứng.

![image](https://github.com/user-attachments/assets/5e893f6a-ab6d-431e-89d3-8d1049a9ba13)

SELECT * FROM HoaDon; : lấp toàn bộ dữ liệu từ bảng **HoaDon**, Kiểm tra trigger có hoạt động đúng không.

Kiểm tra xem **TongGiaHD** đã hoạt động đúng hay sai.

### Kết quả cuối cùng

![image](https://github.com/user-attachments/assets/e3633968-7f44-4912-ab99-61543cbb57c5)

### Kết luận về Trigger đã giúp gì cho đồ án của em.

Trigger tự động: giúp đồ án trở lên dễ dàng lấy dữ liệu, tránh nhập thủ công, dễ kiểm tra và truy vấn.



