# CombinationLock

![image](https://user-images.githubusercontent.com/87920408/196593385-fbc5480b-afc3-462a-8411-fae36378e4e2.png)

Sau khi tải file về và chạy thử bằng IDA Pro thì mình thấy các hàm cũng không cần thiết lắm

![image](https://user-images.githubusercontent.com/87920408/196596443-44b9c424-70b9-4aea-88a9-d4bcb2bd8091.png)

Nên mình quyết định chạy file trực tiếp luôn, sử dụng `./CombinationLock.exe` để khởi chạy file .exe này

![image](https://user-images.githubusercontent.com/87920408/196596779-d0c3b691-e912-47a9-a898-06f90c4b0d0f.png)

Nôm na là sẽ tìm giá trị cho các số Number1, Number2, ... , Number8 sao cho r1 = 88 và r2 = 8800 (ở đây quy luật của r1 và r2 không được show ra)
Với giao diện này, ta thấy các số N1, ..., N8 bị giới hạn bởi 8

Thì sau một vài lần thử cũng như vận dụng một xíu toán học mình đã nhận ra:
```python
r1 = N1*N2 + N3*N4 + N5*N6 + N7*N8
r2 = (N1+N2)*(N3+N4)*(N5+N6)*(N7+N8)
```
Tới đây hoàn toàn có thể nhẩm miệng ra kết quả hoặc mình viết script bruteforce các số N1 --> N8
```c
#include <stdio.h>
int main()
{
    int a, b, c, d, e, f, g, h, r1, r2;
    for (a = 1; a < 9; a++)
    {
        for (b = 1; b < 9; b++)
        {
            for (c = 1; c < 9; c++)
            {
                for (d = 1; d < 9; d++)
                {
                    for (e = 1; e < 9; e++)
                    {
                        for (f = 1; f < 9; f++)
                        {
                            for (g = 1; g < 9; g++)
                            {
                                for (h = 1; h < 9; h++)
                                {
                                    r1 = a * b + c * d + e * f + g * h;
                                    r2 = (a + b) * (c + d) * (e + f) * (g + h);
                                    if (r1 == 88 && r2 == 8800)
                                        printf("%d %d %d %d %d %d %d %d\n", a, b, c, d, e, f, g, h);
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```
![image](https://user-images.githubusercontent.com/87920408/196597509-5dae5a44-d116-4f92-9618-d39498f03af7.png)

Ở đây mình dùng luôn kết quả thu được `3 5 7 3 6 4 4 7`

![image](https://user-images.githubusercontent.com/87920408/196597679-53cae090-922f-4254-ab93-af83371ebf64.png)

Done --> `ASCIS{ca3512f4dfa95a03169c5a670a4c91a19b3077b4}`
