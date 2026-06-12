---
title: "strange sematic error calculating continual growth (c++)"
date: 2007-02-20
forum: Programming Talk
---

### Post by n0dl on 2007-02-20
Hello Im trying to write a program that allows me to calculate growth (money wise) of a certain principle in either daily, monthly or quarterly compoundings utilizing the formula
> F = Pe^rt*ln(1+R/n)
 in c++. Here is the code:
```

#include <iostream>
#include <cmath>
#include <string>
#include <iomanip>

using namespace std;

int main()
{
 int A, n, t;
 double F, e, R, uppow, temp_one;
 string compounds;
 cout<<fixed<<showpoint<<setprecision(2);
 cout<<"\tHow much would like to invest(A)? "; cin>>A;
 cout<<"\tEnter the interest rate(R)? "; cin>>R;
 cout<<"\tEnter the number of compouds per year(Daily, Monthly, Quarterly): ";
 getline(cin,compounds);
 cout<<"\tEnter duration (in years): "; cin>>t;
 if (compounds == "daily" || compounds == "Daily")
 {
  n = 365;
 }
 else if (compounds == "monthly" || compounds == "Monthly")
 {
  n = 12;
 }
 else
 {
  n = 4;
 }
 temp_one = log(1 + R/n);
 uppow = n*t * temp_one;
 e = 2.71;
 F = pow(A*e, uppow);
 cout<<"\t   After "<<t<<" you will have $"<<F<<endl;
 return 0;
}

```
However, whenver i run the program i get this error:
>         How much would like to invest(A)? 10000
        Enter the interest rate(R)? .085
        Enter the number of compouds per year(Daily, Monthly, Quarterly):       Enter duration (in years):
The first two parts are fine. Then when it asks for how many times its compounded it skips and goes straight to asking for the duration. The output is then some strange garbage. Any help is appreciated. Thank you

---

### Post by Lux Perpetua on 2007-02-20
> **n0dl said:**
> Hello Im trying to write a program that allows me to calculate growth (money wise) of a certain principle in either daily, monthly or quarterly compoundings utilizing the formula

 in c++. Here is the code:
```

#include <iostream>
#include <cmath>
#include <string>
#include <iomanip>

using namespace std;

int main()
{
 int A, n, t;
 double F, e, R, uppow, temp_one;
 string compounds;
 cout<<fixed<<showpoint<<setprecision(2);
 cout<<"\tHow much would like to invest(A)? "; cin>>A;
 cout<<"\tEnter the interest rate(R)? "; cin>>R;
 cout<<"\tEnter the number of compouds per year(Daily, Monthly, Quarterly): ";
 getline(cin,compounds);
 cout<<"\tEnter duration (in years): "; cin>>t;
 if (compounds == "daily" || compounds == "Daily")
 {
  n = 365;
 }
 else if (compounds == "monthly" || compounds == "Monthly")
 {
  n = 12;
 }
 else
 {
  n = 4;
 }
 temp_one = log(1 + R/n);
 uppow = n*t * temp_one;
 e = 2.71;
 F = pow(A*e, uppow);
 cout<<"\t   After "<<t<<" you will have $"<<F<<endl;
 return 0;
}

```
However, whenver i run the program i get this error:

The first two parts are fine. Then when it asks for how many times its compounded it skips and goes straight to asking for the duration. The output is then some strange garbage. Any help is appreciated. Thank youI think the problem is that "cin >> R" leaves the newline in the stream, causing the subsequent getline to read only whitespace. "cin >> compounds" would fix this, although it would change the functionality (it would take the next word, not the next line, but the former seems more intuitive to me anyway (and more consistent with your other inputting)).

---

### Post by n0dl on 2007-02-20
Ahh i see! Of course! I forgot that getline fills up a buffer and in order to use it you have to clear the buffer before use. I just cin.ignore(); right before the getline statement and it worked. Thanks

---

