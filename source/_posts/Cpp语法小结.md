---
title: Cpp语法小结
date: 2022-10-11 00:15:27
author: Hanlin Xu
toc: true
tags: 
  Cpp
---

# Cpp

# 1 输入和输出

* 最简单的Cpp程序

```C++
//很多头文件
#include <cstdio> #scanf,printf
#include <iostream>
using namespace std; //先记住，不加上报错

int main() //函数的执行入口，一定要叫main,参见python中的if __name__ = "__main__":
{
    cout<< "Hello World" <<endl;
    return 0; //一定需要返回0，如果返回不是0，那就错了
}
```

## 变量定义

* 数据类型

```c++
int main(){
    bool false/true  1byte(有八位，2^8)
    char 'c','a' 
    int //有一定的范围
    long long int //int的扩展，范围更大的int
    float //单精度浮点型，6-7位有效数字
    double //双精度浮点型，15-16位有效数字
}
```

## 输入输出

* cin/cout

```c++
int main(){
    int a,b; //定义两个变量
    //这里是cin和cout的输入输出，不需要判断数据类型是什么
    //cin 会忽略空格，但是scanf""里面所有的东西都是需要读的
    cin >> a >> b; //输入
    cout << a+b << endl; // 输出，endl表示回车
    return 0;
}
```

* printf/scanf

```c++
scanf("??"这个中间所有的都是需要输入的东西（也就是需要被读），包括逗号，空格",)
```

```c++
int main(){
    //scanf 和 printf,整数还是比较简单的，这里浮点数的用法需要注意
    float a, b = 0;
    scanf("%f%f",&a,&b);
    printf("a + b = %.1f\na * b = %.2f \n",a + b,a * b);
    //%.1f,%.2f,%.3f表示输出浮点数为几位小数
    
    //一般会采用printf和scanf，效率比较高
    return 0;
}
```

* 浮点数的输入输出

```c++
int main(){
    char a , b;
    scanf("%c%c",&a,&b);
    //注意scanf的输入语法scanf("%?",&a)：读取了一个特定类型的数据，然后赋给了变量a
    //知识点2：%c是会读入空格的
    //例如：scanf("%c %c",&a,&b)
    printf("%c\n%c",a,b);
    //double -> %lf
    //long long ->%lld
    //int,pool -> %d
    return 0;
}
```

## 表达式

* 四则运算

```c++
int main(){
    cout << 5 / 2 << endl;
    cout << 5 / 2.0 << endl;
    //取模运算,前面一个数除以后面一个数的余数
    //%取模只能是整数
    cout << 5 % 2 << endl;
    cout << -5 % 2 << endl;
    return 0;
}
```

* 重要：整数的自增自减，会在写循环结构里面常用

```c++
int main(){
    int a = 6;
    int c = a ++;
    //先把a赋值给c，然后再对a进行a++
    cout << a << " " << c << endl;
    
    int b = 6;
    int d = ++ c;
    //先++c,再把++c之后的值赋给d
    cout << b << " " << d << endl;
    
    return 0;
}
```

* 数据类型转换

```c++
int main(){
    //数据类型之间的相互转换，这里是显式的数据转换
    //但是实际上还有隐形的数据类型转换，默认把精度比较高得转为精度比较低的
    //int -> float 直接过去，float -> int 向下取整
    //int <-> char ASCII表
    
    float a = 5.23;
    int b = (int)a;
    
    cout << a << " " << b << endl;
    return 0;
}
```

1. 输出菱形

```C++
int main()
{
    char c;
    cin >> c;

    cout << "  " << c << endl;
    cout << " " << c << c << c << endl;
    cout << c << c << c << c << c << endl;
    cout << " " << c << c << c << endl;
    cout << "  " << c << endl;

    return 0;
}
```

# 2 条件语句

## `printf()`的用法

用法上节，这里讲几个特殊用法

```C++
int main(){
    //printf语句的用法，保留有效位数
    double f = 1.43478364872;
    printf("%.5lf\n",f);
       
    //格式化输出，固定他们的宽度
    int a = 1;
    int b = 23;
    int c = 456;
    
    //在前面补空格
    printf("%5d!\n",a);
    printf("%5d!\n",b);
    printf("%5d!\n",c);
    
    //在后面补空格
    printf("%-5d!\n",a);
    printf("%-5d!\n",b);
    printf("%-5d!\n",c);
    
    //在前面补0
    printf("%05d!\n",a);
    printf("%05d!\n",b);
    printf("%05d!\n",c);
    
    //浮点数也是一样的,小数点前面是宽度，小数点后面是保留的位数
    printf("%5.1d!\n",f);
    return 0;
    
}
```

## `if`判断

* 基本的`if`语句用法

```c++
//最完整的if语句
int main(){
    int score;
    cin >> score;  
    /*
    C语言中几种比较
    a>b
    a<b
    a>=b
    a<=b
    a==b
    a!=b
    */    
    if (score >= 60)//if后面绝对不能有分号
    {
        cout << "及格" <<  endl;
    }
    //变形1：else可以省略，if可以单独使用
    //变性2：如果if/else里面只有一句话，{}可以省略
    //C语言不是按照行来划分语句的，是按照分号，所以分号需要加上
    else{
        cout << "不及格" << endl;
    }
    return 0;
}
```

* `if-else`连写

```C++
int main(){
    int grade;
    cin >> grade;
    //C语言中，''表示引用的是单个字母，""表示字符串
    //这是一般写法
    /*
    if (grade >= 90) cout << 'A' << endl;
    else{
        if (grade >= 85) cout << 'B' << endl;
        else{
            if (grade >= 70)cout << 'C' << endl;
            else cout << "不及格" << endl;       
        }
    }
    return 0;
    */    
    //事实上对于，什么什么，否则什么什么，什么什么否则什么什么，有if-else连写，虽然只是写的方式，不影响编译
    //参考python中的elif
    if (grade >= 90) cout << 'A' << endl;
    else if (grade >= 85) cout << 'B' << endl;
    else if (grade >= 70)cout << 'C' << endl;
    else cout << "不及格" << endl;
    return 0;   
}
```

## 条件表达式

```C++
//条件表达式，在一句话里面表达复杂的逻辑
/*
与 && / and
遵循短路原则，如果第一个条件是false，那后面的就不会执行了
或 || / or
非 ！ / not，指的是不满足什么什么条件
if (a>b && c>d)
if (a>b || c>d)
if (!(a>b))
这三种也可以组合起来，而且有一定的优先级，其中&&优先级高于||
*/

//判断闰年
int main(){
    int year;
    cin >> year;
    if (year % 100 == 0 && year % 400 == 0 || year % 100 != 0 && year % 4 == 0)
        cout << "yes" << endl;
    else cout << "no" << endl;
    return 0;
}
```

# 3 条件判断和循环

## `while`

```c++
/*
while可以理解为循环版的if判断，如果条件成立，就一直执行
if 走完了，就出去了，但是while还是回到条件判断处
如果while条件判断失败了，就执行后面的
*/
int main(){
    int sum = 0;
    int i = 0;
    
    while( i <= 100){
        sum += i*i*i;
        i += 1;
    }
    cout << sum << endl;
    return 0;
}
```

## `for`

与whlie的区别：基本思想为把控制循环次数的变量从循环体中剥离。

* 基本结构

```c++
/*
for(init语句;条件;表达)
{
    statement
}
与while的区别：初始化语句和表达式语句
初始化 -> 条件语句 -> statement -> 表达式 -> 条件语句 -> statement
初始化只执行一次，可以为空
条件（与while不同，可以为空，为空表示为真）
表达式，每次之后都会执行，表示更新，可以为空

初始化和表达式可以是多个变量，其中用，隔开
*/

int main()
{
    for (int i = 0; i <= 10; i++){
        cout << i << endl;
    }
    //这个i只能在for{}里面使用，不是全局变量
    return 0;
}
```

## 跳转语句

```c++
/*
break 直接跳出来，跳到循环外面
continue 跳过该次循环后循环体中continue后面的内容
*/

int main(){
    int n;
    cin >> n;
    bool is_prime = true;
    
    for (int i = 2; i <= n; i ++){
        if (n % i == 0) {
            is_prime = false;
        }
        break; //break后面需要有分号
    }
    
    if (is_prime) cout << "n是质数" << endl;
    else cout << "n不是质数" << endl;
    return 0;
}
```

## 多重循环

```C++
//多重循环，循环套循环
int main(){
    int n;
    cin >> n;
    //int的时候，只需要一个int，后面直接定义就可以了
    for (int i = 1, k = 1; i <= n; i ++, k ++){
        for (int j = 1; j <= n; j ++, k ++){
            printf("%5d",k); //格式化输出
        }
    cout << endl; //回车，表示换行
    }
    return 0;
}
```

# 4 数组

why? 本来变量需要一个一个定义，现在直接可以定义很多个

## 一维数组

* 数组定义，数组的初始化

```c++
int main(){
    int a[10]; //中括号内表示数组的长度
    int a[3] = {0, 1, 3}; //初始化{}
    int b[] = {0, 1, 3}; //[]中括号内可以不写
    int b[5] = {0, 1, 3}; //定义了一个长度是5的数组，{}没有写的，默认是0
    char d[3] = {'a', 'b', 'c'};
    int m[100] = {0}; //将数组全部初始化为0的写法
    int a[3]; //没有初始化数组都是随机的
    //栈空间，所有开到函数里面数组的数据都会放到栈空间里面（局部变量）
    //空间不够大？开到函数外面去，函数外面放在堆空间，定义在函数外面的数组默认值都是0
}
```

* 访问数组元素

```cpp
int main(){
    int a[100] = {0}; //数组的下标一定是从零开始
    a[0],a[1],a[99]; //这里面每一个变量都是一个普通变量
}
```

* 数组中每一个都可以灵活使用，赋值等等操作

```c++
int main(){
    int a[3] = {0, 1, 2}; 
    cout << a[0] << ' ' << a[1] << ' ' << a[2] << endl;
    a[0] = 5; 
    cout << a[0] << endl;
    return 0;
}
```

1. 数组求斐波那契第n项

```c++
int main(){
    int f[100] = {1,1};
    int n;
    cin >> n;
    
    for (int i = 2; i < n + 1; i++)
        f[i] = f[i-1] + f[i-2];
    
    cout << f[n] << endl;
    return 0;
}
```

2. 逆序输出（不用数组没办法做，因为不知道需要定义多少个变量）

```c++
int main(){
    int a[100];
    
    int n;
    cin >> n;
    5
    for (int i = 0; i < n; i++) cin >> a[i];
    for (int j = n; j > 0; j--) cout << a[j-1] << ' ';
    return 0;
}
```

3. 旋转

```c++
int main(){
    int a[100];
    int n, k;
    cin >> n >> k;
    
    for (int i = 0; i < n; i++) cin >> a[i];
    while (k--){
        int t = a[n-1];
        for (int i = n-2; i >= 0; i--)
            a[i+1] = a[i];
        a[0] = t;
    } 
    for (int i = 0; i < n; i++) cout << a[i] << ' ';
    return 0;
}
```

巧妙的做法，先翻转数组a，再翻转前半部分，再翻转后半部分，用到reverse函数

```c++
#include <iostream>
#include <algorithm>
using namespace std;

int main(){
    int a[100];
    int n, k;
    cin >> n >> k;
    
    for (int i = 0; i < n; i++) cin >> a[i];
    
    reverse(a, a + n);
    reverse(a, a + k);
    reverse(a + k, a + n);
    
    for (int i = 0; i < n; i++) cout << a[i] << ' '; 
    return 0;
}
```

4. **高精度2的N次幂**

问题背景：一个数很大，一般int大概只有10位，如果这个数有三四十位，需要用一个数组来存

倒着存，因为方便进位，数组后面添加比较方便

```c++
//const int N = 3010; //const常量，设置了不能修改，修改会报错
int main(){   
    int a[10000] = {1};
    int t = 1;
    int b = 0;
    int n;
    
    cin >> n;
    
    for(int j = 0 ; j < n; j ++){     
        //内循环做一次乘法
        int temp = 0;
        for (int i = 0; i < t; i++){
            temp += a[i] * 2;
            a[i] = temp % 10;
            temp = temp / 10;
        }
        if (temp) a[ t++ ] = 1;
    }
    //输出数组，倒着输出
    for(int i = t - 1; i >= 0; i--)
        cout << a[i];
    return 0;
}
```

## 二维数组

多维数组就是数组的数组，数组里面的每一个元素都是数组

* 初始化：特殊的初始化暂时没有好的方法来初始化

```c++
int main(){
    int a[10], b[10];
    
    memset(a, 0, sizeof a);
    /*
    memset需要头文件<cstring>
    传入三个参数，第一个需要初始化数组的名字
    第三个，需要初始化的长度，不是肉眼可见的长度，而是Byte，比如一个int需要8Byte,一个Byte = 8bit,也就是8位，8个位置，每个位置0 or 1
    sizeof 自动计算所需要的Byte，不需要括号，它是一个指示符，类似+，-
    第二个，每个Byte初始化的值，所以一般用两个值0/-1, 0则初始化为0，-1则初始化为-1
    */
    
    for (int i = 0; i < 10; i ++) cout << a[i] << ' ';
    return 0;    
}
```

* 数组的复制

```C++
int main(){
    int a[10],b[10];
    for(int i = 0; i < 10; i++) a[i] = i;
    
    memcpy(b,a,sizeof a);//需要头文件同上，传入三个参数，（需要复制的，被复制的，多长（同上的长度规定））
    
    for (int j = 0; j < 10; j ++) cout << b[j] << ' ';
    return 0;
}
```

* 蛇形矩阵 : 思路是偏移量,二维数组的坐标表示，竖过来是x，横着的是y

```c++
int main(){
    int n, m; //n行m列
    cin >> n >> m;
    int dx[] = {0, 1, 0, -1}, dy[] = {1, 0, -1, 0};
    
    for (int x = 0, y = 0, d = 0, k = 1; k <= n * m; k++){
        res[x][y] = k;
        int a = x + dx[d], b = y + dy[d];
        //判断有没有越界 or 重复（填过的地方有人填过了）
        if (a < 0 || a >= n || b < 0 || b >= m || res[a][b]){
            d = (d + 1) % 4; //3 % 4 = 3
            a = x + dx[d], b = y + dy[d];
        }
        //更新下次需要填充的坐标
        x = a, y = b;
    }
    
    for (int i = 0; i < n; i ++){
        for (int j = 0; j < m; j ++) cout << res[i][j] << ' ';
        cout << endl;
    }
    
    return 0;   
}
```

# 5 字符串

## 字符串与整数

字符串是计算机与人类沟通的重要手段

英文字符与数字的对应关系ASCII表，每个常用字符都对应一个$-128 \sim 127$的数字，二者之间可以相互转化

```c++
int main(){
    for (int i = 1; i < 128; i ++) printf("%d:%c\n",i, char(i));    
    return 0;
}
```

需要记住的48 - > 0；65 -> A, 97 -> a，往后面依次+1

字符可以参与运算，运算时会将其当做整数：`int a = 'A' - 'Z'`, `char = 'A' + 2`char事实上存的是一个整数，只有输出的时候是一个字符（给人看的）

1. **输入一行字符，统计出其中数字字符的个数，以及字母字符的个数**

```C++
int main(){
    char c;
    int nums = 0, chars = 0;
    while(cin >> c){
        //知识点在于可以直接c>='0',字符之间可以直接比较，比较的时候被当成数字
        if (c >= '0' && c <= '9') nums ++;
        if (c >= 'a' && c <= 'z' || c >= 'A' && c <= 'Z') chars ++;
    }
    printf("nums:%d\nchars:%d",nums,chars);
    return 0;
}
```

## 字符数组

字符串就是字符数组加上结束符`'\0'`,这个表示空字符

```c++
int main(){
    char a[] = {'C','+','+'}; //字符数组
    char b[] = {'C','+','+','\0'}; //字符数组（长度为4），也可以视为字符串（长度为3）
    char c[] = "C++"; //与b[]是等价的，c[4]
    
    //输出
    cout << a << endl;
    printf("%s\n",b);
    return 0;
}
```

* 后面补充：为什么说字符串是个指针

```c++
int main(){
    //输入
    char s[100];
    scanf("%s",s); //不需要&s,&表示取地址符号，但是字符串本身就是指针
    return 0;
}
```

```c++
int main(){
    char str[100];
    cin >> str; // 输入字符串时，遇到空格或者回车就会停止,输入`abc def`，只会输出`abc`
    cout << str << endl; // 输出字符串时，遇到空格或者回车不会停止，遇到'\0'时停止
    
    //读入一行到一个字符数组里面
    fgets(str, 100, stdin); //str定义的字符数组名字，100最多读入的字符个数，stdin记住就行了
    //fgets会把回车也读进来
    
    //读入一行到一个字符串里面
    string s;
    getline(cin, s);
    
    printf("%s\n", str);
    puts(s); //等价于上面那个，包括了换行符
    return 0;
}
```

字符数组中常用的几个函数

```C++
int main(){
    char s1[] = "C++";
    char s2[] = "Python";
    char s3[100];
    
    cout << strlen(s1) << endl; //输出字符串的长度，不包含\0
    cout << strlen(s2) << endl;
    
    cout << strcmp(s1,s2) << endl; //比较两个字符数组，字典序比较，a < b返回-1， a == b返回0，a > b返回1
    cout << strcpy(s3,s2) << endl; //后一个复制给前一个
    return 0;
}
```

2. **输出只出现一次的字符**

```C++
int count[26];
char str[100010]; //放到函数外面，堆空间

int main(){
    cin >> str;
    int len = strlen(str);
    for (int i = 0; i < len; i ++) count[str[i]-'a'] ++; //这一步的操作比较细节
    //另一种写法 for (int i = 0; str[i]; i ++) 第二个是判断条件的，一个字符串的最后一个是\0,就是false
    //再遍历一遍，输出第一个只出现一次的，为什么还要遍历len,因为count[i]=1不代表它是第一个出现一次的
    for (int i = 0; i < len; i ++){
        if (count[str[i]-'a'] == 1){
            cout << str[i] << endl;
            return 0; //遇到return 0; 函数就停止了，后面不会再执行了
        }
    }
    puts("no");
    return 0;
}
```

## string

实际中很少采用字符数组，而是直接用string，可变长的字符序列

* 定义和初始化

```C++
int main(){
    string s1; //默认，空字符串
    string s2 = s1; //s2为s1的副本，只是值相同，但是不指向同一段地址
    string s3 = "C++"; //s3是该字符串字面值的副本
    string s4(10,'c'); //"cccccccccc"
    return 0;
}
```

* `string`上的操作

```C++
int main(){
    // 读写
    string s1,s2;
    cin >> s1 >> s2; //不可以用scanf读入，cin只会读到空格，如果有空格会停止
    getline(cin, s1); //读入一整行，空格也可以读
    cout << s1 << s2 << endl;
    printf("%s",s1.c_str()); //不能直接printf出来string,需要s1.c_str()
    return 0;
}
```

```C++
int main(){
    string s1;
    cout << s1.empty() << endl; //返回布尔值，判断string是不是空的
    cout << s1.size() << endl; //返回长度，复杂度O(1),不需要遍历，里面存了长度
    return 0;
}
```

`string`支持`>, <, ==, !=`等比较运算符，按照字典序进行比较

`string`相加：

```C++
int main(){
    string s1 = "hello, ", s2 = "world\n";
    string s3 = s1 + s2;  // s3的内容是 hello, world\n
    s1 += s2;  // s1 = s1 + s2
    cout << s3 << endl;
    return 0;
}
```

```c++
//字符串相加的一些细节：做加法运算的时候，字面值和字符都会变成string对象，相加就是串联
//string," ",' '混用的时候，必须保证加法运算符两边各有一个对象是string
string s1 = s1 + ","; //可以
string s2 = "Hello" + ","; //不可以
string s3 = "hello" + ", " + s2; //不可以，加法从左到右进行
```

处理string对象中的字符

```C++
int main(){
    string s  = "Hello, world";
    for (int i = 0; i < s.size(); i ++) cout << s[i] << endl; //当作字符数组操作
    
    for (char c : s) cout << c << endl; //注意这里的char c是s[i]的副本，修改c不会修改s
    for (auto c : s) cout << c << endl; //auto编译器自己去猜变量是什么类型
        c = 'a'; //没有用
        
    for (char &c : s) c = 'a'; // &取地址
    cout << s << endl; //会修改s的值
    
    return 0;
}
```

3. **密码加密**

```c++
int main(){
    string str;
    getline(cin, str);
    
    for (char &c : str){
        if (c >= 'a' && c <= 'z') c = 'a' + (c - 'a' + 1) % 26; //使用偏移量
        else if (c >= 'A' && c <= 'Z') c = 'A' + (c - 'A' + 1) % 26;
    }
    cout << str << endl;
    return 0;
}
```

4. **循环相克令**：挖掘一些更本质的东西

```c++
int main(){
    int n;
    cin >> n;
    
    while(n--){
        string a, b;
        cin >> a >> b;
        
        int x, y;
        if (a == "Hunter") x = 0;
        else if ( a == "Bear") x = 1;
        else x = 2;
        
        if ( b == "Hunter") y = 0;
        else if ( b == "Bear") y = 1;
        else y = 2;
        
        if (x == y) cout << "Tie" << endl;
        else if (x == (y + 1) % 3) cout << "Player1" << endl;
        else cout << "Player2" << endl;
    }
    return 0;
}
```

5. **`stringstream`用法**

   字符串流的默认分隔符为空格

```c++
#include <iostream>
#include <string>
#include <sstream> //加入这个头文件
using namespace std;

int main(){
    string s, a, b;
    getline(cin, s);
    cin >> a >> b;
    
    stringstream ssin(s); //参考的cin的输入，不会读入空格,abd efx是两个输入
    //就是说shid shdij shid,用了这个用法，就类似123 537 236用cin的输入
    string str;
    while(ssin >> str){
        if (str == a) cout << b << ' ';
        else cout << str << ' ';
    }
    return 0;
}
```

6. **双指针初探，第一类双指针**

```c++
#include <iostream>
#include <string>
#include <cstdio>
using namespace std;

int main(){
    int n; 
    cin >> n;
    while(n--){
        string s; 
        cin >> s;
        char c; int count = 0;
        for (int i = 0; i < (int)s.size() ; i ++){
            int j = i;
            while (j < (int)s.size() && s[j] == s[i]) j ++;
            if ( j - i > count){
                count = j - i; c = s[i];
            }
            i = j - 1;
        }
        cout << c << ' ' << count << endl;
    }
    return 0;
}
```

# 6 函数

## 函数基础

* 编写函数，调用函数

  函数调用，有点类似深度优先遍历

  调用函数，被调用的函数需要在上面，先声明才能用

```C++
//int为返回类型, foo为函数名字，()内是由0个或多个形参组成的列表
//函数的返回类型，int char string ，特殊返回类型void，没有返回类型
int foo(int n) 
//函数体,需要括号
{
    int res = 1;
    for(int i = 1; i <= n; i ++){
        res *= i;
    }
    return res; //返回值，不写return，可以，但是会返回一个随机的值
}

int main(){
    int output = foo(5); //调用的时候直接写函数名字，()内写传入的参数，按照顺序传入
    //遇到一个函数，进去，把所有的都走完，然后进行下一步
    cout << output << endl;
    return 0;
}
```

* 形参的参数列表

```C++
int output(void)
/* 传入参数
规则一：可以为空，但是一定要有()
int output()      //隐式表示传入为空
int output(void)  //显式表示传入为空
规则二：每一个变量都要定义类型
int f3(int v1, v2)        // 错误
int f4(int v1, int v2)    // 正确  */
{
    cout << "Hello world" << endl;
}
```

* 全局变量，局部变量，静态变量

```C++
int output(void){
    static int cnt = 0; //只会在第一次调用的时候被初始化，只会被初始化一次
    //静态变量类似于写在函数里面，只有这个函数能够使用的全局变量
    cnt ++;
    cout << "call: " << cnt << " times" << endl;
}

int main(){
    output(); output(); output(); output(); output();
}
```

## 参数传递

* 传值参数：

  1. 当初始化一个**非引用类型**的变量时，初始值被拷贝给变量。此时，对变量的改动不会影响初始值。

  2. 当函数的形参为**引用类型**时，对形参的修改会影响实参的值。

     使用引用的作用：避免拷贝、让函数返回额外信息。（本来只能返回一个值，但是现在通过参数的改变来）

```c++
int max(int &x,int &y) //加入了取地址符号，所以再外部传入的参数在函数里面会被修改
{
    x = 10; y = 20;
    if (x > y) return x;
    else return y;
}

int main(){
    int a = 3; int b = 4;
    cout << max(a,b) << endl;
    cout << a << ' ' << b << endl;
    return 0;
}
```

* 数组参数（一维情况）

  后面会讲，数组事实上就是指针

```C++
//下面几个实际上是等价的，虽然看上去不同
void print(int *a)
void print(int a[])
void print(int a[10])
```

* 多维数组参数

```c++
// void (int m, int n, a[][3]),第一个参数可以省，但是第二个不可以
void output(int m, int n, int a[3][3])
{
    for (int i = 0; i < m; i ++){
        for (int j = 0; j < n; j ++){
            cout << a[i][j] << ' ';
        }
        cout << endl;
    }
}

int main(){
    int a[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}, //写多维数组的时候，逗号不要忘记
    };
    output(3, 3, a); //这里a是数组名称，就不能写成a[3][3]
    return 0;
}
```

注意：数组的参数是引用传递，里面改变形参会改变外面实参的值

* 可以有默认参数，给它传值的时候就是传入的值，不给函数传值得时候就是默认得值，类似python

## return

* 执行到`return`就会退出

## 递归

* 函数自己调用自己，递归

  看不明白的话，可以画图

1. 递归求阶乘

```C++
int fact(int n){
    if (n == 1) return 1; //递归边界
    return n * fact(n - 1);
}

int main(){
    cout << fact(5) << endl;
    return 0;
}
```

2. 递归求斐波那契数列

```c++
int f(int n){
    if (n <= 2) return 1;
    return f(n - 1) + f(n - 2);
}

int main(){
    int n;
    cin >> n;
    cout << f(n) << endl;
    return 0;
}
```

# 7 类，结构体

这里只涉及最简单的类和结构体的知识，继承，多态等等不会涉及

## class

* 定义

```c++
class Person{
    private: //私有，只有类内部可以访问
        int age, height;
        double money;
        string book[100];
    public: //公有，外部也可以访问
        string name;
        
        void say(){
            cout << "I'm" << name << endl;
        }
        
        int get_age(){
            return age;
        }
        
        void add_money(double x){
            money += x;
        }
}; // C++定义类后面一定要有; 不要忘了
```

* 使用（接上面的内容）

```C++
int main(){
    Person c; //定义了对象c
    c.name = "xhl";      // 正确！访问公有变量
    c.age = 18;          // 错误！访问私有变量
    c.add_money(100);
    c.say();
    cout << c.get_age() << endl;
    
    return 0;
}
```

## struct

与类完全是一样的，只有一个区别：类默认是`private`，结构体默认是`public`

一半在写短代码的时候会用到，内容非常复杂的就写到类里面

* 构造函数（类里面也可以有）

```C++
struct Person{
    int age, height;
    double money;
    //可以在函数内部将person几个变量赋值
    Person(int _age, int _height, double _money){
        age = _age;
        height = _height;
        money = _money;
    } //构造函数函数名与类名相同
    
    //构造函数另一种写法：当只是为了赋值，然后这个运行会比上面的快一点
    Person(int _age, int _height, double _money): age(_age), height(_height), money(_money) {}
}; //不要忘记

int main(){
    Person c(18, 180, 10000.0); //有了这个可以传入参数，重写，顺次写入
    cout << c.money << endl;
    return 0;
}
```

 # 8 指针，引用，链表

## 指针

这里只会涉及到指针最简单的应用

* 指针，取指

  指针也可以支持运算

```C++
char a, b; //定义在堆空间里面，从下往上定义（一般认为最下面的是地址是0）
//堆空间里面的变量会默认初始化为0

int main(){
    char c, d; //定义在栈空间里面，从上往下定义
    cout << (void*) &a << endl;
    cout << (void*) &b << endl;
    cout << (void*) &c << endl;
    cout << (void*) &d << endl; // c,d之间差1，因为char类型一个byte为1
    return 0;
}
```

* 数组就是指针

```C++
int main(){
    char c;
    int a[5] = {1, 2, 3, 4, 5};
    cout << a << endl; //数组的名称就是数组第一个所在的地址
    for (int i = 1; i < 5; i ++)
        cout << (void*) &a[i] << endl; //输出每一个之间差4，int变量占4Byte
    
    int* p = a; //int*表示指针了类型的变量
    int** p = a; //表示指针的指针
    cout << p + 1 << endl; //p+1不是表示p的下一个地址，而是看一下p存的类型是什么，洗一个这个类型的变量在那，是加一个变量
    return 0;

}
```

* 引用，别名

```C++
int main(){
    int a = 10;
    int* p = &a; //int* 是一种表示地址的数据类型，&a,取a所在的地址，
    int& p = a; //变量名称是p，类型是int&, 引用，别名，p和a存在同一个地址上, C++的简化写法
    p += 5; //改变p也会改变a,因为它俩就是一个东西
    cout << a << endl;
    return 0;
}
```

* 困惑的地方`&`和`*`

  `*`指针从本质上讲就是存放变量地址的一个变量，可以被改变，包括其所指向的地址的改变和其指向的地址中所存放的数据的改变。

  `&`引用是一个别名，存在具有依附性，所以引用必须在一开始就被初始化，而且其引用的对象在其整个生命周期中是不能被改变的（自始至终只能依附于同一个变量）。

  `int&`, `int*`, `&a`(取a的地址)

```C++
int main()
{
	int a = 5, b = 10, c = 15;
	int *p1;	//指针可以不初始化
	int &d = b;	//引用必须初始化（相当于给一个人起外号要针对那个人）
	p1 = &a;	//p1指向a的地址
}
```

## 链表初步

链表结合了指针和结构体

```c++
//定义节点，里面需要有两个val和Node*
struct Node{
    int val;
    Node* next; //定义了节点指向的地址，Node*是数据类型，next是变量名
    
    //构造函数
    Node(int_val): val(_val), next(NULL){}
    //NULL是空指针，值为0
};

int main(){
    Node node = Node(1); //一般不这么写，这里是定义了一个Node类型的变量
    //一般是生成一个结构体，然后把它放到指针p里面
    Node* p = new Node(1); //new Node(1)表示定义了一个Node类型的变量，返回值是这个变量的地址，放在指针p里面
    Node* q = new Node(2); 
    Node* o = new Node(3);
    p->next = q;
    q->next = o;
    
    //链表的头结点：存第一个结点的地址
    Node* head = p;
    
    //next指针式可以指向另外一个node的
    p->next = p;//表示指向自己
    /*
    如果想调用结构体和类里面的成员变量的时候，调用的如果是变量而非指针的时候.:
    Node a = Node(1); //a是一个变量
    a.next; a.val
    如果调用的是指针就需要->:
    Node* p = new Node(1); //p是一个指针
    p->val; p->next
    */
    
    //链表的遍历，这里定义的是单链表
    for (Node* i = head; i != 0; i->next)
        cout << i->val << endl;
    
    //添加结点，在最前面加结点，因为我们知道头结点
    Node* u = new Node(4);
    u->next = p;
    head = u;
    
    //节点的删除，不是物理删除，是遍历的时候遍历不到这个点了：跳过去，指针值的跳过去
    head->next = (head->next)->next;
    
    return 0;
}
```

1. 链表的删除（伪装）把自己伪装成下一个节点

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    void deleteNode(ListNode* node) {
        //把自己伪装成下一个节点，然后把下一个节点干掉
        node->val = node->next->val;
        node->next = node->next->next;
    }
};
```

2. 二路归并

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* merge(ListNode* l1, ListNode* l2) {
        auto dummy = new ListNode(-1), tail = dummy; //定义一个虚拟的节点
        while(l1 && l2){
            if (l1->val < l2->val){
                tail = tail->next = l1;
                l1 = l1->next;
            }
            else{
                tail = tail->next = l2;
                l2 = l2->next;
            }
        }
        if (l1) tail->next = l1;
        if (l2) tail->next = l2;
        
        return dummy->next;
    }
};
```

# 9 STL

容器：用来存储数据，前面讲过的`string`就是容器

## vector

* 其实是一个数组，变长数组，原理为**倍增**，不支持在任意位置 `O(1)` 插入。为了保证效率，元素的增删一般应该在末尾进行。

```C++
#include <vector>
int main(){
    //定义
    vector<int> a({1, 2, 3});
    vector<int> b[233]; //第一维是233固定了，第二维变长
    struct Rec{
        int x,y;
    };
    vector<Rec> c; //结构体也可以定义为vector
    
    //常用函数,所有的STL容器都支持这两个方法
    a.size(); //函数返回vector的实际长度
    a.empty(); //函数返回一个bool类型，表明vector是否为空
    a.clear(); //清空
    
    //迭代器，类似于指针，数组的下标
    vector<int>::iterator it; = a.begin(); //第一个元素
    a.end(); //最后一个元素的后一个
    *a.begin(); //表示a[0],因为a.begin()取到第一个地址，值加一个*(从地址取值)
    //支持相加减，it + 2 -> a[2]; it -> a[0]
    //所有的迭代器都是左开右闭
    
    //迭代器的遍历
    for (int i = 0;i < a.size(); i ++) cout << a[i] << ' ';
    for (vector<int>::iterator i = a.begin(); i != a.end(); i ++) cout << *i << ' ';
    for (auto x : a) cout << x << ' ';
    
    a.front(); //返回第一个元素
    a.back(); //返回最后一个元素 = a[a.size()-1]
    
    a.push_back(4); //在最后添加元素 O(1)
    a.pop_back(); //在最后是删除元素 O(1)
    
    return 0;
}
```

## queue

头文件`queue`主要包括循环队列`queue`和优先队列`priority_queue`两个容器

* `queue`：先进先出

```C++
#include <queue>
int main(){
    //定义
    queue<int> q;
    queue<double> p;
    struct rec{
        int a, x, y;
    };
    queue<rec> m;
    
    //操作
    q.push(1); //在队尾插入元素
	q.pop();   // 从队头弹出
	q.front(); // 返回队头元素
	q.back();  // 返回队尾元素
    return 0;
}
```

* `priority_queue`：维护一个无序的数组，先弹出最大的

```C++
int main(){
    priority_queue<int> a; //默认是定义一个大根堆
    priority_queue<int, vector<int>, greater<int>>; //小根堆
    a.push()    // 把元素插入堆
	a.pop()     // 删除堆顶元素
	a.top()     // 查询堆顶元素（最大值）
    return 0;
}
```

## stack

先进后出，栈一般竖着画

```C++
#include <stack>
int main(){
    stack<int> stk;
    stk.push()    // 向栈顶插入
	stk.pop()     // 弹出栈顶元素
}
```

## deqeue

* 一个支持在两端高效插入或删除元素的连续线性存储空间。它就像是`vector`和`queue`的结合。(但是运行速度会慢)
* `vector`不支持任意插入，`deque`在头部增删元素仅需要`O(1)`的时间
* `queue`相比，`deque`像数组一样支持随机访问。

```C++
int main(){
    deqeue<int> a;
    a[]              // 随机访问
	a.begin()/a.end()       // 返回deque的头/尾迭代器
	a.front()/a.back()      // 队头/队尾元素
	a.push_back()       // 从队尾入队
	a.push_front()      // 从队头入队
	a.pop_back()        // 从队尾出队
	a.pop_front()       // 从队头出队
	a.clear()           // 清空队列
}
```

## set

动态维护一个有序的集合，底层实现平衡树

* `set`和`multiset`

```c++
#include <set>
int main(){
    set<int> a; //元素不能重复
    multiset<int> b; //元素可以重复
    //size/empty/clear，与vector类似
    
    //set和multiset的迭代器称为“双向访问迭代器”，不支持“随机访问”，支持星号*解除引用，仅支持++和--两个与算术相关的操作。

	set<int>::iterator it = a.begin();
    it ++; //it会指向“下一个”元素, “下一个”元素是指在元素从小到大排序排在it下一名的元素
    it --; //it将会指向排在“上一个”的元素
    
    a.insert(x);
    if (a.find(x) == a.end()); //查找等于x的元素，并返回指向该元素的迭代器
    
    a.lower_bound(x); //查找大于等于x的元素中最小的一个，并返回指向该元素的迭代器
    a.upper_bound(x); //查找大于x的元素中最小的一个，并返回指向该元素的迭代器
    
    a.erase(x); //删除所有等于x的元素
    a.erase(it); //删除这个迭代器
    
    a.count(); //返回集合s中等于x的元素个数，set里面只有0，1之分，而multiset可以有多个
    
    return 0; 
}
```

## map

里面存的二元组，把第一个映射到第二个，键值对，Map的`key`和`value`可以是任意类型

非常有用，可以像用数组一样用别的变量

```C++
#include <map> //映射
int main(){
    map<key_type, value_type> name;

    map<long, long, bool> vis;
    map<string, int> hash;
    map<pair<int, int>, vector<int>> test;
    
    //size/empty/clear/begin/end 与set类似
    
    //插入
    a.insert({pair<key_type, value_type>});
    //查找
    a.find(x); //在变量名为a的map中查找key为x的二元组
    //[]操作符
    h[key]; //返回key映射的value的引用,通过h[key]来得到key对应的value，还可以对h[key]进行赋值操作，改变key对应的value
    return 0;   
}
```
