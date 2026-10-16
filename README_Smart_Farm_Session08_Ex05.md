**Họ và tên:** Phạm Thành Đạo\
**Lớp:** HCM-KS26-CNTT1\
**Môn học:** IT-101 -- Nhập môn Công nghệ thông tin\
**Session:** 08\
**Bài tập:** Exercise 05 -- Xây dựng bộ tài liệu kỹ thuật cho dự án
Smart Farm

# PHẦN 1. PHÂN TÍCH HỆ THỐNG

## 1.1. Mục tiêu hệ thống

Smart-Farm là hệ thống trang trại thông minh ứng dụng IoT (Internet of
Things -- Internet vạn vật) để thu thập dữ liệu môi trường, hỗ trợ người
vận hành theo dõi điều kiện trồng trọt và điều khiển tưới nước khi đáp
ứng các điều kiện đã thiết lập.

## 1.2. Input và Output

  -----------------------------------------------------------------------
  Loại                    Thành phần              Vai trò
  ----------------------- ----------------------- -----------------------
  Input                   Cảm biến nhiệt độ       Đo nhiệt độ môi trường
                                                  tại khu vực trồng trọt

  Input                   Cảm biến độ ẩm đất      Cung cấp dữ liệu về độ
                                                  ẩm của đất

  Input                   Ngưỡng do người vận     Xác định điều kiện cần
                          hành cấu hình           xem xét tưới

  Xử lý                   Bộ điều khiển/SoC       Đọc dữ liệu, kiểm tra
                                                  điều kiện và điều khiển
                                                  thiết bị

  Output                  Máy bơm hoặc van điện   Cấp nước khi điều kiện
                                                  tưới hợp lệ

  Output                  Màn hình hoặc bảng theo Hiển thị dữ liệu và
                          dõi                     trạng thái hệ thống

  Output                  Nhật ký hoạt động       Ghi nhận sự kiện, lỗi
                                                  và trạng thái tưới
  -----------------------------------------------------------------------

**SoC (System on a Chip)** là hệ thống tích hợp nhiều thành phần xử lý
trên một chip. Trong Smart-Farm, bộ điều khiển có thể dùng SoC để đọc
cảm biến và điều khiển thiết bị. Cấu hình thực tế tùy thuộc phần cứng
được lắp đặt.

## 1.3. Sơ đồ phối hợp phần cứng

![Sơ đồ hệ thống Smart-Farm: cảm biến nhiệt độ và độ ẩm đất gửi dữ liệu
đến bộ điều khiển SoC; bộ điều khiển điều khiển máy bơm hoặc van và gửi
trạng thái đến bảng theo
dõi.](https://placehold.co/1000x420/png?text=Sensors+%E2%86%92+SoC+Controller+%E2%86%92+Pump%2FValve+%E2%86%92+Farm)

*Sơ đồ minh họa luồng dữ liệu và điều khiển. Khi triển khai thực tế, cần
thay bằng sơ đồ đúng với phần cứng đã lắp đặt.*

------------------------------------------------------------------------

# PHẦN 2. README.MD HOÀN CHỈNH

# 🚀 Smart-Farm -- Hệ thống trang trại thông minh

## 🌱 1. Giới thiệu dự án

**Smart-Farm** là hệ thống hỗ trợ theo dõi môi trường trồng trọt và tưới
nước có kiểm soát tại **trang trại Lan**. Hệ thống thu thập dữ liệu cảm
biến, xử lý theo ngưỡng cấu hình và điều khiển máy bơm hoặc van khi các
điều kiện an toàn được đáp ứng.

Mục tiêu là giúp người vận hành theo dõi tình trạng cây trồng thuận tiện
hơn, sử dụng nước hợp lý và phát hiện sớm các trạng thái bất thường.

> **Lưu ý:** Đây là tài liệu mô tả mô hình tham khảo. Tên thiết bị, chân
> kết nối, ngưỡng nhiệt độ và độ ẩm phải được điều chỉnh theo cấu hình
> thực tế của trang trại.

## 🧩 2. Sơ đồ hệ thống

![Sơ đồ Smart-Farm: cảm biến nhiệt độ và độ ẩm đất kết nối bộ điều khiển
SoC; bộ điều khiển điều khiển máy bơm hoặc van và gửi dữ liệu đến giao
diện giám
sát.](https://placehold.co/1000x420/png?text=Temperature+Sensor+%2B+Soil+Moisture+Sensor+%E2%86%92+SoC+%E2%86%92+Pump%2FValve)

**Luồng hoạt động:** Cảm biến → Bộ điều khiển → Kiểm tra điều kiện → Máy
bơm/van → Cập nhật trạng thái.

## ⚙️ 3. Hướng dẫn cài đặt và khởi động

Các bước dưới đây là quy trình triển khai tổng quát. Hãy dùng đúng phần
mềm, cổng kết nối và lệnh khởi động do nhà cung cấp bộ điều khiển quy
định.

1.  Kiểm tra bộ điều khiển, cảm biến, nguồn điện và máy bơm/van.
2.  Kết nối cảm biến nhiệt độ và cảm biến độ ẩm đất với bộ điều khiển
    theo sơ đồ phần cứng.
3.  Cấu hình ngưỡng vận hành phù hợp với loại cây, điều kiện đất và
    hướng dẫn kỹ thuật tại trang trại.
4.  Bật nguồn bộ điều khiển và kiểm tra xem dữ liệu cảm biến có được cập
    nhật hay không.
5.  Thử chế độ điều khiển an toàn trước khi cho hệ thống vận hành tự
    động.

Ví dụ tạo thư mục lưu tài liệu và nhật ký trên máy tính có PowerShell:

``` powershell
mkdir Smart-Farm
cd Smart-Farm
mkdir docs
mkdir logs
```

Các lệnh trên chỉ tạo thư mục mẫu trên máy tính; chúng **không** cài đặt
firmware hoặc tự kết nối phần cứng.

## ✅ 4. Tính năng hệ thống

-   [x] Thu thập dữ liệu nhiệt độ môi trường.
-   [x] Thu thập dữ liệu độ ẩm đất khi có cảm biến tương ứng.
-   [x] Mô tả luồng xử lý dữ liệu theo mô hình IPO.
-   [x] Theo dõi điều kiện tưới dựa trên ngưỡng cấu hình.
-   [ ] Điều khiển máy bơm/van tự động sau khi kiểm tra an toàn và hiệu
    chuẩn.
-   [ ] Hiển thị cảnh báo khi cảm biến mất kết nối hoặc dữ liệu bất
    thường.
-   [ ] Lưu nhật ký vận hành với cơ chế giới hạn dung lượng.

*Các mục đánh dấu `[ ]` cần được triển khai và kiểm thử trên phần cứng
thực tế trước khi xác nhận hoàn thành.*

## 📊 5. Bảng thông số tham khảo

  -----------------------------------------------------------------------
  Thành phần              Dữ liệu/đặc tính        Mục đích
  ----------------------- ----------------------- -----------------------
  Cảm biến nhiệt độ       Nhiệt độ môi trường     Theo dõi điều kiện môi
                                                  trường

  Cảm biến độ ẩm đất      Độ ẩm đất               Hỗ trợ xác định nhu cầu
                                                  tưới

  Bộ điều khiển SoC       Đọc cảm biến và xử lý   Ra quyết định điều
                          logic                   khiển

  Máy bơm/van             Bật hoặc tắt theo lệnh  Cấp nước cho cây
                          điều khiển              

  Nhật ký                 Thời điểm, trạng thái,  Hỗ trợ kiểm tra và xử
                          lỗi                     lý sự cố
  -----------------------------------------------------------------------

*Thông số định lượng như dải đo, độ chính xác, điện áp và ngưỡng tưới
phải lấy từ tài liệu của thiết bị thực tế; không nên tự đặt thông số khi
chưa xác minh.*

## 🧠 6. Mô hình IPO trong Smart-Farm

IPO gồm ba phần:

-   **Input (Đầu vào):** Dữ liệu nhiệt độ, độ ẩm đất và ngưỡng vận hành.
-   **Process (Xử lý):** Bộ điều khiển kiểm tra tính hợp lệ của dữ liệu,
    so sánh với ngưỡng đã cấu hình và kiểm tra điều kiện an toàn.
-   **Output (Đầu ra):** Bật/tắt máy bơm hoặc van, hiển thị trạng thái
    và ghi nhật ký.

Ví dụ: cảm biến báo đất khô hơn ngưỡng đã cấu hình; bộ điều khiển kiểm
tra dữ liệu và trạng thái an toàn; nếu đủ điều kiện, hệ thống bật bơm
trong khoảng thời gian được thiết lập rồi kiểm tra lại.

## 🖥️ 7. Chu kỳ Fetch--Decode--Execute của CPU

Khi bộ xử lý thực thi chương trình điều khiển tưới, chu kỳ cơ bản có thể
mô tả như sau:

> **Fetch (Nạp lệnh):** CPU lấy lệnh tiếp theo từ bộ nhớ.
>
> **Decode (Giải mã):** CPU xác định lệnh yêu cầu thực hiện thao tác gì.
>
> **Execute (Thực thi):** CPU thực hiện thao tác, chẳng hạn tính toán
> điều kiện hoặc cập nhật tín hiệu điều khiển thông qua phần cứng phù
> hợp.
>
> Chu kỳ này lặp lại khi chương trình hoạt động. CPU không tự cấp điện
> trực tiếp cho máy bơm công suất lớn; cần mạch điều khiển phù hợp và
> các biện pháp bảo vệ điện.

## 🔺 8. Mô hình kim tự tháp DIKW

DIKW mô tả cách chuyển dữ liệu thành thông tin, kiến thức và quyết định:

``` text
                 /\
                /  \
               / W  \   WISDOM – HÀNH ĐỘNG
              /------\  Quyết định tưới khi đủ điều kiện
             /   K    \  KNOWLEDGE – KIẾN THỨC
            /----------\ Quy tắc: đất khô và điều kiện an toàn
           /     I      \ INFORMATION – THÔNG TIN
          /--------------\ Nhiệt độ/độ ẩm được đối chiếu ngưỡng
         /        D        \ DATA – DỮ LIỆU
        /__________________\ Số đo cảm biến thô
```

-   **D -- Data (Dữ liệu):** Cảm biến ghi nhận nhiệt độ và độ ẩm đất.
-   **I -- Information (Thông tin):** Dữ liệu được gắn ngữ cảnh và so
    sánh với ngưỡng cấu hình.
-   **K -- Knowledge (Kiến thức):** Quy tắc vận hành cho biết trong điều
    kiện nào cây cần được xem xét tưới.
-   **W -- Wisdom (Hành động/ra quyết định):** Hệ thống quyết định tưới
    hoặc không tưới sau khi kiểm tra điều kiện an toàn.

**Ví dụ:** Nhiệt độ cao chỉ là một dữ kiện. Hệ thống không nên tự động
kết luận phải tưới chỉ dựa vào nhiệt độ; cần xem xét thêm độ ẩm đất,
loại cây và quy tắc vận hành.

## ⚠️ 9. Lưu ý và xử lý sự cố

### Trường hợp RAM đầy do dữ liệu nhật ký

Nếu chương trình giữ quá nhiều nhật ký trong RAM, bộ nhớ khả dụng có thể
giảm, khiến hệ thống chậm, bỏ lỡ dữ liệu cảm biến hoặc khởi động lại.

Thực hiện theo các nguyên tắc an toàn:

1.  **Không xóa dữ liệu tùy tiện:** Không xóa toàn bộ thư mục hệ thống
    hoặc tệp chưa xác định.
2.  **Giới hạn nhật ký trong RAM:** Chỉ giữ một lượng bản ghi gần nhất;
    ghi nhật ký theo từng phần thay vì lưu toàn bộ lịch sử trong bộ nhớ.
3.  **Ghi ra nơi lưu trữ phù hợp:** Dùng bộ nhớ lưu trữ được hỗ trợ, có
    giới hạn dung lượng và chính sách xoay vòng nhật ký (log rotation).
4.  **Giữ an toàn cho việc tưới:** Khi bộ nhớ hoặc cảm biến gặp lỗi,
    chuyển sang trạng thái an toàn đã được thiết kế; không bật bơm vô
    hạn. Cho phép điều khiển thủ công khi phù hợp.
5.  **Kiểm tra trước khi khởi động lại:** Ghi nhận thông báo lỗi nếu có,
    xác minh trạng thái máy bơm/van và làm theo quy trình của nhà cung
    cấp.
6.  **Không tự ý ngắt nguồn phần cứng:** Đặc biệt khi máy bơm đang hoạt
    động hoặc hệ thống đang ghi dữ liệu, trừ khi cần thực hiện quy trình
    dừng khẩn cấp an toàn.

### Các sự cố thường gặp

  -----------------------------------------------------------------------
  Hiện tượng              Nguyên nhân có thể      Cách xử lý
  ----------------------- ----------------------- -----------------------
  Không có dữ liệu cảm    Dây kết nối, nguồn hoặc Kiểm tra nguồn và kết
  biến                    cảm biến lỗi            nối theo hướng dẫn
                                                  thiết bị

  Máy bơm không bật       Chưa đạt điều kiện tưới Kiểm tra dữ liệu,
                          hoặc mạch điều khiển    ngưỡng và trạng thái an
                          lỗi                     toàn

  Nhật ký tăng nhanh      Ghi lặp lỗi hoặc chưa   Giới hạn tốc độ ghi và
                          giới hạn dung lượng     cấu hình xoay vòng nhật
                                                  ký

  Bộ điều khiển thiếu RAM Giữ quá nhiều dữ liệu   Giảm bộ đệm, giải phóng
                          trong bộ nhớ            tài nguyên đúng cách và
                                                  kiểm tra chương trình
  -----------------------------------------------------------------------

## 🔒 10. An toàn vận hành

-   Đặt ngưỡng tưới phù hợp với loại cây và điều kiện thực tế.
-   Kiểm tra cảm biến định kỳ và xác minh dữ liệu bất thường trước khi
    thay đổi cấu hình.
-   Sử dụng mạch điều khiển, nguồn điện và thiết bị bảo vệ đúng thông số
    của máy bơm.
-   Bảo vệ bộ điều khiển khỏi nước, bụi và nhiệt độ vượt giới hạn cho
    phép.
-   Kiểm thử chế độ dừng an toàn và phương án điều khiển thủ công trước
    khi bàn giao.
-   Không coi tài liệu tham khảo này là thay thế cho hướng dẫn của nhà
    sản xuất hoặc quy trình an toàn điện tại trang trại.

## 📚 11. Thuật ngữ

  -----------------------------------------------------------------------
  Thuật ngữ                           Giải thích
  ----------------------------------- -----------------------------------
  IoT                                 Internet vạn vật -- các thiết bị có
                                      khả năng thu thập, trao đổi dữ liệu

  SoC                                 Hệ thống tích hợp nhiều thành phần
                                      trên một chip

  IPO                                 Đầu vào -- Xử lý -- Đầu ra

  DIKW                                Dữ liệu -- Thông tin -- Kiến thức
                                      -- Trí tuệ/ra quyết định

  CPU                                 Bộ xử lý trung tâm

  RAM                                 Bộ nhớ truy cập ngẫu nhiên, dùng
                                      cho dữ liệu/chương trình đang hoạt
                                      động

  Log                                 Nhật ký ghi lại sự kiện, trạng thái
                                      hoặc lỗi

  Log rotation                        Cơ chế luân phiên, giới hạn và lưu
                                      trữ các tệp nhật ký
  -----------------------------------------------------------------------

## 📝 12. Kết luận

README này mô tả cách Smart-Farm tiếp nhận dữ liệu cảm biến, xử lý theo
IPO, vận dụng SoC để thực thi chương trình và chuyển dữ liệu thành quyết
định theo DIKW. Trước khi sử dụng tại trang trại Lan, cần đối chiếu tài
liệu với phần cứng thực tế, kiểm thử các ngưỡng tưới và xác nhận cơ chế
xử lý lỗi.

------------------------------------------------------------------------

# PHẦN 3. KIỂM THỬ TÌNH HUỐNG RAM ĐẦY

**Tình huống:** Bộ điều khiển giữ quá nhiều dữ liệu nhật ký trong RAM.

**Nguy cơ:** Hết bộ nhớ, hệ thống chậm hoặc khởi động lại, mất dữ liệu
cảm biến và ảnh hưởng việc điều khiển tưới.

**Cập nhật trong README:** Đã bổ sung mục **"Lưu ý và xử lý sự cố --
Trường hợp RAM đầy do dữ liệu nhật ký"**, trong đó yêu cầu giới hạn bộ
đệm, ghi nhật ký theo từng phần, dùng lưu trữ phù hợp, không xóa tệp hệ
thống tùy tiện và đưa hệ thống về trạng thái an toàn khi có lỗi.

**Tiêu chí kiểm thử đạt:**

-   [ ] Nhật ký trong RAM được giới hạn, không tăng vô hạn.
-   [ ] Khi bộ nhớ gần đầy, hệ thống có cảnh báo hoặc cơ chế xử lý được
    thiết kế trước.
-   [ ] Lỗi bộ nhớ không khiến máy bơm chạy vô hạn.
-   [ ] Có thể kiểm tra trạng thái và khôi phục theo quy trình an toàn.

------------------------------------------------------------------------

# THÔNG TIN REPOSITORY

**Tên repository đề xuất:**

`HCM-KS26-CNTT1_IT-101_Session08_Ex05`

**Tên file chính:** `README.md`

**Cách kiểm tra:** Mở file trên StackEdit hoặc GitHub để xem tiêu đề,
bảng, danh sách, blockquote, sơ đồ và code block đã hiển thị đúng chưa.
Nếu ảnh sơ đồ không tải được, Alt Text vẫn mô tả nội dung ảnh; nên thay
URL ảnh minh họa bằng ảnh sơ đồ do nhóm lưu trữ ổn định trước khi bàn
giao chính thức.
