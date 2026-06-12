---
title: "Problems with random numbers (C++)"
date: 2006-12-06
forum: Programming Talk
---

### Post by n0dl on 2006-12-06
Hello, I have been trying to make a dice rolling program over the last couple of days as a hobby (and for my RPG gaming nights) and have had problems generating random numbers. Here is the code:
```

#include <iostream>
#include <ctime>
#include <cstdlib>
using namespace std;
void menu ();
int d_twen();
int d_twel();
int d_ten();
int d_eight();
int d_six();
int d_four();
int d_perc();
int main()
{
 int no_of_times, x, choice;
 char cont;
 menu();
 srand(time(0));
 do
 {
        x = 1;
        cout<<"Which dice would you like to roll? (type 8 to display the menu or
 9 to exit) "; cin>>choice;
       if (choice == 8 || choice == 9)
        {
                no_of_times = 1;
        }
        else
        {
                cout<<"How many rolls would you like to make? "; cin>>no_of_time
s;
        }
                while ( x <= no_of_times )
                {
                        switch (choice)
                        {
                                case 1: cout<<d_twen()<<" "; break;
                                case 2: cout<<d_twel()<<" "; break;
                                case 3: cout<<d_ten()<<" "; break;
                                case 4: cout<<d_eight()<<" "; break;
                                case 5: cout<<d_six()<<" "; break;
                                case 6: cout<<d_four()<<" "; break;
                                case 7: cout<<d_perc()<<" "; break;
                                case 8: menu();
                                case 9: break;
                        }
                        x++;
                        cout<<endl;
                }
 }while (choice != 9);
 return 0;
} 

void menu ()
{
 cout<<"+------------------------------+\n";
 cout<<"|         Dice     Roller      |\n";
 cout<<"|         written by n0dl      |\n";
 cout<<"| 1.) D20                      |\n";
 cout<<"| 2.) D12                      |\n";
 cout<<"| 3.) D10                      |\n";
 cout<<"| 4.) D8                       |\n";
 cout<<"| 5.) D6                       |\n";
 cout<<"| 6.) D4                       |\n";
 cout<<"| 7.) D100                     |\n";
 cout<<"+------------------------------+\n";
}

int d_twen ()
{
 srand(time(0));
 return rand()%20+1;
}

int d_twel ()
{
 srand(time(0));
 return rand()%12+1;
}

int d_ten ()
{
 srand(time(0));
 return rand()%10+1;
}

int d_eight ()
{
 srand(time(0));
 return rand()%8+1;
}
int d_six ()
{
 srand(time(0));
 return rand()%6+1;
}

int d_four ()
{
 srand(time(0));
 return rand()%4+1;
}

int d_perc ()
{
 srand(time(0));
 return rand()%100+1;
}

```
The syntax and everything is right so the error is semantic. Whenever I call any dice to roll instead of getting different numbers for the user defined number of rolls i get 3 of the same output. For example
Enter choice: 1 //Rolling a D20 (random number 1 - 20)
How many times? 3 //Three different rolls
4 4 4
Does anyone know how I can get random numbers correctly?

---

### Post by Lster on 2006-12-06
[Post edited.]

Have a look at LibC Manual:

[http://www.gnu.org/software/libc/manual/html_node/Simple-Calendar-Time.html#Simple-Calendar-Time](http://www.gnu.org/software/libc/manual/html_node/Simple-Calendar-Time.html#Simple-Calendar-Time)

---

### Post by n0dl on 2006-12-06
D00d! Thanks Lster! it worked! Ill remember to include this tidbit in the documentation.

---

### Post by Kegladar on 2008-03-25
First off, can i use this code to help with learning to make programs? And second, I don't understand what the time has to do with the problem, and how to fix it. Can you please tell me?

---

### Post by LaRoza on 2008-03-25
> **Kegladar said:**
> First off, can i use this code to help with learning to make programs? And second, I don't understand what the time has to do with the problem, and how to fix it. Can you please tell me?

Probably not without knowledge of C++...

If you want to learn, see the sticky, and my wiki.

---

### Post by Kegladar on 2008-03-25
ok, thanks

---

