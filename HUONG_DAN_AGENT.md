# BỘ UI RỜI — BÀI 10, TIẾT 1
## Thông tin bắt buộc
- UBND phường Bình Hưng Hoà
- Trường Tiểu học Huỳnh Thúc Kháng
- Bài 10: Hoạt động sản xuất thủ công và công nghiệp (Tiết 1)
- Môn Tự nhiên và Xã hội 3
- Giáo viên: Hoàng Thị Tâm — Lớp 3/6

## Phạm vi
Đây là bộ hình ảnh rời để dựng bài, không phải bài giảng hoàn chỉnh.
Thư mục ui chứa hình trang trí/nút/khung không chữ.
Thư mục sgk chứa bốn ảnh cắt trực tiếp từ ảnh SGK người dùng cung cấp và ảnh nguồn nguyên vẹn.
Loi_thu_am.md chứa 46 đoạn lời đọc cùng mã ghép âm thanh.
Mở Danh_muc.html để xem các hình trong gói sau khi giải nén.

## Quy tắc sử dụng hình
1. Ảnh nghề dùng đúng sgk/hinh_2_lam_gom.png, hinh_3_may_tre_dan.png, hinh_4_det_tho_cam.png, hinh_5_tranh_dong_ho.png.
2. Không thay các ảnh nghề bằng ảnh AI, ảnh mạng hoặc ảnh trong mockup trước đó.
3. Các crop chỉ cắt vùng ảnh, không tái tạo, tăng nét AI hoặc sửa nội dung. Ảnh nguồn 551 × 407 px nên độ nét khi phóng lớn có giới hạn. Luôn giữ ảnh gốc để đối chiếu.
4. Nhãn “Hình 2”, “Hình 3”… là chữ thật do agent đặt ngoài ảnh.
5. Chưa có ảnh nguồn hình 6–9 trong bộ này. Không tự gắn số SGK lên ảnh khác. Dành vị trí chờ ảnh bổ sung và ghi rõ trong bản kiểm tra dành cho giáo viên.
6. Huy hiệu bình gốm chỉ là phần thưởng trang trí, không dùng làm ảnh quan sát nghề.
7. Không dùng screenshot/mẫu UI cũ làm nền có sẵn chữ rồi đặt vùng bấm giả.

## Danh mục UI
| Tệp | Cách dùng |
|---|---|
| 01_background_16x9.png | Nền trang, vùng giữa sáng để đặt nội dung |
| 02_panel.png | Viền khung nội dung; đặt trên lớp nền trắng |
| 03_item_card.png | Khung thẻ ảnh và dải nhãn trống; ảnh SGK đặt ở giữa, chữ thật phía dưới |
| 04_button_yellow.png | Nền nút hành động chính |
| 05_button_blue.png | Nền nút phụ, ví dụ Nghe lại |
| 06_icon_back.png | Biểu tượng quay lại |
| 07_icon_next.png | Biểu tượng tiếp tục |
| 08_icon_audio.png | Biểu tượng nghe |
| 09_icon_home.png | Biểu tượng về trang bìa |
| 10_star.png | Sao thưởng; sao chưa đạt dùng CSS grayscale, giảm sáng |
| 11_check.png | Dấu đã khám phá/đã hoàn thành |
| 12_badge.png | Huy hiệu cuối trò chơi |

Tất cả UI không chữ. PNG rời có alpha; các vùng trong suốt khi xem trên nền đen có thể trông như màu đen. Đặt nền trắng dưới panel và vùng ảnh dưới card. Không kéo giãn bất đối xứng icon/huy hiệu. Dùng object-fit: contain, giữ tỉ lệ tự nhiên. Nút bấm nhún xuống bằng transform khi nhấn, không cần ảnh riêng cho từng trạng thái.

## Thiết kế & 16:9
- Canvas logic 1600 × 900; scale = min(chiều rộng vùng nhìn / 1600, chiều cao vùng nhìn / 900).
- Căn giữa cả canvas; phần dư ngoài canvas nền xanh tối. Tuyệt đối không kéo hai chiều độc lập.
- Header khoảng 80 px; footer khoảng 80 px; nội dung chính khoảng 740 px.
- Lề an toàn 32 px, khoảng cách thẻ khoảng 24 px.
- Font Times New Roman toàn bộ. Tiêu đề 44–52 px; nội dung 30–34 px; nhãn nút 28–32 px trên canvas chuẩn.
- Xanh chính #0752E8, xanh tối #082461, vàng #FFD51C, xanh hoàn thành #17A84B, màu chữ #101B46.
- Tắt chuyển động lớn khi prefers-reduced-motion; chỉ dùng hiệu ứng nhấn nhẹ 100–180 ms.
- Vùng bấm rõ ràng; không chỉ đổi màu khi đúng/sai, phải có chữ và biểu tượng.
- Trên điện thoại dọc hiển thị gợi ý xoay ngang; không cắt mất bài.
- Thanh tiến độ là thành phần HTML/CSS động, không ảnh tĩnh. Khởi đầu rỗng 0%, tăng theo dữ liệu thực. Không gắn phần trăm giả.

## Bố cục & luật tương tác
1. Bìa: đầy đủ đơn vị, tên bài, giáo viên, lớp. Nút Bắt đầu. Không dùng tiến độ giả.
2. Video mở đầu: xuất hiện sau bìa, trước giao nhiệm vụ. Chỉ đây có giáo viên AI; các màn sau chỉ phát giọng thu.
3. Giao nhiệm vụ: ba bước Quan sát — Khám phá — Thử tài.
4. Khám phá: bốn thẻ 2 × 2, chọn thứ tự tùy ý. Click mở chi tiết: ảnh 60%, từ khóa 40%. Nút Nghe lại và Đã hiểu. Chỉ Đã hiểu mới tăng tiến độ; mỗi nghề tính một lần. Đủ 4/4 mới mở kiểm tra.
5. Kiểm tra: bốn câu, hiện từng câu và ba đáp án. Không chọn sẵn. Chọn rồi nhấn Trả lời. Sai được thử lại, đúng mới mở Tiếp theo. Đáp án A, B, C, A theo kịch bản thu âm.
6. Ích lợi: ba lượt Khám phá ích lợi — Ghi nhớ — Tìm hiểu thêm. Không dồn cả ba lên một màn. Phần thiếu ảnh 6–9 phải báo giáo viên khi bàn giao, không tự thay ảnh kiến thức.
7. Trò chơi: năm thử thách, mỗi thử thách được một sao duy nhất; sai không trừ sao, được thử lại. Ghép cặp có thao tác chạm chọn sản phẩm rồi chọn nghề; kéo thả là lựa chọn bổ sung. Thử thách 4 chọn đúng hai đáp án.
8. Góc hỏi đáp: nếu có AI thật mới dùng ô nhập. Nếu chưa có tích hợp, dùng hỏi đáp soạn sẵn, đổi tiêu đề “Góc hỏi đáp”, không trình bày như AI trực tiếp. Câu trả lời ngắn, phù hợp lớp 3.
9. Kết thúc: dùng huy hiệu; có Khám phá lại và Kết thúc. Huy hiệu cũng có thể hiện sau trò chơi nhưng không đánh dấu xong toàn bài trước lời kết.
10. Quay lại giữ trạng thái; chơi lại chỉ reset sau khi người học chọn thao tác đó.

## Âm thanh
Dùng mã và vị trí trong Loi_thu_am.md. Mỗi lần chỉ phát một đoạn. Đổi thẻ hoặc đổi màn phải dừng âm cũ. Phản hồi chỉ phát sau thao tác kiểm tra, không lộ đáp án trước. Chờ tệp thu âm thật, không tự tạo giọng khác thay giáo viên. Video mở đầu dùng mã 01. Âm thanh trình duyệt bắt đầu sau thao tác của người dùng.

## Nghiệm thu
- Đúng tên trường, phường, giáo viên, lớp và tên bài.
- Toàn bộ ảnh nghề khớp pixel với crop SGK, không thay nguồn.
- Không méo 16:9, không tràn chữ tại các kích thước 1920×1080, 1366×768, 1024×768 và điện thoại ngang.
- Font Times New Roman được áp dụng thật; nếu thiết bị không có font, báo phương án font được phép sử dụng, không âm thầm thay kiểu.
- Đủ 4 nghề mới mở kiểm tra; không cộng lặp tiến độ.
- Các câu hỏi đúng/sai hoạt động; ghép cặp dùng được bằng chạm.
- Âm không chồng; Nghe lại và tắt âm hoạt động.
- Tab/Enter sử dụng được cho nút; có nhãn dễ hiểu.
- Chưa có ảnh 6–9 và âm thanh thực phải được ghi rõ trong báo cáo bàn giao.

