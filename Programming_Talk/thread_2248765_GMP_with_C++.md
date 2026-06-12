---
title: "GMP with C++"
date: 2014-10-16
forum: Programming Talk
---

### Post by bikewrecker on 2014-10-16
Hi guys. I'm trying to get this program to work with more precision using GMP.

```

      1 #include <iostream>
      2 #include <math.h>
      3 #include <gmpxx.h>
      4 using namespace std;
      5
      6 double factorial(int k);
      7
      8 int main()
      9 {
     10         double x = 1; double Sum = 0; int m = 1; double J = 0;
     11
     12         for(m = 0; m < 9; m++)
     13         {
     14                 for(int k = 0; k < 1000; k++)
     15                 {
     16                         Sum = Sum + pow((-(x*x)/4),k)/(factorial(k)*factorial(m+k));
     17                 }
     18                 cout<< "Sum = " << Sum << endl;
     19                 J = pow((x/2),m)* Sum;
     20                 cout << "m = " << m << "  => J_m = "<< J << endl << endl;
     21                 Sum = 0;
     22         }
     23
     24 }
     25
     26 double factorial(int k)
     27 {
     28         if(k == 0)
     29         {
     30                 return 1;
     31         } else {
     32                 double returner = k;
     33                 while(k > 2)
     34                 {
     35                         returner = returner*(k-1);
     36                         k = k-1;
     37                 }
     38                 return returner;
     39         }
     40 }
~


```

The output looks like this:

```

Sum = 0.765198
m = 0  => J_m = 0.765198

Sum = 0.880101
m = 1  => J_m = 0.440051

Sum = 0.459614
m = 2  => J_m = 0.114903

Sum = 0.156507
m = 3  => J_m = 0.0195634

Sum = 0.0396262
m = 4  => J_m = 0.00247664

Sum = 0.00799225
m = 5  => J_m = 0.000249758

Sum = 0.00134005
m = 6  => J_m = 2.09383e-05

Sum = 0.000192298
m = 7  => J_m = 1.50233e-06

Sum = 2.41212e-05
m = 8  => J_m = 9.42234e-08


```
Which is awesome, it's just not precise enough. (I need at least 10 digits accuracy.)

My GMP program looks like this:

```

      1 #include <iostream>
      2 #include <math.h>
      3 #include <gmpxx.h>
      4 using namespace std;
      5
      6 double factorial(int k);
      7
      8 int main()
      9 {
     10         double x = 1; int m = 1;// double J = 0; double Jp = 0; double Jm = 0;
     11         mpz_t J, Sum, Num;
     12         mpz_init(J);
     13         mpz_init(Num);
     14         mpz_init(Sum);
     15         mpz_set_ui(J,0);
     16         mpz_set_ui(Sum,0);
     17         mpz_set_ui(Num,1);
     18         for(m = 0; m < 9; m++)
     19         {
     20                 for(int k = 0; k < 1000; k++)
     21                 {
     22                         mpz_add_ui(Sum, Sum, pow((-(x*x)/4),k)/(factorial(k)*factorial(m+k)));
     23                 }
     24                 mpz_mul_ui(Num,Num,pow((x/2),m));
     25                 cout << "Sum = " ;
     26                 mpz_out_str(stdout,10,Sum);
     27                 cout << endl;
     28                 //mpz_mul_ui(J, Num, Sum);
     29                 cout << "m = " << m << "=> J_m = ";
     30                 mpz_out_str(stdout,10,J);
     31                 cout << endl;
     32                 mpz_set_ui(Sum, 0);
     33         }
     34         mpz_clear(J);
     35         mpz_clear(Sum);
     36         mpz_clear(Num);
     37
     38 }
     39
     40 double factorial(int k)
     41 {
     42         if(k == 0)
     43         {
     44                 return 1;
     45         } else {
     46                 double returner = k;
     47                 while(k > 2)
     48                 {
     49                         returner = returner*(k-1);
     50                         k = k-1;
     51                 }
     52                 return returner;
     53         }
     54 }


```

But the mpz_add_ui command isn't doing what it's supposed to because the output is:

```

Sum = 1
m = 0=> J_m = 0
Sum = 1
m = 1=> J_m = 0
Sum = 0
m = 2=> J_m = 0
Sum = 0
m = 3=> J_m = 0
Sum = 0
m = 4=> J_m = 0
Sum = 0
m = 5=> J_m = 0
Sum = 0
m = 6=> J_m = 0
Sum = 0
m = 7=> J_m = 0
Sum = 0
m = 8=> J_m = 0


```

also if I uncomment out the "mpz_mul_ui(J, Num, Sum);" line i get this error:
```

Homework1B.cpp:26:25: error: invalid conversion from ‘__mpz_struct*’ to ‘long unsigned int’ [-fpermissive]
   mpz_mul_ui(J, Num, Sum);
                         ^
In file included from /usr/include/gmpxx.h:43:0,
                 from Homework1B.cpp:3:
/usr/include/gmp.h:945:21: error:   initializing argument 3 of ‘void __gmpz_mul_ui(mpz_ptr, mpz_srcptr, long unsigned int)’ [-fpermissive]
 __GMP_DECLSPEC void mpz_mul_ui (mpz_ptr, mpz_srcptr, unsigned long int);
                     ^

```

---

### Post by ofnuts on 2014-10-17
A 'double' has a [52 bits significand]("http://en.wikipedia.org/wiki/Double-precision_floating-point_format"), which means the accuracy is around 15-17 decimal digits. Your problem isn't the accuracy of the computation but the [format of the printed output]("http://stackoverflow.com/questions/20539608/using-various-format-specifiers-of-c-in-c").

---

### Post by bikewrecker on 2014-10-17
Oh duh. There goes like 4 hours of wasted work lol. I'd still like to figure out what I was doing wrong though because I'll probably need to know it for the rest of my numerical analysis class.

---

### Post by ofnuts on 2014-10-18
Just not using format specifiers in your cout statement... 

Also, if the double is not accurate enough (which I doubt) there is a "long double" (80 bits instead of 64).

---

