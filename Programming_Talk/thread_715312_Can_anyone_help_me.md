---
title: "Can anyone help me?"
date: 2008-03-04
forum: Programming Talk
---

### Post by kool_kat_os on 2008-03-04
I am writing a small c++ app. in Win32 API

here is the code:

[PHP]//Temprature Conversion Program
//Created by Aakash Patel
using namespace std;
#include <iostream>
int main ()
{
int temp;
system ("color F0");
system ("title Temprature Converter");
cout << "Welcome to the Temprature Conversion Program\n";
cout << "Author: Aakash Patel\n";
cout << "-----------\n";
cout << "Please select the temprature that you would like to convert from: \n";
cout << "Press 1 for Fahrenheit\n";
cout << "Press 2 for Celcius\n";
cout << "Press 3 for Kelvin\n";
cout << "> ";
cin >> temp;
system ("cls");
if (temp == 1)  
{  
       int temp;
       cout << "Please select the temprature that you would like to:\n";
       cout << "Press 1 for Celcius\n";
       cout << "Press 2 for Kelvin\n";
       cout << "> ";
       cin >> temp;
       system ("cls");
       if (temp == 1)
       {
                    int temp;
                    cout << "Please enter the temprature in fahrenhiet that you would\n"; 
                    cout << "like to convert to celcius\n";
                    cout << "> ";
                    cin >> temp;
                    system ("cls");
                    cout << "The temprature you entered in fahrenhiet is: " << temp << "\n";
                    cout << "That temprature converted to celcius is: " << (temp-32.00)*5.00/9.00 << "\n";
                    system ("PAUSE");
                    return 0;
       }
       if (temp == 2)
       {
                    int temp;
                    cout << "Please enter the temprature in fahrenhiet that you would\n";
                    cout << "like to convert to kelvin\n";
                    cout << "> ";
                    cin >> temp;
                    system ("cls");
                    cout << "The temprature you entered in farenhiet is: " << temp << "\n";
                    cout << "That temprature converted to kelvin is: " << (temp+459.67)/9.00/5.00 << "\n";
                    system ("PAUSE");
                    return 0;
       }                    
}
if (temp == 2)
{
       int temp;
       cout << "Please select the temprature that you would like to:\n";
       cout << "Press 1 for Fahrenhiet\n";
       cout << "Press 2 for Kelvin\n";
       cout << "> ";
       cin >> temp;
       system ("cls");
       if (temp == 1)
       {
                    int temp;
                    cout << "Please enter the temprature in celcius that you would\n"; 
                    cout << "like to convert to fahrenhiet\n";
                    cout << "> ";
                    cin >> temp;
                    system ("cls");
                    cout << "The temprature you entered in celcius is: " << temp << "\n";
                    cout << "That temprature converted to fahrehiet is: " << temp*9.00/5.00+32.00 << "\n";
                    system ("PAUSE");
                    return 0;
       }
       if (temp == 2)
       {
                    int temp;
                    cout << "Please enter the temprature in celcius that you would\n";
                    cout << "like to convert to kelvin\n";
                    cout << "> ";
                    cin >> temp;
                    system ("cls");
                    cout << "The temprature you entered in celcius is: " << temp << "\n";
                    cout << "That temprature converted to kelvin is: " << (temp*9.00/5.00)+32.00 << "\n";
                    system ("PAUSE");
                    return 0;
       }                    
}
if (temp == 3)
{
int temp;
       cout << "Please select the temprature that you would like to:\n";
       cout << "Press 1 for Fahrenhiet\n";
       cout << "Press 2 for Celcius\n";
       cout << "> ";
       cin >> temp;
       system ("cls");
       if (temp == 1)
       {
                    int temp;
                    cout << "Please enter the temprature in kelvin that you would\n"; 
                    cout << "like to convert to fahrenhiet\n";
                    cout << "> ";
                    cin >> temp;
                    system ("cls");
                    cout << "The temprature you entered in kelvin is: " << temp << "\n";
                    cout << "That temprature converted to fahrehiet is: " << (temp*1.80)-459.67 << "\n";
                    system ("PAUSE");
                    return 0;
       }
       if (temp == 2)
       {
                    int temp;
                    cout << "Please enter the temprature in kelvin that you would\n";
                    cout << "like to convert to celcius\n";
                    cout << "> ";
                    cin >> temp;
                    system ("cls");
                    cout << "The temprature you entered in kelvin is: " << temp << "\n";
                    cout << "That temprature converted to celcius is: " << temp-273.15 << "\n";
                    system ("PAUSE");
                    return 0;
       }
}
}


  
[/PHP]

i have these thing in it [PHP]system ("PAUSE")[/PHP]

how do i make it so that it says "press q to quit" or "press r to restart"???

---

### Post by mike_g on 2008-03-04
Instead of system("pause"); perhaps something like:
```

[COLOR="Green"]#include <cctype> //Include header for tolower function[/COLOR]
char ch;
do
{
    cout << "press q to quit or r to restart\n";
    cin.get(ch);
    tolower(ch);
}(while (ch != 'q') && (ch != 'r'));

```

I havent tested it, but it might give you an idea :)

It might work well if you wrap it in a function too.

---

### Post by kool_kat_os on 2008-03-04
> **mike_g said:**
> Instead of system("pause"); perhaps something like:
```

[COLOR="Green"]#include <cctype> //Include header for tolower function[/COLOR]
char ch;
do
{
    cout << "press q to quit or r to restart\n";
    cin.get(ch);
    tolower(ch);
}(while (ch != 'q') && (ch != 'r'));

```

I havent tested it, but it might give you an idea :)

It might work well if you wrap it in a function too.

where do i put it?
(i know where the cctype goes, but everything else)

EDIT: I got it...it doesnt work

---

### Post by kool_kat_os on 2008-03-04
when i press "r " it  it exits

---

### Post by mike_g on 2008-03-04
If you want to repeat your program you will want to put it all in a main loop. EG:
```
char repeat = 'r';
while(repeat != 'q')
{
    //Code goes here
   
    do
    {
        cout << "press q to quit or r to restart\n";
        cin.get(repeat);
        tolower(repeat);
    }(while (repeat != 'q') && (repeat != 'r'));
}
```
This would make all the code in the outer loop repeat until the user enters 'q' at the prompt.

---

### Post by kool_kat_os on 2008-03-04
ok...uh....forget about the restart part....i just want to make it say..."press q to quit"

---

### Post by LaRoza on 2008-03-04
> **kool_kat_os said:**
> ok...uh....forget about the restart part....i just want to make it say..."press q to quit"

Then make it say that...

---

### Post by kool_kat_os on 2008-03-04
[PHP]                   char ch;
                    do
                    {
                    cout << "press q to quit\n";
                    cin.get(ch);
                    tolower(ch);
                    }while (ch != 'q');[/PHP]

when i get to this part it says press q to quit twice

EDIT: what does the ! stand for?

---

### Post by kool_kat_os on 2008-03-04
here is a screenshot

EDIT: i just realized i spelled Fahrenheit wrong

---

### Post by mike_g on 2008-03-04
Ok, here you go:
```
//Temprature Conversion Program
//Created by Aakash Patel
using namespace std;
#include <iostream>
#include <cctype>
int main ()
{
    char restart = 'r';
    while(restart != 'q')
    {
        int temp;
        system ("color F0");
        system ("title Temprature Converter");
        cout << "Welcome to the Temprature Conversion Program\n";
        cout << "Author: Aakash Patel\n";
        cout << "-----------\n";
        cout << "Please select the temprature that you would like to convert from: \n";
        cout << "Press 1 for Fahrenheit\n";
        cout << "Press 2 for Celcius\n";
        cout << "Press 3 for Kelvin\n";
        cout << "> ";
        cin >> temp;
        system ("cls");
        if (temp == 1)  
        {  
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Celcius\n";
               cout << "Press 2 for Kelvin\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in fahrenhiet that you would\n"; 
                            cout << "like to convert to celcius\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in fahrenhiet is: " << temp << "\n";
                            cout << "That temprature converted to celcius is: " << (temp-32.00)*5.00/9.00 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in fahrenhiet that you would\n";
                            cout << "like to convert to kelvin\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in farenhiet is: " << temp << "\n";
                            cout << "That temprature converted to kelvin is: " << (temp+459.67)/9.00/5.00 << "\n";
               }                    
        }
        if (temp == 2)
        {
               int temp;
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Fahrenhiet\n";
               cout << "Press 2 for Kelvin\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in celcius that you would\n"; 
                            cout << "like to convert to fahrenhiet\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in celcius is: " << temp << "\n";
                            cout << "That temprature converted to fahrehiet is: " << temp*9.00/5.00+32.00 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in celcius that you would\n";
                            cout << "like to convert to kelvin\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in celcius is: " << temp << "\n";
                            cout << "That temprature converted to kelvin is: " << (temp*9.00/5.00)+32.00 << "\n";
               }                    
        }
        if (temp == 3)
        {
        int temp;
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Fahrenhiet\n";
               cout << "Press 2 for Celcius\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in kelvin that you would\n"; 
                            cout << "like to convert to fahrenhiet\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in kelvin is: " << temp << "\n";
                            cout << "That temprature converted to fahrehiet is: " << (temp*1.80)-459.67 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in kelvin that you would\n";
                            cout << "like to convert to celcius\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in kelvin is: " << temp << "\n";
                            cout << "That temprature converted to celcius is: " << temp-273.15 << "\n";                           
               }
        }
        
        do
        {
            cin.ignore();
            cout << "press q to quit or r to restart\n";
            cin.get(restart);
            tolower(restart);
        }while ((restart != 'q') && (restart != 'r'));    
    }
    return 0;
}  
```
I hope you will check out the code and work out what it does as loops are very useful to know in programming. 

One problem you had was that you were returning from main before you got to the end of your program. 

Also, its best to keep stuff that dosent specifically need to be in if statements out of it as you can save on a lot of repetitive code that way and it makes your prog easier to read.

Hope that helps.

---

### Post by kool_kat_os on 2008-03-04
> **mike_g said:**
> 
I hope you will check out the code and work out what it does as loops are very useful to know in programming. 

One problem you had was that you were returning from main before you got to the end of your program. 

Also, its best to keep stuff that dosent specifically need to be in if statements out of it as you can save on a lot of repetitive code that way and it makes your prog easier to read.

Hope that helps.

i new to programming...so thanks alot:) ill try it

---

### Post by nanotube on 2008-03-04
> **kool_kat_os said:**
> 

EDIT: what does the ! stand for?

!= means "not equal"

---

### Post by kool_kat_os on 2008-03-04
> **mike_g said:**
> Ok, here you go:
```
//Temprature Conversion Program
//Created by Aakash Patel
using namespace std;
#include <iostream>
#include <cctype>
int main ()
{
    char restart = 'r';
    while(restart != 'q')
    {
        int temp;
        system ("color F0");
        system ("title Temprature Converter");
        cout << "Welcome to the Temprature Conversion Program\n";
        cout << "Author: Aakash Patel\n";
        cout << "-----------\n";
        cout << "Please select the temprature that you would like to convert from: \n";
        cout << "Press 1 for Fahrenheit\n";
        cout << "Press 2 for Celcius\n";
        cout << "Press 3 for Kelvin\n";
        cout << "> ";
        cin >> temp;
        system ("cls");
        if (temp == 1)  
        {  
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Celcius\n";
               cout << "Press 2 for Kelvin\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in fahrenhiet that you would\n"; 
                            cout << "like to convert to celcius\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in fahrenhiet is: " << temp << "\n";
                            cout << "That temprature converted to celcius is: " << (temp-32.00)*5.00/9.00 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in fahrenhiet that you would\n";
                            cout << "like to convert to kelvin\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in farenhiet is: " << temp << "\n";
                            cout << "That temprature converted to kelvin is: " << (temp+459.67)/9.00/5.00 << "\n";
               }                    
        }
        if (temp == 2)
        {
               int temp;
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Fahrenhiet\n";
               cout << "Press 2 for Kelvin\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in celcius that you would\n"; 
                            cout << "like to convert to fahrenhiet\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in celcius is: " << temp << "\n";
                            cout << "That temprature converted to fahrehiet is: " << temp*9.00/5.00+32.00 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in celcius that you would\n";
                            cout << "like to convert to kelvin\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in celcius is: " << temp << "\n";
                            cout << "That temprature converted to kelvin is: " << (temp*9.00/5.00)+32.00 << "\n";
               }                    
        }
        if (temp == 3)
        {
        int temp;
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Fahrenhiet\n";
               cout << "Press 2 for Celcius\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in kelvin that you would\n"; 
                            cout << "like to convert to fahrenhiet\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in kelvin is: " << temp << "\n";
                            cout << "That temprature converted to fahrehiet is: " << (temp*1.80)-459.67 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in kelvin that you would\n";
                            cout << "like to convert to celcius\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in kelvin is: " << temp << "\n";
                            cout << "That temprature converted to celcius is: " << temp-273.15 << "\n";                           
               }
        }
        
        do
        {
            cin.ignore();
            cout << "press q to quit or r to restart\n";
            cin.get(restart);
            tolower(restart);
        }while ((restart != 'q') && (restart != 'r'));    
    }
    return 0;
}  
```
I hope you will check out the code and work out what it does as loops are very useful to know in programming. 

One problem you had was that you were returning from main before you got to the end of your program. 

Also, its best to keep stuff that dosent specifically need to be in if statements out of it as you can save on a lot of repetitive code that way and it makes your prog easier to read.

Hope that helps.

it sometimes works right when you select specific conversions...but others....no

---

### Post by mike_g on 2008-03-04
Hmm.. Well i think the problems somewhere else in your code as I removed all the return 0 statements from in the if statements. 

Good luck with it ;)

---

### Post by kool_kat_os on 2008-03-04
Ok...now i jsut tring to make it quit with the q thing...i was messing around...what wrong?

[PHP]//Temprature Conversion Program
//Created by Aakash Patel
using namespace std;
#include <iostream>
#include <cctype>
int main ()
{
    char quit = 'q';
    {
        int temp;
        system ("color F0");
        system ("title Temprature Converter");
        cout << "Welcome to the Temprature Conversion Program\n";
        cout << "Author: Aakash Patel\n";
        cout << "-----------\n";
        cout << "Please select the temprature that you would like to convert from: \n";
        cout << "Press 1 for Fahrenheit\n";
        cout << "Press 2 for Celcius\n";
        cout << "Press 3 for Kelvin\n";
        cout << "> ";
        cin >> temp;
        system ("cls");
        if (temp == 1)  
        {  
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Celcius\n";
               cout << "Press 2 for Kelvin\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in fahrenhiet that you would\n"; 
                            cout << "like to convert to celcius\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in fahrenhiet is: " << temp << "\n";
                            cout << "That temprature converted to celcius is: " << (temp-32.00)*5.00/9.00 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in fahrenhiet that you would\n";
                            cout << "like to convert to kelvin\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in farenhiet is: " << temp << "\n";
                            cout << "That temprature converted to kelvin is: " << (temp+459.67)/9.00/5.00 << "\n";
               }                    
        }
        if (temp == 2)
        {
               int temp;
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Fahrenhiet\n";
               cout << "Press 2 for Kelvin\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in celcius that you would\n"; 
                            cout << "like to convert to fahrenhiet\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in celcius is: " << temp << "\n";
                            cout << "That temprature converted to fahrehiet is: " << temp*9.00/5.00+32.00 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in celcius that you would\n";
                            cout << "like to convert to kelvin\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in celcius is: " << temp << "\n";
                            cout << "That temprature converted to kelvin is: " << (temp*9.00/5.00)+32.00 << "\n";
               }                    
        }
        if (temp == 3)
        {
        int temp;
               cout << "Please select the temprature that you would like to:\n";
               cout << "Press 1 for Fahrenhiet\n";
               cout << "Press 2 for Celcius\n";
               cout << "> ";
               cin >> temp;
               system ("cls");
               if (temp == 1)
               {
                            int temp;
                            cout << "Please enter the temprature in kelvin that you would\n"; 
                            cout << "like to convert to fahrenhiet\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in kelvin is: " << temp << "\n";
                            cout << "That temprature converted to fahrehiet is: " << (temp*1.80)-459.67 << "\n";
               }
               if (temp == 2)
               {
                            int temp;
                            cout << "Please enter the temprature in kelvin that you would\n";
                            cout << "like to convert to celcius\n";
                            cout << "> ";
                            cin >> temp;
                            system ("cls");
                            cout << "The temprature you entered in kelvin is: " << temp << "\n";
                            cout << "That temprature converted to celcius is: " << temp-273.15 << "\n";                           
               }
        }
        
        do
        {
            cin.ignore();
            cout << "press q to quit\n";
            cin.get(quit);
            tolower(quit);
        }while ((quit != 'q'));    
    }
    return 0;
}
[/PHP]

EDIT: i dont know what i doing

---

### Post by LaRoza on 2008-03-04
> **kool_kat_os said:**
> 
EDIT: i dont know what i doing

I see.

Perhaps you should start over again, and try to understand what you are doing before doing it.

---

### Post by kool_kat_os on 2008-03-04
> **LaRoza said:**
> I see.

Perhaps you should start over again, and try to understand what you are doing before doing it.

im talking about the stuff i added because the guy told me to in  this thread....i know what everything else does.

---

### Post by bben on 2008-03-04
```
                    cout << "Please enter the temprature in fahrenhiet that you would\n";
```

Nothing to do with the actual code, but "temperature" "Fahrenheit"... :KS

Oh, and Kelvin, Celcius and Fahrenheit need CAPS

hey, it's all part of debugging :P
no offence btw!

---

### Post by kool_kat_os on 2008-03-04
> **bben said:**
> ```
                    cout << "Please enter the temprature in fahrenhiet that you would\n";
```

Nothing to do with the actual code, but "temperature" "Fahrenheit"... :KS

Oh, and Kelvin, Celcius and Fahrenheit need CAPS

hey, it's all part of debugging :P
no offence btw!

thanks anyway...i was in a hurry so i just copy and pasted the rest:)

---

