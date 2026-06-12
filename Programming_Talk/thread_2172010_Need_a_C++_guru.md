---
title: "Need a C++ guru"
date: 2013-09-02
forum: Programming Talk
---

### Post by nathan-b on 2013-09-02
Hi!

I'm writing a c++ program that uses sqlite and I need to get the data from a result column as a string, so I use this function:

```
const unsigned char *sqlite3_column_text(sqlite3_stmt*, int iCol);
```

The problem is I need to convert the const unsigned char* to a std::string or a QString (the gui is in Qt). I googled and lots of people seem to have the same issue but the most common suggestion is apparently just
```
reinterpret_cast<const char*>(sqlite3_column_text())
``` which seems kind of like one of those if-you-have-a-hammer-everything-seems-like-a-nail situations. I think the const unsigned char* is binary UTF-8 data, so casting it would work as long as everything was ascii but I'm writing a music player so I need to be able to store and retrieve strings like "Björk". Is something like libicu the solution here?

I'm thinking of just using the Qt SQL interface, but I don't want to get tied down to where all I know is Qt. I want to know how to use C++ with other libraries too. If all I use is one API for everything I might as well just use Java. :p

---

### Post by MG&amp;TL on 2013-09-03
I'm by no means a guru, but *const char ** is just data, it doesn't have to be ASCII-encoded. Here's a demo which returns an *unsigned const char **, casts it to a *const char **, and stores it in a *std::string*.

```
#include <string>
#include <iostream>

const unsigned char *foo()
{
    return (const unsigned char *)"Björk";
}

int main()
{
    std::string data((const char *)foo());
    std::cout << data << std::endl;
    return 0;
}

```

This outputs *Björk**, *as expected.

I imagine the C++ - style casts (*reinterpret_cast* and co) would work as well, but here I *wanted* raw pointer casts, so I used a C-style cast.

---

### Post by SledgeHammer_999 on 2013-09-03
Qt supports utf8. Just use [QString::fromUtf8()](https://qt-project.org/doc/qt-4.8/qstring.html#fromUtf8) (static method, can be used without a class instance). But it takes a signed const char*. I have no idea why sqlite returns unsigned here...

---

### Post by nathan-b on 2013-09-03
> **SledgeHammer_999 said:**
> Qt supports utf8. Just use [QString::fromUtf8()]("https://qt-project.org/doc/qt-4.8/qstring.html#fromUtf8") (static method, can be used without a class instance). But it takes a signed const char*. I have no idea why sqlite returns unsigned here...

Yeah, I thought using an unsigned type was weird too, that's why I didn't want to just cast it and continue on my way. I thought that if they had a reason to return an unsigned char, who was I to second guess their decision? :) But I decided just to cast it like MG&TL suggested. It works for now, if it starts mangling something I'll deal with it when it happens.

---

