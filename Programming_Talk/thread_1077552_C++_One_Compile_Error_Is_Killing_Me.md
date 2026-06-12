---
title: "C++ One Compile Error Is Killing Me"
date: 2009-02-22
forum: Programming Talk
---

### Post by tdrusk on 2009-02-22
I'm sick of staring at this code and decided that it would help to just ask.
The error I'm getting is

```
:109: error: expected declaration before ‘}’ token
```

I'm sure it's something stupid, but yeah...


```
#include<iostream>
      2 using namespace std;
      3 #include<string>
      4 struct Circle
      5 {
      6   int radius;
      7   string color;
      8 };
      9 double price, rate;
     10 
     11 int main()
     12 {
     13         for (int dc = 1; dc <=2; dc++)
     14         {
     15                 switch (dc)
     16                 {
     17                         case 1:
     18                         {
     19                                 void countDown(int, int);
     20                                 int high, low, temp;
     21                                 cout << "I will count down from the higher number you enter " <<"to the lower one." << endl;
     22                                 cout << "Enter a number" << endl;
     23                                 cin >> high;
     24                                 cout << "Enter another number > ";
     25                                 cin >> low;
     26                                 if(high < low)
     27                                 {
     28                                         low=temp;
     29                                         low = high;
     30                                         high = temp;
     31                                 }
     32                                 countDown(low, high);
     33                                 return 0;
     34 
     35                         }
     36                         break;
     37 
     38                         case 2:
     39                         {
     40                                 {
     41                                         double askPrice();
     42                                         askPrice();
     43 
     44                                         double calcTax();
     45 
     46                                         calcTax();
     47                                         cout << "On $" << price << ", the taxRate is " << rate << endl;
     48                                 }
     49                                 break;
```

.......

```

     73                                 }
     74                         break;
     75                 }
     76         }
     77 return 0;
     78 }
     79 
     80 
     81 void countDown(int lowest, int highest)
     82 {
     83         int x;
     84         for(x = highest; x >= lowest; --x)
     85                 cout << x << " " << endl;
     86 }
     87 
     88 double askPrice()
     89 {
     90         cout << "Enter price $";
     91         cin>>price;
     92         return price;
     93 }
     94 
     95 double calcTax()
     96 {
     97         const double CUTOFF = 10.00;
     98         const double LOWRATE = 0.05;
     99         const double HIGHRATE = 0.07;
    100         if(price <= CUTOFF)
    101                 rate = LOWRATE;
    102         else
    103                 rate = HIGHRATE;
    104         return rate;
    105 }
    106 
    107 void displayCourseInfo(string course, string instructor, int enrollment)
    108 {
    109         cout << course << " taught by " << instructor <<" enrollment " << enrollment << endl;
    110 }                                        }
    111 
    112 void displayArea(Circle c)
    113 {
    114 double area;
    115 const double PI = 3.14159;
    116 area = c.radius * c.radius * PI;
    117 cout << "The " << c.color << " circle with radius " <<
    118 c.radius <<  " has an area of " << area << endl;
    119 }
    120 
    121 void displayDiameter(Circle c)
    122 {
    123 int diam;
    124 diam = c.radius * 2;
    125 cout << "The " << c.color << " circle with radius " <<  c.radius << " has a diameter of " << diam << endl;
    126 }

```

---

### Post by WW on 2009-02-22
You have an extra } on line 110.

---

### Post by tdrusk on 2009-02-22
> **WW said:**
> You have an extra } on line 110.
ah hahah thanks.

*slaps forehead*

---

