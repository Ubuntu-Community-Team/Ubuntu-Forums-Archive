---
title: "[SOLVED] Simple C++ Windows OOP"
date: 2008-10-25
forum: Programming Talk
---

### Post by rabbitman on 2008-10-25
I found _[this](http://msdn.microsoft.com/en-us/library/ms724950(VS.85).aspx)_ page at the msdn library. It shows you how to return the time on a Windows machine.

I wrote this C++ program that prints the Year, Month and Day of Week.

```


#include <windows.h>

#include <iostream>
using std::cout;
using std::endl;

int main()
{
    SYSTEMTIME st;

    GetSystemTime(&st);

    cout << st.wYear << endl;
    cout << st.wMonth << endl;
    cout << st.wDayOfWeek << endl;

}


```

The problem is I want to create a SystemTime Class but I don't know how. I found _[this](http://www.cplusplus.com/doc/tutorial/classes.html)_ tutorial on Classes and have tried most of the day to create my Class but I haven't been successful. Could someone help me create the Class?

---

### Post by jimi_hendrix on 2008-10-25
well you will want to start off with

```

class Example
{
     private: /*put variables/functions/anything else that you dont want/need to be acessed from outside the class under this access specifier*/
     int ex = 5;
    public: /*put anything that you need to access outside the class under this specifier*/

    void printex()
   {
       cout << ex << endl;
   }
    
};

```that should be right but might syntax errors :(

```

int main()
{
     Example examp;
     
     examp.printex();
}

```same goes for this one...may have syntax errors

---

### Post by rabbitman on 2008-10-25
Thank you jimi_hendrix I have tried to create a Class called SYSTEMTIME but when I try to compile my program I get the following error.

```
using typedef-name `SYSTEMTIME' after `class'
```

Perhaps I should try and call my Class something else but I don't know how to access the SYSTEMTIME Structure if I do that.

---

### Post by snova on 2008-10-25
You can't create a class called SYSTEMTIME because that name is already defined as something else. Try SystemTime instead.

---

### Post by rabbitman on 2008-10-25
Thank you snova, I renamed my Class to SystemTime & rewrote my program below. It compiled correctly and when run it gave the correct results, does the code look correct to you?

```


#include <windows.h>

#include <iostream>
using std::cout;
using std::endl;

class SystemTime
{
    public:
        int wYear;
        int wMonth;
        int wDayOfWeek;
};

int main()
{
    SYSTEMTIME st;

    cout << st.wYear << endl;
    cout << st.wMonth << endl;
    cout << st.wDayOfWeek << endl;

}


```

---

### Post by jimi_hendrix on 2008-10-25
you are not using your class though...to use the class try

```

SystemTime systime; //the identifier doesnt matter but im gong to call it this
cout << systime.wYear << endl;

```

but this would give you an error because there is no value in wYear yet

so create SYSTEMTIME st inside your class and give each a value like:

wYear = st.wYear;

then you can even make a function inside the class to print out the year, month, and day too and call it like

systime.print // where print is the name of the function

---

### Post by snova on 2008-10-25
Technically it wouldn't give you an error, but a good compiler would warn you about it.

[php]
class SystemTime
{
    public:
        SystemTime()
        {
            Update();
        }

        void Update()
        {
            SYSTEMTIME st;
            GetSystemTime( &st );

            wYear = st.wYear;
            wMonth = st.wMonth;
            wDayOfWeek = st.wDayOfWeek;
        }

        int wYear;
        int wMonth;
        int wDayOfWeek;
};
[/php]

---

### Post by rabbitman on 2008-10-25
Your Class looks good snova but when I compile it (using Code::Blocks) I get the following error messages. I even turned off **-Wall -W**.

```

systimeclass.cpp: In member function `void SystemTime::Update()':
systimeclass.cpp:12: error: `SYSTEMTIME' was not declared in this scope
systimeclass.cpp:12: error: expected `;' before "st"
systimeclass.cpp:13: error: `st' was not declared in this scope
systimeclass.cpp:13: error: `GetSystemTime' was not declared in this scope

```

I'm really confused because I thought that would have worked. :(

---

### Post by jimi_hendrix on 2008-10-25
do you have all the headers in?

snova did not put any headers in his snippit but you will need the ones that you normally use

---

### Post by rabbitman on 2008-10-25
Thank you both very much, you have been very helpful.

I added the necessary headers like you said jimi and the example that snova posted worked perfectly.

---

