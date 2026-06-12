---
title: "Need help with &quot;nan&quot; in my program"
date: 2011-10-13
forum: Programming Talk
---

### Post by greenberet on 2011-10-13
Hey guys, i`ve just started studying programming and i`ve run into a problem i don`t know how to fix, its very very basic, but i`m a newbie, anyway i how you can help me out, because i saw someone with a similar program, but couldn`t quite understand how to fix it in my program.

#include <iostream>
using namespace std;

int main()
{
    int a, b=0, n=0, c, ok;
    double summa;    
                   
    do
    {
    summa = 0;
    cout << "Ievadi naturalu skaitli" << endl;
    cin >> a;     
    if (a >= 0) 

    {
        n=0;  

         if (a==0)
         cout <<a<<endl;
         while (a!=0)
            {
            b = a % 10;
            a=a/10;
            summa=summa+b;
            n++;
            }
        cout << summa/n << endl;


    }

    else
    {
        cout <<"Ievaditais skaitlis ir negativs";
    }
    cout << " Vai turpinaat (1) vai beigt (0)?" << endl;
    cin >> ok;
    } while (ok == 1);
    return 0;
}

when i enter 0 in the consule, he gives out the asked for 0 but the program also adds "nan" at the end, how do i get rid of it?

thanks for the support.

---

### Post by Zugzwang on 2011-10-13
In your program, you initialise n to 0 and only modify it if a is not equal to 0 (in the "while (a!=0)" loop).

Then you execute the following line:
```

cout << summa/n << endl;

```

Since n is still 0 when a was 0, you divide by 0 here, which results in "not a number"=NaN as the result.

---

