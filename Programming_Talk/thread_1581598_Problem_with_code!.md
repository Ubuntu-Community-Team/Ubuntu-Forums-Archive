---
title: "Problem with code!"
date: 2010-09-25
forum: Programming Talk
---

### Post by hariwonderful on 2010-09-25
I have started using Qt SDK for developing apps for c++. So i wrote a small program as a building block for my project. 
here it goes:

```



[COLOR=#000080]#include[/COLOR][COLOR=#008000]<iostream>[/COLOR] [COLOR=#000080]
#include[/COLOR][COLOR=#008000]<cstring>
[/COLOR]   [COLOR=#808000]using[/COLOR][COLOR=#808000] namespace[/COLOR] std[COLOR=#000000];[/COLOR]  
 [COLOR=#808000]struct [/COLOR]Address[COLOR=#008000]//[/COLOR][COLOR=#008000]structure[/COLOR][COLOR=#008000]for[/COLOR][COLOR=#008000]address[/COLOR]  [COLOR=#000000]
{[/COLOR]  [COLOR=#808000]int[/COLOR] hno[COLOR=#000000];[/COLOR]  
    [COLOR=#808000]char [/COLOR]city[COLOR=#000000][[/COLOR][COLOR=#000080]18[/COLOR][COLOR=#000000]],[/COLOR]locality[COLOR=#000000][[/COLOR][COLOR=#000080]20[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000];[/COLOR]  [COLOR=#808000]
    void[/COLOR] getadd[COLOR=#000000]()[/COLOR]  
    [COLOR=#000000]{[/COLOR]  cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"Enter[/COLOR][COLOR=#008000]house[/COLOR][COLOR=#008000]no:[/COLOR][COLOR=#008000]"[/COLOR][COLOR=#000000];[/COLOR]
        cin[COLOR=#000000]>>[/COLOR]hno[COLOR=#000000];[/COLOR]cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"\n"[/COLOR][COLOR=#000000];[/COLOR] 
        cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"Enter[/COLOR][COLOR=#008000]locality:[/COLOR][COLOR=#008000]"[/COLOR][COLOR=#000000];[/COLOR]  
        gets[COLOR=#000000]([/COLOR]locality[COLOR=#000000])[/COLOR][COLOR=#000000];[/COLOR]cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"\n"[/COLOR][COLOR=#000000];[/COLOR] 
         cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"Enter[/COLOR][COLOR=#008000]city:[/COLOR][COLOR=#008000]"[/COLOR][COLOR=#000000];[/COLOR]  
         gets[COLOR=#000000]([/COLOR]city[COLOR=#000000])[/COLOR][COLOR=#000000];[/COLOR]cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"\n"[/COLOR][COLOR=#000000];[/COLOR]
     [COLOR=#000000]}[/COLOR]  [COLOR=#000000]
};[/COLOR]   [COLOR=#808000]
class [/COLOR]Member  
[COLOR=#000000]{[/COLOR]   Addressadd[COLOR=#000000];
[/COLOR]     [COLOR=#808000]char[/COLOR] mname[COLOR=#000000][[/COLOR][COLOR=#000080]20[/COLOR][COLOR=#000000]],[/COLOR]sex[COLOR=#000000],[/COLOR]regno[COLOR=#000000][[/COLOR][COLOR=#000080]4[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000];[/COLOR] 
 [COLOR=#808000]    int[/COLOR] age[COLOR=#000000];
[/COLOR]   [COLOR=#808000]public[/COLOR][COLOR=#000000]:[/COLOR]  [COLOR=#808000]
        void[/COLOR] getdata[COLOR=#000000]()[/COLOR] 
         [COLOR=#000000]{[/COLOR] 
              cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"Enter[/COLOR][COLOR=#008000]Name:[/COLOR][COLOR=#008000]"[/COLOR][COLOR=#000000];[/COLOR]  
              gets[COLOR=#000000]([/COLOR]mname[COLOR=#000000])[/COLOR][COLOR=#000000];[/COLOR]cout[COLOR=#000000]<<[/COLOR]endl[COLOR=#000000];
            [/COLOR]  cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"Enter[/COLOR][COLOR=#008000]Age:[/COLOR][COLOR=#008000]"[/COLOR][COLOR=#000000];[/COLOR]  cin[COLOR=#000000]>>[/COLOR]age[COLOR=#000000];
[/COLOR]              cout[COLOR=#000000]<<[/COLOR]endl[COLOR=#000000];
[/COLOR]              cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"Enter[/COLOR][COLOR=#008000]Sex:[/COLOR][COLOR=#008000]"[/COLOR][COLOR=#000000];
            [/COLOR]  cin[COLOR=#000000]>>[/COLOR]sex[COLOR=#000000];[/COLOR]cout[COLOR=#000000]<<[/COLOR]endl[COLOR=#000000];
            [/COLOR]  cout[COLOR=#000000]<<[/COLOR][COLOR=#008000]"ADDRESS:[/COLOR][COLOR=#008000]"[/COLOR][COLOR=#000000]<<[/COLOR]endl[COLOR=#000000];
            [/COLOR]  add[COLOR=#000000].[/COLOR]getadd[COLOR=#000000]();[/COLOR]  
        [COLOR=#000000]}
[/COLOR]  [COLOR=#000000]};[/COLOR]   [COLOR=#808000]
int[/COLOR]main[COLOR=#000000]()[/COLOR] 
 [COLOR=#000000]{
[/COLOR]     MemberM[COLOR=#000000];[/COLOR]  
    M[COLOR=#000000].[/COLOR]getdata[COLOR=#000000]();[/COLOR]  
    cin[COLOR=#000000].[/COLOR]get[COLOR=#000000]()[/COLOR][COLOR=#000000];[/COLOR]
  [COLOR=#000000]}[/COLOR]  


```When i build it in Qt Creator 2.0, i get the following errors: :mad:

> 
[COLOR=#ff0000]..\LIBRARYMANAGEMENT\main.cpp: In member function 'void Address::getadd()': [/COLOR] [COLOR=#ff0000]..\LIBRARYMANAGEMENT\main.cpp:15: error: 'gets' was not declared in this scope [/COLOR]
  [COLOR=#ff0000]..\LIBRARYMANAGEMENT\main.cpp: In member function 'void Member::getdata()': [/COLOR]
  [COLOR=#ff0000]..\LIBRARYMANAGEMENT\main.cpp:33: error: 'gets' was not declared in this scope 
[/COLOR]
 [COLOR=#ff0000]
  [/COLOR]
 Also in build issues it shows: :sad:

> 
'gets' was not declared in this scope                  Line 15
'gets' was not declared in this scope                  Line 33
I don't understand why this is happening cos usually when i use gets in classes, the compiler does not go mad. Please help. :???:

---

### Post by James78 on 2010-09-25
Not related to your problem, but did you check where it says "intmain()"? Perhaps it should be "int main()". Also, main() says the return type is int, but you aren't returning successful with "return 0;"

As for gets, it's defined in cstdio, which you haven't included in your code. [Gets reference]("http://www.cplusplus.com/reference/clibrary/cstdio/gets/")

You should bookmark [this site]("http://www.cplusplus.com/reference/") for reference, as it's really useful.

---

### Post by philinux on 2010-09-25
Moved to Programming talk forum.

---

### Post by spjackson on 2010-09-25
> **hariwonderful said:**
> I don't understand why this is happening cos usually when i use gets in classes, the compiler does not go mad. Please help. :???:
In order to call gets() you need
```

#include <cstdio>

```However, it is very strongly recommended that you don't use gets(); it's a really good way to crash your program.

---

### Post by dwhitney67 on 2010-09-25
My $0.02...

Add the following header file:
```

...
#include <string>

```

Change the following:
```

...
//char city[18],locality[20];
std::string city;
std::string locality;
...
//char mname[20],sex,regno[4];
std::string mname;
std::string sex;
std::string regno;
...

```
And as others have mentioned, don't use gets(), whether you are programming in C++ or C.

For C++, use std::getline();  for example:
```

std::string text;

std::cout << "Input some text: ";
std::getline(std::cin, text);
...

```

---

### Post by hariwonderful on 2010-12-16
Thanks a lot..sorry i didnt watch the forum for soooo many months ....got caught up wid high school academics! Yea cstdio was the problem

---

### Post by Tony Flury on 2010-12-16
did you fix the issue with using gets too - you do get why "gets" is an issue - don't you ?

I will give you a clue - if your buffer is 20 characters, and you use gets - what happens if i type in 25 characters ?

[http://linux.die.net/man/3/gets](http://linux.die.net/man/3/gets)

---

