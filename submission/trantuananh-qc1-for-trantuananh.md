# Phiếu QC 1 — Road v1.0 (tự kiểm)

> Buổi này làm trên CVAT local cá nhân theo hướng dẫn của coach, không có bạn để đổi lô. Phiếu này là **tự kiểm** lô của chính mình, theo đúng mẫu `templates/qc1_form.md`, trên **bản export đầu tiên** (trước khi sửa).

Lô được kiểm (học viên): Trần Tuấn Anh        Người kiểm (học viên): Trần Tuấn Anh (tự kiểm)  
Ngày: 20/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `trantuananh-front.zip` (export 19:15) + `trantuananh-fisheye.zip` (export 19:14), revision 1, không kèm manifest theo coach  
Số ảnh kiểm: 6 (A04, A08, A09, A10, A12, B04) (+ 0 ảnh thêm)   Số nhãn đã kiểm (shape + tag): 138  

Cách đếm số nhãn đã kiểm (shape + 4 tag mỗi ảnh): A04 17 · A08 36 · A09 23 · A10 27 · A12 24 · B04 11 = **138**.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 tag (6 camera) | 2 | camera: 0 lỗi; 2 lỗi tag `weather` là **nhẹ** |
| QC1-02 đủ L1, R1 | bỏ sót | 12 (L1 + R1 × 6 ảnh) | 1 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 15 lane | 4 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 15 lane | 2 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 15 lane | 2 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 15 lane | 1 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 21 (11 drivable, 7 crosswalk, 3 road_curb) | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 33 đèn | 5 | 1 nặng, 4 chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 78 (33 đèn + 45 biển) | 11 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 45 biển | 2 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 7 shape (B04) | 0 | chính |
| QC1-12 file | lỗi file | 2 file | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-03 | A04 | lane R2 @(718,536) | nặng | Mẩu gần của vạch trắng đứt R1 bị gán `R2` (sai thuộc tính) |
| 2 | QC1-05 | A04 | lane R1 @(639,397) | chính | Cùng vạch đứt R1 bị tách làm hai polyline (sai phạm vi) |
| 3 | QC1-04 | A04 | lane R2 (vạch làn xe đạp) | chính | Bỏ sót vạch trắng liền R2 thật bên phải |
| 4 | QC1-06 | A04 | lane L1 @(48,552) | chính | Vạch tim vàng đôi liền gán `dashed / single`, đúng là `solid / double` |
| 5 | QC1-07 | A04 | drivable alternative @(729,536) | chính | Vùng alternative tràn qua R2 sang làn xe đạp |
| 6 | QC1-09 | A04 | traffic_sign @(765,248) | chính | Biển tên đường xanh lá để `other`, đúng là `information` |
| 7 | QC1-09 | A04 | traffic_sign @(233,152) | chính | Thấy mặt sau tấm biển nhưng gán `facing = front` |
| 8 | QC1-01 | A04 | tag weather | nhẹ | Trời xám đặc, gán `clear`, đúng là `overcast` |
| 9 | QC1-03 | A08 | lane R1 @(1271,481) | nặng | Vạch liền mép phải gán `R1`, đúng là `R2` |
| 10 | QC1-02 | A08 | lane R1 (vạch đứt giữa) | nặng | Bỏ sót R1 thật: vạch trắng đứt từ (752,438) lên (645,312) |
| 11 | QC1-07 | A08 | drivable direct @(1.5,322) | chính | Một polygon direct phủ cả mặt đường, không tách làn bên phải thành alternative |
| 12 | QC1-09 | A08 | traffic_sign @(777,37) | chính | Tấm "PASSENGER CARS ONLY" để `other`, đúng là `supplementary` |
| 13 | QC1-09 | A08 | traffic_sign @(991,205) | chính | Biển tiêu sọc chéo để `other`, đúng là `warning` |
| 14 | QC1-10 | A08 | traffic_sign @(991,183) | chính | Box gộp hai tấm biển tiêu chồng nhau (box không sát) |
| 15 | QC1-01 | A08 | tag weather | nhẹ | Trời xám đặc, gán `clear`, đúng là `overcast` |
| 16 | QC1-05 | A09 | lane L1 @(536,645) | chính | Vạch L1 bị tách thành hai polyline tại (595,551) |
| 17 | QC1-03 | A09 | lane L2 @(595,551) | nặng | Đoạn xa của L1 mang `position = L2` |
| 18 | QC1-04 | A10 | lane L1 @(539,384) | chính | Polyline vẽ từ xa về gần (điểm đầu ở trên) |
| 19 | QC1-08 | A10 | traffic_light @(669,178) | chính | Thừa: đèn ưu tiên trên nóc xe cứu thương, không phải đèn giao thông |
| 20 | QC1-08 | A10 | traffic_light @(662,178) | chính | Thừa: box trùng, cũng là đèn nóc xe cứu thương |
| 21 | QC1-08 | A10 | traffic_light @(561,194) | chính | Thừa: đèn trên nóc xe |
| 22 | QC1-10 | A10 | traffic_sign @(45,50) | chính | Box gộp cả biển chính lẫn biển phụ (đã có hai box riêng) |
| 23 | QC1-09 | A10 | traffic_sign @(536,235) | chính | Biển tên đường để `other`, đúng là `information` |
| 24 | QC1-09 | A10 | traffic_sign @(422,192) | chính | Biển tên đường gán `supplementary`, đúng là `information` |
| 25 | QC1-09 | A10 | traffic_sign @(439,199) | chính | Biển ONE WAY để `other`, đúng là `mandatory` |
| 26 | QC1-09 | A10 | traffic_sign @(764,187) | chính | Biển tên đường để `other`, đúng là `information` |
| 27 | QC1-09 | A10 | traffic_sign @(439,169) | chính | Biển tuyến xe đạp để `other`, đúng là `information` |
| 28 | QC1-09 | A10 | traffic_sign @(439,150) | chính | Biển tuyến xe đạp để `other`, đúng là `information` |
| 29 | QC1-03 | A12 | lane L1 @(485,624) | nặng | Thừa: polyline 2 điểm ở mép capô, không phải vạch |
| 30 | QC1-08 | A12 | traffic_light @(725,47) | chính | Box gộp hai cụm đèn (đã có hai box riêng) |
| 31 | QC1-08 | A12 | traffic_light @(967,287) | nặng | Đèn đi bộ đang sáng, hướng về xe, gán `vehicle / unknown / back`; đúng là `pedestrian / green / front` (sai màu đèn hướng về xe → chọn mức cao hơn) |
| 32 | QC1-09 | A12 | traffic_sign @(0,273) | chính | Biển ONE WAY để `other`, đúng là `mandatory` |

Ảnh **không lỗi**: **B04** (fisheye_rear). Đã kiểm: tag camera `fisheye_rear`; L1 vẽ đúng phần vệt đứt còn thấy; hai `road_curb` theo vỉa không sơn; crosswalk bám theo cung; drivable dừng ở mép thân xe, không gán làn BUS; biển cấm vào có tâm cách tâm ảnh ≈ 525 px > 512 px nên `edge_zone = true`; đèn đi bộ ≈ 497 px < 512 px nên `edge_zone = false`.

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A08 | Bên trái làn mình là giao lộ rộng, không có vạch sát làn. Có phải vẽ L1 không? | Coach đã xác nhận: không thấy vạch, miễn QC1-02 |
| A09 | Bên phải là bó vỉa không sơn (đã gán `road_curb`). Có phải vẽ R1 không? | Coach đã xác nhận: miễn QC1-02 |
| A12 | Bên phải là làn xe đỗ, không có vạch. Có phải vẽ R1 không? | Coach đã xác nhận: miễn QC1-02 |
| A09 | Ba biển nhỏ ở (1038,308), (831,317), (810,339) không đọc được chữ: giữ `other` hay xóa? | Giữ `other` (cao ≥ 8 px), ghi vào bảng ca khó của báo cáo |
| B04 | Làn BUS bên trái có tính `alternative` không? | Chọn không gán, vì xe mình không được đi; ghi ở bảng ca khó |

## Quyết định
Lỗi nặng: 6   Lỗi chính: 24 / 138 nhãn = 17,4 %   Lỗi nhẹ: 2   Ca chờ lead: 0 (các ca trên đã có lời đáp)  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): còn 6 lỗi nặng (QC1-02, QC1-03, QC1-08 sai màu đèn hướng về xe). Chỉ cần một lỗi nặng là đã phải Rework. Ngoài ra tỉ lệ lỗi chính 17,4 % > 5 % số nhãn đã kiểm.

## Sau Rework (kiểm lại bản export 20:42)
Cả 32 lỗi trên đã được sửa trong `trantuananh-front.zip` export 20:42, cùng các lỗi tương tự ở ảnh ngoài mẫu (A03, A05, A06, A07, A11). Chạy `road_check lint` trên hai file: 20 ảnh, chỉ còn QC1-02 ở A05, A07, A08, A09, A12, đều là ảnh không có vạch và đã được coach xác nhận miễn.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: thang mức lỗi Road v1.0.
