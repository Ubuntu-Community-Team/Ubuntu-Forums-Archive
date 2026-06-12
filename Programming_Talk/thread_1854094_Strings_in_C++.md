---
title: "Strings in C++"
date: 2011-10-03
forum: Programming Talk
---

### Post by DaimyoKirby on 2011-10-03
So I just installed Dev-C++ on Xubuntu 11.04.

I want to be able to use strings, but I've had problems getting them working before.
I copied the code for apstring.h and apstring.cpp from here, and created files for them, placing them in /Dev-Cpp/include.
I tried writing and running this code to quickly test if I got strings working:
```
//test.cpp
//Alden Davidson

#include <iostream.h>
#include "apstring.h"
#include <apstring.h>

int main()
{
    string Name;
    
    cout << "What is your name? ";
    getline(cin, Name);
    
    cout << Name << ", have a nice day.";
    
    system("pause");
    return 0;
}
```

I keep getting these errors though:
[IMG]http://i.imgur.com/5ItKul.jpg[/IMG]

This is odd, because I'm pretty sure I typed everything exactly how I learned in school, so I think it's just a problem with the libraries.

Can anyone tell me what I need to do to get strings working?
Do I need to download any libraries?

---

### Post by gardnan on 2011-10-03
I think you need to add either:
```
using namespace std;
```
or change cin to std::cin, cout to std::cout and string to std::string.

---

### Post by aura7 on 2011-10-03
// try this code this should work fine.

//test.cpp
//Alden Davidson

#include <iostream>
#include <string.h>

using namespace std;

int main()
{
    string Name;
    
    cout << "What is your name? ";
    getline(cin, Name);
    
    cout << Name << ", have a nice day.";
    
    return 0;
}

---

### Post by trent.josephsen on 2011-10-03
You are learning an old dialect of C++, one without namespaces.  That at least is evident from the #include lines (which shouldn't include a .h extension).  gardnan addressed that issue.

However, you're also working with apstring, with which I'm not familiar, but, from the name, is probably supplemental material for AP Computer Science.  I'll date myself by observing that AP CS hasn't used C++ since before I took it, and therefore you probably want to look for some more up to date material.  In any case, it's not a standard library, so you probably want to avoid it.  Use std::string instead.

tl;dr -- get a better book.  May I recommend [this one](http://www.amazon.com/gp/product/0201700735)?

---

### Post by DaimyoKirby on 2011-10-03
Well, it's just a basic highschool computer programming course, and an independent study (of sorts) to boot. So I just use the books they have.

But that's good to know. And would that be the reason I'm always getting:
```
32:2 C:\Dev-Cpp\include\c++\3.4.2\backward\backward_warning.h #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
```
every time I compile some code?

Also, I'll probably ask my teacher about it next class.

---

### Post by trent.josephsen on 2011-10-03
Yeah, that's the cause of the diagnostic.

If you're being provided the book... that's a different story.  But you should know the book you're using is dated, and I strongly recommend trying to find another one (even if you have to use the title provided to do your classwork).  Asking your teacher about it is probably a good idea.

---

### Post by DaimyoKirby on 2011-10-03
Ok. Thanks everyone for the help.

---

