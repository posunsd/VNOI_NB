# Giải VNOI

### Bài 1

Tiền điện
Hàng tháng, công ty điện lực phải lập hóa đơn để tính tiền điện cho các hộ gia đình sử dụng
điện theo quy định như sau:

- 100 kWh đầu tiên, mỗi kWh phải trả 650 đồng;
- Từ kWh thứ 101 đến 150, mỗi kWh phải trả 1250 đồng;
- Từ kWh thứ 151 đến 200, mỗi kWh phải trả 1580 đồng;
- Từ kWh thứ 201 trở lên, mỗi kWh phải trả 1790 đồng.

Tiền điện trong hóa đơn mỗi hộ gia đình phải trả bằng số tiền điện mà hộ đó đã sử dụng
theo đơn giá cộng thêm 10% của số tiền đó (thuế giá trị gia tăng – VAT).
Yêu cầu: Bạn hãy giúp công ty điện lực thành phố tính tiền điện cho mỗi hộ gia đình.
Dữ liệu vào: Ghi số nguyên 𝐾 (1 ≤ 𝑘 ≤ 1000) là số kWh của một hộ đã sử dụng.
Dữ liệu ra: Ghi số tiền mà hộ đó phải trả trong hóa đơn, kết quả ghi theo định dạng số thực
có hai chữ số thập.

```
def calculate_electricity_bill(k):
    rates = [(100, 650), (50, 1250), (50, 1580),\
     (float('inf'), 1790)]
    total_bill = 0
    remaining_k = k

    for limit, rate in rates:
        if remaining_k > 0:
            usage = min(remaining_k, limit)
            total_bill += usage * rate
            remaining_k -= usage

    total_bill *= 1.1
    return round(total_bill, 2)

## test result
k = int(input())
print(calculate_electricity_bill(k))
```

### Bài 2

Trong toán học thì việc tìm chữ số tận cùng là một chuyên đề hay và khó. Hôm
nay thầy giáo tin học cho các bạn lập trình giải bài toán sau:
Cho số nguyên không âm n (n ≤ 1018). Hãy tìm chữ số tận cùng của $2^n$

Dữ liệu vào: Ghi số nguyên không âm n.
Dữ liệu ra: Ghi duy nhất chữ số tận cùng của $2^n$

```
def last_digit_of_power_of_two(n):
    last_digits = [6, 2, 4, 8]
    return last_digits[n % 4]

## test
n = int(input())
print(last_digit_of_power_of_two(n))
```

### Bài 3 Khai căn

Trong toán học, khi học về căn bậc hai ta có: $\sqrt(16)$ = 4 ; $\sqrt{50} = 5\sqrt{2}$
Tổng quát:$\sqrt{n} = x \sqrt{y}$ (Với $x^2.y=n$ và x lớn nhất có thể).
Yêu cầu: Viết chương trình tìm x và y khi biết giá trị của n.
Dữ liệu vào: Một số nguyên dương duy nhất n (𝑛 ≤ 109).
Dữ liệu ra: Ghi kết quả dựa trên 1 trong 3 trường hợp:

- Giá trị của x và y nếu 𝑥 ≠ 1 và 𝑦 ≠ 1 (giữa hai số cách nhau một khoảng trắng).
- Giá trị của x nếu y=1 hoặc giá trị của y nếu x=1.
- Ghi số 1 nếu x=1 và y=1.

```
def khai_can(n):
    x = 1
    import math
    for i in range(1, int(math.sqrt(n))+ 1):
        if n % (i*i) == 0:
            x = i

    y = n//(x*x)

    if x == 1 and y == a:
        return 1
    elif x == 1:
        return str(y)
    elif y == 1:
        return str(x)

    else:
        return f"{x} {y}"

n = int(input())
print(khai_can(n))
```

### Bài 4

Hình vuông nhỏ nhất
Cho hai hình chữ nhật có kích thước bằng nhau, mỗi hình chữ nhật có độ dài hai cạnh
lần lượt là 𝑎 và 𝑏.
Yêu cầu: Hãy tìm hình vuông có diện tích nhỏ nhất để chứa được hai hình chữ nhật
đã cho. Biết rằng cả hai hình chữ nhật chỉ có thể xoay, di chuyển, tiếp xúc nhau nhưng
không được cắt nhau.
Dữ liệu vào: Nhập từ bàn phím hai số nguyên dương 𝑎, 𝑏 (𝑎, 𝑏 ≤100)
Dữ liệu ra: Ghi ra màn hình diện tích của hình vuông thỏa mãn yêu cầu bài toán.

```
def min_square_area(a, b):
    c_1 = max(2 * a, b)
    c_2 = max(a, 2 * b)
    c_3 = max(a + b, max(a, b))

    min_c = min(c_1, c_2, c_3)

    return min_c ** 2

a, b = map(int, input("nhập a và b: ").split())
print(min_square_area(a,b))
```

### Bài 5

Vườn hoa hồng rất đẹp của ông Ba có 𝑛 khóm hoa, khóm hoa thứ 𝑖 có 𝑖 bông
hoa (1 ≤ 𝑖 ≤ 𝑛). Vào dịp lễ 20/11, có một lái buôn muốn mua rất nhiều hoa nhưng
yêu cầu ông Ba phải chọn ra những khóm hoa may mắn. Khóm hoa may mắn là
khóm hoa có số lượng bông hoa không có ước chung khác 1 với số 𝑛. Ông Ba muốn
đếm số lượng khóm hoa may mắn để bán cho lái buôn nhưng số lượng khóm hoa rất
lớn nên ông muốn nhờ bạn lập trình tin học tính cho nhanh.
Yêu cầu: Đếm số lượng khóm hoa may mắn có trong vườn ông Ba.
Dữ liệu vào: Một dòng duy nhất chứa số nguyên dương 𝑛 (2 ≤ 𝑛 ≤ 1016)
Dữ liệu ra: Ghi một số nguyên dương là số lượng khóm hoa may mắn.

```
def dem_hoa_may_man(n):
    result = n
    p = 2
    while p ** 2 <= n:
        if n % p == 0:
            while n % p == 0:
                n //= p
            result -= result // p
        p += 1
    if n > 1:
        result -= result // n
    return result

n = int(input().strip())
print(dem_hoa_may_man(n))
```

### Cú pháp cơ bản (Python)

```
# Các kiểu dữ liệu
type(3) # int nguyên
type(True) # boolean (True/False hay 1/0)
type('ngay 10-1') # string (kí tự)
type(1.1) # số thực

# nhập biến
k = input()
n = input("nhap vao day: ")

# cấu trúc danh sách
k = ['Mèo', 'Ngu', True, 1, 1.1]

# Ope
## Cộng
print(1+1) # 2
print(2-2) # 0
print(2*3) # 6
print(2%3) # 3
print(2 == 2) # True
print(2 != 2) # False
print(2**3) #8
...

# Hàm
def ten_ham(bien: int):

    # Xử lý nghiệp vụ
    bien = bien + 1
    return bien

# Câu điều kiện:
m = 0
if (m == 0):
    print('m bằng 0')
else:
    print('m khác 0')

# Vòng lặp
fruits = ["a", "b", "c", 1]
for x in fruits:
  print(x)

```
