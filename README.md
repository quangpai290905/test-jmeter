Báo cáo Kiểm thử Hiệu năng với Apache JMeter
Họ và tên: Dương Việt Quanng
Mã sinh viên: BIT230352
Trang web kiểm thử: https://www.wikipedia.org

Công cụ sử dụng: Apache JMeter 5.6.3

1. Mục tiêu kiểm thử
Hiểu cách sử dụng JMeter để thực hiện kiểm thử hiệu năng cho một trang web thực tế.

Thiết kế và thực thi 3 kịch bản kiểm thử (Thread Group) với các tham số người dùng khác nhau.

Phân tích các chỉ số quan trọng như thời gian phản hồi (Response Time), thông lượng (Throughput) và tỉ lệ lỗi (Error Rate).

2. Thiết lập kịch bản kiểm thử
Kịch bản 1: Baseline Test (TG01_Basics)
Mô tả: Kiểm tra khả năng phản hồi cơ bản của trang chủ.

Số lượng người dùng (Threads): 10.

Số lần lặp (Loop Count): 5.

Hành vi: Gửi yêu cầu HTTP GET đến trang chủ /.

Kịch bản 2: Stress Test (TG02_HeavyLoad)
Mô tả: Giả lập tải nặng để kiểm tra độ ổn định của hệ thống.

Số lượng người dùng (Threads): 50.

Thời gian tăng tải (Ramp-up): 30 giây.

Hành vi: Truy cập trang chủ / và trang con /wiki/Wikipedia:About.

Kịch bản 3: Custom Scenario (TG03_Custom)
Mô tả: Kiểm tra hiệu năng chức năng tìm kiếm trong thời gian duy trì 1 phút.

Số lượng người dùng (Threads): 20.

Thời gian chạy (Duration): 60 giây.

Hành vi: Gửi yêu cầu tìm kiếm từ khóa "JMeter" qua Path /w/index.php.

3. Kết quả kiểm thử thực tế
Hình ảnh minh chứng


4. Phân tích và Kết luận
Xử lý lỗi 403 Forbidden: Trong lần chạy đầu tiên, hệ thống phản hồi lỗi 403 do thiếu thông tin trình duyệt. Vấn đề này đã được khắc phục bằng cách thêm HTTP Header Manager với thuộc tính User-Agent giả lập trình duyệt Chrome.

Thời gian phản hồi: Thời gian phản hồi trung bình (Average) tăng dần từ 134ms (10 users) lên 362ms (50 users). Điều này cho thấy hệ thống cần nhiều thời gian xử lý hơn khi số lượng người dùng đồng thời tăng lên.

Độ ổn định: Ở kịch bản tải nặng 50 users (TG02), tỉ lệ lỗi đạt 0.00%, chứng tỏ trang web Wikipedia chịu tải rất tốt dưới cấu hình thử nghiệm.

Chức năng tìm kiếm: Kịch bản tìm kiếm (TG03) có thời gian phản hồi cao nhất (1091ms) do đây là tác vụ yêu cầu truy vấn dữ liệu phức tạp hơn so với việc tải trang tĩnh.
