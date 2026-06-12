---
title: "C++ Clock Program"
date: 2006-11-07
forum: Programming Talk
---

### Post by APNelson.L on 2006-11-07
I am fairly new to c++ and I have made a program that is basically a little clock, here is the code for it:
```
//time
#include <iostream>
#include <windows.h>

using namespace std;

int main()
{
    int a = 0;
    int h;
    int m;
    int s;
    
    mistake:
    
    cout << "What is the current hour?\n";
    cin >> h;
    
    cout << "\nWhat is the current minute?\n";
    cin >> m;
    
    cout << "\nWhat is the current second?\n";
    cin >> s;
    
    if (h > 24 || m > 60 || s > 60)
    {
          cout << "\nPlease try again!\n\n";
          goto mistake;
    }
    
    cout << "\n\n\n\n\n\n\n\n\n\n\n\n\n";
    
    while (a == 0)
    {
          cout << h << ":" << m << ":" << s << "\n\n\n\n\n\n\n\n\n\n\n\n\n";
          Sleep(1000);
          s++;
          if (s > 59)
          {
                s = 0;
                m++;
                
                if (m > 59)
                {
                      m = 0;
                      h++;
                      
                      if (h > 24)
                      {
                            h = 0;
                      }
                }
          }
    }
}

```
currently I have made it so that there are a lot of new lines so it appears that the command prompt is only displaying the time once over and over again. When you scroll up on the command prompt it is clear that this is not true though. I was wondering if there is a way to essentially clear the command prompt so that when you scroll up there is nothing.

---

### Post by themusicwave on 2006-11-07
On windows calling System("cls") clears the command prompt.

I think you need a library to use it though.  it might be called stdlib I don't really remember.

Something cool is that you can use any dos command inside the System("") command.  So for instance calling System("Color 0A") will make your program have green text.  Have some fun with that.

---

### Post by APNelson.L on 2006-11-07
Thanks I think I will have some fun and that opens up a lot of possibilities for me.

---

### Post by Houman on 2006-11-07
Hi there;

I think System("clear") would do the job, on linux clear is used instead of cls, but basically what themusicwave said is what i would do as well, 

regards

Houman

---

### Post by APNelson.L on 2006-11-07
Okay so now my program looks like this:
```
//time
#include <iostream>
#include <windows.h>
#include <stdlib.h>

using namespace std;

int main()
{
    int a = 0;
    int h;
    int m;
    int s;
    
    mistake:
    
    cout << "What is the current hour?\n";
    cin >> h;
    
    cout << "\nWhat is the current minute?\n";
    cin >> m;
    
    cout << "\nWhat is the current second?\n";
    cin >> s;
    
    if (h > 24 || m > 60 || s > 60)
    {
          cout << "\nPlease try again!\n\n";
          goto mistake;
    }
    
    system("cls");
    
    while (a == 0)
    {
          cout << h << ":" << m << ":" << s << "\n\n\n\n\n\n\n\n\n\n\n\n\n";
          Sleep(1000);
          s++;
          if (s > 59)
          {
                s = 0;
                m++;
                
                if (m > 59)
                {
                      m = 0;
                      h++;
                      
                      if (h > 24)
                      {
                            h = 0;
                      }
                }
          }
    }
}
```
The only problem is that when I try to compile it i get an error that says Permission denied Id returned 1 exit status
I really do not know what this means or how to fix it. Any idea on what to do?

---

### Post by APNelson.L on 2006-11-07
> **APNelson.L said:**
> Okay so now my program looks like this:
```
//time
#include <iostream>
#include <windows.h>
#include <stdlib.h>

using namespace std;

int main()
{
    int a = 0;
    int h;
    int m;
    int s;
    
    mistake:
    
    cout << "What is the current hour?\n";
    cin >> h;
    
    cout << "\nWhat is the current minute?\n";
    cin >> m;
    
    cout << "\nWhat is the current second?\n";
    cin >> s;
    
    if (h > 24 || m > 60 || s > 60)
    {
          cout << "\nPlease try again!\n\n";
          goto mistake;
    }
    
    system("cls");
    
    while (a == 0)
    {
          cout << h << ":" << m << ":" << s << "\n\n\n\n\n\n\n\n\n\n\n\n\n";
          Sleep(1000);
          s++;
          if (s > 59)
          {
                s = 0;
                m++;
                
                if (m > 59)
                {
                      m = 0;
                      h++;
                      
                      if (h > 24)
                      {
                            h = 0;
                      }
                }
          }
    }
}
```
The only problem is that when I try to compile it i get an error that says Permission denied Id returned 1 exit status
I really do not know what this means or how to fix it. Any idea on what to do?

wow I found my problem. The program was still running when I tried to compile it ](*,)

---

### Post by Houman on 2006-11-07
hi there,

I am a bit confused, can you tell us what platform are you using and what compiler? I see you included windows.h but at the same time your error indicates you are using ld (the linker on unix/linux). 

regards

---

### Post by APNelson.L on 2006-11-07
I am running windows but using gcc as my compiler

---

### Post by themusicwave on 2006-11-07
I think you forgot your return 0; at the end of int main.  Sometimes this causes errors(won't compile, crashes) and is generally considered bad programming.

Any function that has a return type other than void needs to return a value when it finishes executing.

A return value of 0 from a main function indicates that the program terminated successfully.

---

### Post by po0f on 2006-11-07
APNelson.L,

Please change:
```
mistake:
    
    cout << "What is the current hour?\n";
    cin >> h;
    
    cout << "\nWhat is the current minute?\n";
    cin >> m;
    
    cout << "\nWhat is the current second?\n";
    cin >> s;
    
    if (h > 24 || m > 60 || s > 60)
    {
          cout << "\nPlease try again!\n\n";
          goto mistake;
    }
```

to this:
```
do {
    cout << "Enter hour: ";
    cin >> h;

    cout << "Enter minute: ";
    cin >> m;

    cout << "Enter second: ";
    cin >> s;
} while (h > 24 || m > 60 || s > 60);
```

---

### Post by shunthemask on 2006-11-09
FYI, I think that your c++ is a little out of date.  Header files haven't been used since the standardization in '98, but some compilers still support them.

---

