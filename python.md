# 初始
#### if语句
- 输入分数判断级别
```python
score = input ("你考了多少分：")  
if score.isdigit():  
    score = int(score)  
    if score <= 100 and score >= 0:  
        if score >= 90 :  
            print("优秀")  
        elif score >= 80:  
            print("很好")  
        elif score >= 70:  
            print("一般")  
        elif score >= 60:  
            print("及格")  
        else:  
            print("考的什么蛋")  
    else:  
        print("输入的什么蛋")  
else:  
    print("请输入数字")
```
#### 流程控制之 while语句
- 使用while循环计算1+2+3+...+100的结果
```python
sum = 0  
i = 0  
while i<= 100:  
    sum += i  
    i += 1  
print(f"最后的结果是{sum}")
```
- 循环中止语句
	- break 用于完全结束一个循环，跳出循环体执行后面的语句
	- continue 和 break 有点类似，区别在于continue只是终止本次循环，接着执行后面的循环，break则完全终止循环
- 使用while True制造无限循环来完成一个简单的猜数游戏
```python
import random  
num = random.randint(1, 100)  
while True:  
    guess = input("请输入一个数字(1-100):")  
    if guess.isdigit():  
        guess = int(guess)  
        if guess < 1 or guess > 100:  
            print("请输入范围内的数字")  
        else:  
            if guess < num:  
                print("往大点猜")  
            elif guess > num:  
                print("往小点猜")  
            else:  
                print("猜对啦")  
                break  
    else:  
        print("请输入数字")
```

# 基础数据类型
## 数字(int)
## 布尔值()bool
- 布尔值就两种：True，False。就是反应条件的正确与否
## 字符串 str
### 字符串的索引与切片
```python
a = 'ABCFDIKskdh'  
# [开始:结束]，默认取到结束之前，不写结束也直接取到结尾  
print(a[1:]) # BCFDIKskdh  
# [开始:结束:步长]，步长默认是1，如果是-1，就倒着走  
print(a[1::2]) # BFIsd  
print(a[-1::-1]) # hdksKIDFCBA
```
### 字符串常用方法
```python
## 内容居中，总长度，空白处填充  
while True:  
    color = input("请输入一种颜色:")  
    print(color.center(20, '='))
    
## 数字符串中的元素出现的次数
a = input("请发表你的高见:")  
if a.count("hello"):  
    print("hello")  
else:  
    print(a.count("a"))
```
# 文件操作

```python
# r模式打开文件的时候，文件必须存在，不存在就报错  
# r模式默认使用命令行字符集去读取文字，如果是UTF-8需要说明  
f = open('demo01.txt', 'r',encoding='utf-8')  
data = f.read()  
print(data)  
  
# rb读取的是二进制，一般用于读取二进制文件  
f = open('ScreenShot_2026-03-17_091609_055.png', "rb")  
image=f.read()  
print(image)  

# r+可读可写  
# seek是光标概念，r模式默认光标在开头  
f = open('demo01.txt', 'r+',encoding='utf-8')  
data = f.read()  
print(data)  
# read()到文件结尾，光标也移到结尾  
# write在光标所在处，写上新的内容  
f.write("world")  
# 所以需要将seek移动到开头  
f.seek(0)  
data2 = f.read()  
print(data2)

# w是覆盖，文件不存在，就创建，存在就直接覆盖  
f = open('demo01.txt', 'w',encoding='utf-8')  
f.write('hello world')  
  
# w+覆盖后可读可写  
f = open('demo01.txt', 'w+',encoding='utf-8')  
data = f.read()  
f.write('hello world???')

# 二进制方式复制图片文件  
f = open('ScreenShot_2026-03-17_091609_055.png', 'rb')  
old_img = f.read()  
f1 = open('screenshot.png', 'wb')  
f1.write(old_img)  
f1.close()

# a在文件后面追加内容，a+可追加可读
# 文件存在就打开，光标在最后，文件不存在就新建
f = open('demo01.txt','a',encoding='utf-8')  
f.write("hello")
```
