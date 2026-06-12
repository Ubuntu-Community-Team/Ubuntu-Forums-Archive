---
title: "C++ no member function declared in class"
date: 2012-01-19
forum: Programming Talk
---

### Post by sony_gamer on 2012-01-19
I am working in Code::Blocks on a C++ program and trying to keep my functions organized in seperate class and header files.
Could someone let me know what I'm doing wrong.
I get this message when I try to test/compile:
~/Programs/Disc Master/media.cpp|14|error: no ‘void media::disctype()’ member function declared in class ‘media’|
the same error occurs for ripmusic and dvdmanip

Currently the compiler for the project is on GCC, I checked to see if G++ is installed and it is, but it's not selectable in Code::Blocks.

As you can see it's pretty simple code just setting up functions.

cpp

```
#include "media.h"

//using namespace std;
media::media()
{
    //ctor
}

media::~media()
{
    //dtor
}

void media::disctype()
{
    do
        detectdisc= system(cdde -b)
    while detectdisc != ""

    if (detectdisc == "An audio cd was inserted.")
    {
        ripmusic();
    }
    else if (detectdisc == "A dvd was inserted.")
    {
        dvdmanip();
    }
}

void media::ripmusic()
{
    musicrip.hidden=false
}

void media::dvdmanip()
{
    //musicrip.hidden=false
}

```

header

```
#ifndef MUSIC_H
#define MUSIC_H
using namespace std;

class media
{
    public:
        media();
        virtual ~media();

    protected:
        string detectdisc;
    private:

};

class disctype: public media
{
    public:
        disctype();
};

class ripmusic: public media
{
    public:
        ripmusic();
};

class dvdmanip: public media
{
    public:
        dvdmanip();
};

#endif // MUSIC_H
```

---

### Post by cgroza on 2012-01-19
Disctype is a class.
Maybe you mean:

```

disctype::disctype() {...}

```And a constructor cannot have a return type, in this case void.

---

### Post by Hetepeperfan on 2012-01-19
If i'm not mistaken you are trying to define member functions which according to the class do not exist.
therfore you have to change the class header in order to accomodate the funtions.

```
class media
{
    public:
        media();
        virtual ~media();
        void disctype(void);
        void ripmusic(void);
        void dvdmanip(void);

    protected:
        std::string detectdisc;
    private:

};
```

But there are more problems ahead. Like u should probably not make namespace std available in a header. The standard template library is put into a namespace for a reason. Now every file that includes your media header has the STL available, i think this is bad coding style you also forgot to include #include <string>.

well the adaptation of the class should fix the error you created by defining the funtions in the .cpp file but did not declare in the class declaration , but there is more ahead.

cheers,

Maarten

---

### Post by sony_gamer on 2012-01-19
Unfortunately when I change 'void media::*()' to *::*()' (sub * for disctype, ripmusic, and dvdmanip) I get errors saying cdde and b are not declared in the scope, I added some ;'s and brackets where I was missing them so the error count dropped.

Pre-post edit:

The issue with the cdde and b was they weren't inside quotes.  Trying to learn c++ coming from a vb(6,2008,.NET) background so used to autocomplete taking care of the little nuances like these.

---

### Post by dwhitney67 on 2012-01-20
> **sony_gamer said:**
> ... so used to autocomplete taking care of the little nuances like these.
Yes, I hear this all the time.  It's the editor's (or IDE's) fault, not the programmer's.

I agree with what Hetepeperfan stated concerning the (mis)use of "using namespace" declarations within header files; they should be avoided.

Also, you might want to consider changing your class names to begin with an uppercase letter, so as not to confuse a class name with a method (function) name.  When all objects, functions, and variables (whether local or class-scoped) have the same style of lettering, it is difficult to discern one from the other in an efficient manner.

---

