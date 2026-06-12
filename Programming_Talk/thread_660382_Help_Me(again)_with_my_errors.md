---
title: "Help Me(again) with my errors"
date: 2008-01-06
forum: Programming Talk
---

### Post by kool_kat_os on 2008-01-06
I am experimenting with  C++ and I wrote this and i dont know how to fix it:

[PHP]#include <cstdlib>
#include <iostream>
#include <windows.h>

using namespace std;

int main()
{
    int name;
    cout << "Hi, Please enter your name: \n";
    cin >> name;
int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow);      
       MessageBox (NULL, "Hello" << name <<  , "Hello",MB_ICONEXCLAMATION);
       return 0;

}[/PHP]


When I try to compile it my compiler gives my errors like:
 
invalid operands of types `const char[6]' and `int' to binary `operator<<' 

expected primary-expression before ',' token 


This programs is supposed to Ask you for you name and a message box supposed to come up and say "Hello "You Name"

Can someone help me?
(please)

---

### Post by kool_kat_os on 2008-01-06
Anyone??? :confused:

---

### Post by Wybiral on 2008-01-06
What is this supposed to be:
```

MessageBox (NULL, [COLOR="Red"]"Hello" << name <<[/COLOR]  , "Hello",MB_ICONEXCLAMATION);

```?

---

### Post by kool_kat_os on 2008-01-06
A message box, thats were I want It to say "Hello Your name"

---

### Post by Majorix on 2008-01-06
You are using the Win32 API... I doubt many know how to use it here.

You would be far better of with QT as your GUI API.

---

### Post by Wybiral on 2008-01-06
Yes, I'm asking why you're using the "<<" operator there.

---

### Post by kool_kat_os on 2008-01-06
I dont know, thats what I use on console apps, (this is my first time using message boxes)

---

### Post by kool_kat_os on 2008-01-06
What  should I use?

---

### Post by Majorix on 2008-01-06
What you use is the Windows API and won't work under Linux.

You should try learning QT from here, at least read the Hello World example and for the rest keep a reference next to yourself. Anyways without further chat, here is the tutorial:
[http://doc.trolltech.com/4.3/tutorial.html](http://doc.trolltech.com/4.3/tutorial.html)

---

### Post by kool_kat_os on 2008-01-06
Im tring to use this for windo'z (unfortunalty)

---

### Post by Majorix on 2008-01-06
As far as I am concerned QT is cross-platform and works under Windows too.

The problem with the Windows API is that it is too complicated to even learn. For even a Hello World message box you have to write dozens of lines of code. With QT or similar the number of lines and the level of difficulty is greatly reduced.

Your call.

---

### Post by Wybiral on 2008-01-06
> **kool_kat_os said:**
> I dont know, thats what I use on console apps, (this is my first time using message boxes)

Then I suggest reading more about the language and not bothering with message boxes and such. If you can use the console, use it to learn about functions and classes (with operator overloading) so you can make some sense out of the code you just posted and try not to practice [voodoo]("http://en.wikipedia.org/wiki/Voodoo_programming").

---

### Post by kool_kat_os on 2008-01-06
Any recommendations for a compiler for "QT" that works on windows?? :)

---

### Post by Majorix on 2008-01-06
> **Wybiral said:**
> Then I suggest reading more about the language and not bothering with message boxes and such. If you can use the console, use it to learn about functions and classes (with operator overloading) so you can make some sense out of the code you just posted and try not to practice [voodoo]("http://en.wikipedia.org/wiki/Voodoo_programming").
I agree that the OP should practice more before programming GUI.
> **kool_kat_os said:**
> Any recommendations for a compiler for "QT" that works on windows?? :)
I don't know of any but I will look for you.

---

### Post by kool_kat_os on 2008-01-06
thanx

---

### Post by Majorix on 2008-01-06
QT's designer apparently works under Windows too.
[http://trolltech.com/downloads/index](http://trolltech.com/downloads/index)

QT has a dual licensing policy, which means you have to pay them if you develop commercial software. If you produce open-source software or do it for education, then you don't have to pay a buck.

Check for something called "QT Designer" inside the package you download. That's what you need. If you have Visual Studio then I have read that you can integrate the designer into it. Read on on their site if you wish.

---

### Post by chammy on 2008-01-07
I do some GUI junk on Win32 at work, and I've been using FLTK instead of Qt. It's a lot simpler and doesn't use any shared libraries. Qt is nice (all my crossplatform junk, including OSX stuff, uses Qt) but sometimes it's a little too much horsepower for what its worth.

A good IDE for Win32 would be [DevC++]("http://www.bloodshed.net/devcpp.html"), by Bloodshed. It has a "DevPak" that's a click-and-point install for FLTK, and it comes with a sample project you can base your programming off of.

---

