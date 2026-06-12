---
title: "Undefined reference to my function.(C++,codeblocks)."
date: 2009-10-07
forum: Programming Talk
---

### Post by myromance123 on 2009-10-07
hi there.

 This error pops up during build:
```
undefined referene to `Pen::write_on_paper(std::basic_string<char, std::char_...
```

Here's my main.cpp:
```
#include <iostream>
#include "Pen"

using namespace std;

int main()
{
    Pen AwesomePen;
    Pen TerriblePen;

    AwesomePen.InkColor = black;
    AwesomePen.Style = felt_tip;
    AwesomePen.Brand = "Faber Castke";
    AwesomePen.Length = 4.0;
    AwesomePen.InkLevelPercent = 100;

    AwesomePen.write_on_paper("Here is the pen I think is Awesome");
    cout << AwesomePen.Brand << endl;
    cout << AwesomePen.Length << endl;
    cout << AwesomePen.InkColor << endl;
    cout << AwesomePen.Style << endl;


    return 0;
}
```

Here's my func.cpp:
```
#include <iostream>
#include "Pen"

using namespace std;

void Pen::write_on_paper(string words)
{
    if (InkLevelPercent <= 0 )
    {
        cout << "Oops! Out of Ink!" <, endl;
    }
    else
    {
        cout << words << endl;
        InkLevelPercent = InkLevelPercent - words.length();
    }
};

void Pen::break_in_half()
{
    InkLevelPercent = InkLevelPercent / 2;
    Length = Length / 2.0;
};

void Pen::run_out_of_ink()
{
    InkLevelPercent = 0;
};
```

here's my class Pen.h:
```
#ifndef PEN_INCLUDED
#define PEN_INCLUDED

using namespace std;

enum Color
{
    blue,
    red,
    black,
    clear
};

enum PenStyle
{
    ballpoint,
    felt_tip,
    fountain_pen
};

class Pen
{
public:
    Color InkColor;
    Color ShellColor;
    Color CapColor;
    PenStyle Style;
    float Length;
    string Brand;
    int InkLevelPercent;

    void write_on_paper(string words);
    void break_in_half();
    void run_out_of_ink();
};

#endif // PEN_INCLUDED

```

 Please note that CodeBlocks will not accept if I type #include "Pen.h" instead of #include "Pen", although in Vista its the other way around..

What am I missing?
 I reread it several times but well I'm not sure of the solution.
The error points to the function being called in main.cpp.
 i'm guessing it cant find write_on_paper(string words)..

---

### Post by dwhitney67 on 2009-10-07
The include statement should be:
```

#include "Pen.h"

```
If CodeBlocks disagrees, then you should consider using another IDE.

You should consider renaming func.cpp to be Pen.cpp.  That is the normal convention used by C++ developers.

You may need to tell CodeBlocks where to locate header files, if you are still unable to find Pen.h.

CodeBlocks also needs to compile main.cpp and Pen.cpp, and link them together.

If you would use the command line, you would probably be done with your issue "yesterday".

P.S.  Pen.h is missing an include for <string>.  Never use a "using namespace" directive in a header file; specify the namespace (ie. std::string).  Also, consider declaring the function to accept a const reference to a string.

---

### Post by TheStatsMan on 2009-10-07
There is a mistake here, other than that it works for me in codeblocks (using Pen.h). Should be << instead of <,
```

if (InkLevelPercent <= 0 )
{
    cout << "Oops! Out of Ink!" <, endl;
}

```

---

### Post by myromance123 on 2009-10-07
I find that I can't name the .cpp and .h the same name or CodeBlocks will just overwrite the other one.
 Maybe I'm saving the .h file in the wrong folder.
TheStatsMan, may I ask, where did you save your .h file? Directly in the folder of your project or elsewhere?

Also, for the header file did you tick Debug and Release?


EDIT:
 Sorry didn't have enough time to properly reply.
The thing is I'm learning from a book called C++ All-In-One for Dummies and this is getting frustrating. This isn't the first book where things just dont work out like their supposed to when I use Ubuntu (the first was on C and using even the terminal, i found the C standard on Ubuntu is different..meaning certain keywords don't work).
 Of course the Terminal would have no problem here but I'm practicing to use IDEs to increase speed and hopefully efficiency in my programming skills, not so much to memorize the various tags/arguments to pass to the compiler when I want to compile my source code..so yeah, I know many won't agree with this but thats the way I'd like to go :)

---

### Post by TheStatsMan on 2009-10-07
They are all in the same folder. I just added a new empty file for each file after I created a project. I saved the files as main.cpp ,pen.h and pen.cpp. Naturally in my case in included "pen.h", but the case is not important as long as you are consistent. Make sure it is in your case as this could cause a linking error. 

I agree with dwhitney67, by the way it is worthwhile going to the command line (with a Makefile) at some stage and taking up vim (make sure you read a guide to start with though and then look into some plugins). It is much more efficient. Still code::blocks should work. I used to use it for my projects when I first came from Windows and I never had a problem with it and I can certainly compile and run your code.

Edit:
Following your edit, it won't be clear why the command line (with a Makefile or equivalent) and a text editor like vim is much more efficient until you start using it, but the majority of linux programmers to take this approach for good reason, it is not as if there isn't ample choice.

---

### Post by myromance123 on 2009-10-07
OMG!

 Nut CRACKERS!!

 So much for calling CodeBlocks an IDE!!

When I added those C++ source file and Header file, guess what?!
 CodeBlocks doesn't know to save them with a .cpp and .h extension!!

 My goodness...

After saving it as .cpp and as .h(actually naming it func.cpp and Pen.h) for the C++ source and header file respectively it all works.

I thought something was wrong when I typed in those files but keywords weren't colored, just grey...

you wanna know what's weird?
 When I don't use classes, but make my functions in a separate source file before this, even without the .cpp extension the compiler could handle it....
 CodeBlocks shouldn't let the user do whats not allowed!
All well that ends well, Thanks guys :)

---

### Post by forrestcupp on 2009-10-07
> **myromance123 said:**
> 
you wanna know what's weird?
 When I don't use classes, but make my functions in a separate source file before this, even without the .cpp extension the compiler could handle it....
 CodeBlocks shouldn't let the user do whats not allowed!
All well that ends well, Thanks guys :)

That's because every file is considered a source file.  Even header files are really source files, we just call and name them header files for our own benefits.  You could technically do all your declarations in your source .cpp file if you wanted to.  To an IDE, they're all the same unless you make them different.

It's unfortunate that it can't automatically save files with the proper extensions, though.

---

