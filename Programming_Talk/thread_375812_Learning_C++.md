---
title: "Learning C++"
date: 2007-03-04
forum: Programming Talk
---

### Post by mrmonday on 2007-03-04
Hi everyone,

I am interested in learning C++ and was wondering what program would be best to use. It needs to a good all round program, easy for beginners,but have lots of advanced features. It also preferably needs to be cross platform, so I can run it on Linux and windows. I would like to be able to develop programs for lots of operating systems (mainly windows and linux). Also does anyone know a good site for learning C++.

Thanks in advance for your help.

---

### Post by sriram on 2007-03-04
try searchin for books on c++ in torrents ..
i found a lot of them like about 200 books for c++.
use torrentz.com

---

### Post by rekahsoft on 2007-03-04
I assume you are talking about an IDE and compiler. On linux most use g++. If you want to compile an executable for windows you can use MinGW. If you want an environment that works in both linux and windows you can use Dev C++ ([http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)) which is bundled with MinGW so you will be set.

---

### Post by mrmonday on 2007-03-04
Hi,

Thanks for your help, however Dev C++ and MinGW both seem to be for windows, I can't find a linux version. According to my system g++ is installed, however I can't find it on my system:(

I still have no idea of how to get started, so any help would be appreciated. Thanks.

---

### Post by thumper on 2007-03-04
As far as books are concerned, I'd suggest "Accelerated C++" by Andrew Koenig and Barbara Moo.

For ubuntu, make sure you have the package "build-essential" installed.

Learn the command line for compilations.  It will help your understanding.

Then make a file like this:
```

#include <iostream>

int main()
{
   std::cout << "Hello world!\n";
}

```

Call it hello.cpp and compile and run it like this:

```

$ g++ hello.cpp -o hello
$ ./hello

```

---

### Post by studiesrule on 2007-03-04
There are a lot of C++ IDE's out there. It is debatable, but when your just starting out, it's better to just use gedit or Scintilla. The reason being is that you need to focus on learning the language rather than the tools. Some IDE's will do a bunch of stuff for you, and when you leave that IDE (or are stuck on an island with a terminal). 

After you've got some minor grip and are making very large programs, you may want to use Anjuta or KDevelop (if your KDE). Eclipse also is extremely good for this (and is cross-platform). Another cross-platform IDE is [Code::Blocks]("http://forums.codeblocks.org/index.php?PHPSESSID=de3bef4bbdfec2c6a24f08b5875b1488&board=20.0"). 
( you want to get one of the nightly builds)

As far as books go, any of those mentioned above are good, and you might want to look at ['How to be a Computer Scientist in C++"]("http://www.ibiblio.org/obp/thinkCS/"). It covers the OO concepts very well, and concentrates more on the comp. sci. part of it than the programming. After you've done your basic course, you want to keep [Bjarne Stroustrup's C++ Guide]("http://www.research.att.com/~bs/3rd.html") close to you always (you can get that from torrents as well). That is a reference of sorts and an advanced tutorial. Its helped me get out of tight spots, but its moderate to advanced stuff.

EDIT: 
It would do you some good to learn a 'make' system like SCons or how to use autotools later on, but only later on, when you are linking libraries and stuff. 

Best of Luck!

---

### Post by rekahsoft on 2007-03-04
oops..lol i read your ? wrong...you can just use any editor or IDE in either windows and linux and compile with g++ on linux and MinGW in windows ;) :D

---

### Post by iAlta on 2007-03-04
> **studiesrule said:**
> There are a lot of C++ IDE's out there. It is debatable, but when your just starting out, it's better to just use gedit or Scintilla. The reason being is that you need to focus on learning the language rather than the tools. Some IDE's will do a bunch of stuff for you, and when you leave that IDE (or are stuck on an island with a terminal). 

After you've got some minor grip and are making very large programs, you may want to use Anjuta or KDevelop (if your KDE). Eclipse also is extremely good for this (and is cross-platform). Another cross-platform IDE is [Code::Blocks]("http://forums.codeblocks.org/index.php?PHPSESSID=de3bef4bbdfec2c6a24f08b5875b1488&board=20.0"). 
( you want to get one of the nightly builds)

As far as books go, any of those mentioned above are good, and you might want to look at ['How to be a Computer Scientist in C++"]("http://www.ibiblio.org/obp/thinkCS/"). It covers the OO concepts very well, and concentrates more on the comp. sci. part of it than the programming. After you've done your basic course, you want to keep [Bjarne Stroustrup's C++ Guide]("http://www.research.att.com/~bs/3rd.html") close to you always (you can get that from torrents as well). That is a reference of sorts and an advanced tutorial. Its helped me get out of tight spots, but its moderate to advanced stuff.

EDIT: 
It would do you some good to learn a 'make' system like SCons or how to use autotools later on, but only later on, when you are linking libraries and stuff. 

Best of Luck!
thanks

---

### Post by mrmonday on 2007-03-06
> **studiesrule said:**
> 
As far as books go, any of those mentioned above are good, and you might want to look at ['How to be a Computer Scientist in C++"]("http://www.ibiblio.org/obp/thinkCS/"). It covers the OO concepts very well, and concentrates more on the comp. sci. part of it than the programming. After you've done your basic course, you want to keep [Bjarne Stroustrup's C++ Guide]("http://www.research.att.com/~bs/3rd.html") close to you always (you can get that from torrents as well). That is a reference of sorts and an advanced tutorial. Its helped me get out of tight spots, but its moderate to advanced stuff.


When I follow the first tutorial in 'How to be a Computer Scientist in C++' When I compile I get lots of errors about deprecated code. When I edit it to look like thumpers It works fine... Any ideas why?:confused:

Thanks.

---

### Post by WW on 2007-03-06
Are talking about the book where the first example is the following?
```

#include <iostream.h>

// main: generate some simple output

void main ()
{
  cout << "Hello, world." << endl;
} 

```
I found this here:
[http://www.ibiblio.org/obp/thinkCS/cpp/english/chap01.htm](http://www.ibiblio.org/obp/thinkCS/cpp/english/chap01.htm)

If this is a typical example of the code in this book, you should not use it.  It appears to be outdated.  Three problems jump out at me:
1. The first line, to follow current standards, should be
```
#include <iostream>
```

2. The code is going to use **cout** and **endl**, so either add this line before main()
```
using namespace std;
```
or change **cout** and **endl** to **std::cout** and **std::endl**, respectively.

3. **main()** must return an **int**, not **void**.

If you fix these problems, you obtain thumpers code (well, he also used "\n" inside his string instead of using endl).

---

### Post by MRCeltic on 2007-12-28
hmm... kinda old post and all but i think i need to learn some new tricks looks like things have changed since i took my C++ class all those years ago :(

---

