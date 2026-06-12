---
title: "makefiles?"
date: 2008-08-19
forum: Programming Talk
---

### Post by StOoZ on 2008-08-19
ok , finally I completed my app , and I want to distribute it , opened source , with a makefile (?) , how do I do that?
I used several libs in my development , such as taglib , wxwidgets , boost etc.

is there a good walk-through guide of how to do it?
btw , im using netbeans , and I can see a "MakeFile" in my project's tree , but it seems quite empty.

---

### Post by cmay on 2008-08-19
[http://hsrl.rutgers.edu/ug/make_help.html](http://hsrl.rutgers.edu/ug/make_help.html)
hope it helps.

---

### Post by theyranos on 2008-08-19
[http://www.gnu.org/software/make/manual/](http://www.gnu.org/software/make/manual/) is fairly well-written. They have a tutorial-esque introduction to the makefile syntax [here](http://www.gnu.org/software/make/manual/html_node/Introduction.html#Introduction)

**Edit: ** cmay: Thank you for the latest addition to my List o' Quick Reference Bookmarks :)

---

### Post by StOoZ on 2008-08-19
does my appllication must also have a ./configure file?
usually when I download a source app , I compile it this way: 
./configure
make
sudo make install


where the ./configure came from?

---

### Post by theyranos on 2008-08-19
./configure files are usually a script that generates your makefile based on what libraries are available on the machine doing the compiling. Usually, when you have to ./configure a program, it means it was prepared with autoconf and automake.

If you're coding in java, then a ./configure is probably not necessary. 
If that's the case, for people who are used to the standard ./configure && make && sudo make install thing, you can include a configure file that just looks like this:
```

#!/bin/sh
echo "Configure not necssary for this program :)"

```

---

### Post by spongedaddy on 2008-08-19
Many thanks to cmay and theraynos for the links and to StOoZ too for posting the question. I've been wanting to ask the same question myself, but have just been too lazy ;)

---

### Post by StOoZ on 2008-08-19
well im not using java , but C++.
this part , of distributing the app , is more tedious than writing and creating it :(

---

### Post by theyranos on 2008-08-19
C++ apps typically do use autoconf+automake to generate the configure and make files. And as of right now, you've exhausted my knowledge of the subject.

[quote=StOoz]
this part , of distributing the app , is more tedious than writing and creating it
[/quote]
Yep. If anyone can post a link to an autoconf+automake tutorial that isn't insanely complicated or woefully incomplete, they'll have my eternal gratitude.

---

### Post by StOoZ on 2008-08-19
ok , so few steps backwards :)
basically , a C++ app, if I understand it correctly , doesnt have to use a ./configure file , if the make file is properly written?

---

### Post by WW on 2008-08-19
> **StOoZ said:**
> ok , so few steps backwards :)
basically , a C++ app, if I understand it correctly , doesnt have to use a ./configure file , if the make file is properly written?
Aye, there's the rub.  It is hard to create a "properly written" makefile that will work in all the computer systems people might use to run your program (Mac, umpteen Linux flavors, Windows, Solaris, etc).  This is one of the reasons for the autoconf tools.

---

### Post by hod139 on 2008-08-19
I would suggest you use [cmake]("http://www.cmake.org/") instead of the gnu auto-tools.  cmake is much easier to use, and it is cross platform (auto-tools only works on linux).

---

### Post by StOoZ on 2008-08-19
:(
seeing the autoconf && automake docs (official ones...) its like learning a new language , while the only thing I want , is a simple way to deploy my app :(

---

### Post by theyranos on 2008-08-19
[This Linuxjournal article](http://www.linuxjournal.com/article/6700) makes cmake look pretty simple to use. Certainly a lot simpler than any documentation I've ever seen for autotools.

/me thanks hod139

---

### Post by dwhitney67 on 2008-08-19
> **StOoZ said:**
> :(
seeing the autoconf && automake docs (official ones...) its like learning a new language , while the only thing I want , is a simple way to deploy my app :(
The simplest way is to deploy the binaries, not the source code.  Consider creating a Debian package, an RPM, and whatever those Windoze folks want.

---

### Post by StOoZ on 2008-08-19
can you please provide more details about that?

sounds interesting.

---

### Post by bruce89 on 2008-08-19
> **hod139 said:**
> and it is cross platform (auto-tools only works on linux).

No they don't. That was one of the reasons for their development.

> **dwhitney67 said:**
> The simplest way is to deploy the binaries, not the source code.

Then it wouldn't be FOSS.

Anyway, a wee Makefile would be fairly simple (assuming all the libraries you are using have a pkg-config file). Something along these lines:
```

CXX = g++
CXXFLAGS = `pkg-config --cflags --libs "list of lib names"`

all: program

program: program.cpp
	$(CXX) $(CXXFLAGS) -o program program.cpp

clean:
	rm -f program

```

---

### Post by hod139 on 2008-08-19
> **bruce89 said:**
> No they don't. That was one of the reasons for their development.

Autoconf requires a unix-like system.  This means a windows user must install a GNU bash shell (e.g. cygwin).  This is not what I consider cross platform.

CMake on the other had installs natively on the host OS, and will produce native build tools for the respective OS.  On linux like systems, cmake will produce makefiles.  On windows, it will generate visual studio solution files (or if you want, it will make mingw makefiles).  This, imo, is a true cross platform solution.

---

### Post by bruce89 on 2008-08-19
> **hod139 said:**
> Autoconf requires a unix-like system.  This means a windows user must install a GNU bash shell (e.g. cygwin).  This is not what I consider cross platform.

I suppose that Autotools are cross-UNIX then.

---

### Post by cabalas on 2008-08-19
> **theyranos said:**
> Yep. If anyone can post a link to an autoconf+automake tutorial that isn't insanely complicated or woefully incomplete, they'll have my eternal gratitude.

When I learnt how to use autotools I found that this tutorial was a lot of help, it's short and easy to understand.

[http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/](http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/)

It might be a little out of date on a few minor things but nothing that you shouldn't be able to easily figure out.

---

### Post by scourge on 2008-08-20
> **StOoZ said:**
> I used several libs in my development , such as taglib , wxwidgets , boost etc.

May I ask what you used boost for? Because if it was for cross-platform threads, networking, containers, etc. you could've done it all with wxWidgets.

The preferred way to build wxWidgets apps is a Bakefile: [http://www.bakefile.org/index.html](http://www.bakefile.org/index.html)
It works on all supported platforms and creates a native makefile, just like Qmake (for Qt apps).

---

### Post by dribeas on 2008-08-20
> **scourge said:**
> May I ask what you used boost for? Because if it was for cross-platform threads, networking, containers, etc. you could've done it all with wxWidgets.

I don't know others, but I am currently using boost::signals, boost::bind, boost::random and in a couple other places boost::datetime, boost::function...

From those, bind and lambda::bind are really powerful tools; signals decouple caller from callee in function/method calls with little overhead and development time. It can help to setup unit testing, and dynamically changing classes without needing a inheritance relationship... you can even have multiple callees for one call (think of plugging a debug log at any time in any call, different operations with just a trigger/event...)

---

### Post by scourge on 2008-08-20
> **dribeas said:**
> I don't know others, but I am currently using boost::signals, boost::bind, boost::random and in a couple other places boost::datetime, boost::function...

From those, bind and lambda::bind are really powerful tools; signals decouple caller from callee in function/method calls with little overhead and development time. It can help to setup unit testing, and dynamically changing classes without needing a inheritance relationship... you can even have multiple callees for one call (think of plugging a debug log at any time in any call, different operations with just a trigger/event...)

Of course there can be situations where wxWidgets is not enough, and something like Boost is needed. But there's also a lot of overlapping between the two libraries, so it may be best to just stick to wxWidgets if possible. That's why I asked what the OP was doing with Boost.

---

### Post by StOoZ on 2008-08-20
> **scourge said:**
> May I ask what you used boost for? Because if it was for cross-platform threads, networking, containers, etc. you could've done it all with wxWidgets.

The preferred way to build wxWidgets apps is a Bakefile: [http://www.bakefile.org/index.html](http://www.bakefile.org/index.html)
It works on all supported platforms and creates a native makefile, just like Qmake (for Qt apps).

I use the math parts of it.
and this bakefiles , can be a replacement for autoconf & automake etc?

I've started reading about CMake... not too much up to now.

---

### Post by theyranos on 2008-08-20
[quote=http://www.bakefile.org/index.html]generates native makefile (autoconf's Makefile.in, Visual C++ project, bcc makefile etc.). [/quote]

Seems like it generates autoconf/automake input files on UNIX-like systems.

Oh, and thank you cabalas. That was much clearer than anything I've seen before on the subject.

---

### Post by hod139 on 2008-08-20
> **dwhitney67 said:**
> The simplest way is to deploy the binaries, not the source code.  Consider creating a Debian package, an RPM, and whatever those Windoze folks want.
CMake can also generate packages for you.  CPack (the name of the packager) can generate the following packages:
 DEB    Debian packages
 NSIS   Null Soft Installer
 RPM    RPM packages
 STGZ   Self extracting Tar GZip compression
 TBZ2   Tar BZip2 compression
 TGZ    Tar GZip compression
 TZ     Tar Compress compression
 ZIP    ZIP file format

---

