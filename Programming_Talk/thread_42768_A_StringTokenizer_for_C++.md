---
title: "A StringTokenizer for C++"
date: 2005-06-19
forum: Programming Talk
---

### Post by josuealcalde on 2005-06-19
Do someone know about a StringTokenizer in g++ libraries?
Now, I am using a code found in gcc.gnu.org but I would like to know if is there a way to do it with default libraries.

---

### Post by WakkiTabakki on 2005-06-19
How about char* strtok(char*, char* ) found in string.h?

[http://www.cplusplus.com/ref/cstring/strtok.html](http://www.cplusplus.com/ref/cstring/strtok.html)

It's part of the ANSI standard C libraries...
/N

---

### Post by jerome bettis on 2005-06-19
what exactly are you trying to do?

---

### Post by LordHunter317 on 2005-06-19
No, **never, ever, ever, ever** use strtok().  It's crap, and it shouldn't be used in new applications ever.  Period.   

And C isn't C++.  While the standard functions are available, they should generally be avoided unless you're working with existing C applications.

Look at the boost::tokenizer library part of the freely available C++ libraries part of boost.org.  It ought to be available via the universe repository.   This ought to be able to do what you want, and it's infinetely better than strtok().  Also, boost::tokenizer is templated, so it doesn't increase your run-time dependencies.

---

### Post by jerome bettis on 2005-06-19
[QUOTE=LordHunter317]No, **never, ever, ever, ever** use strtok().  It's crap, and it shouldn't be used in new applications ever.  Period.   [/quote]

agreed.

> And C isn't C++.  While the standard functions are available, they should generally be avoided unless you're working with existing C applications.

i usually go with the C++ way of doing stuff, but sometimes the C way does have it's place.

> Look at the boost::tokenizer library part of the freely available C++ libraries part of boost.org.  It ought to be available via the universe repository.   This ought to be able to do what you want, and it's infinetely better than strtok().  Also, boost::tokenizer is templated, so it doesn't increase your run-time dependencies.

yeah i use the boost libraries every chance i get.  hopefully they will find their way into the standard soon.  enable the universe and apt-get install libboost-dev.  then #include "boost/whateveryoureusing.hpp"

---

### Post by thumper on 2005-06-20
[QUOTE=LordHunter317]No, **never, ever, ever, ever** use strtok().  It's crap, and it shouldn't be used in new applications ever.  Period.   

And C isn't C++.  While the standard functions are available, they should generally be avoided unless you're working with existing C applications.[/QUOTE]
Even then you don't always want to use it.  One of the primary reasons that it is now generally avoided is that strtok uses global variables to remember state.  This means that you cannot safely call it from two different threads, or even have another call to strtok inside a loop where an outer loop is also calling strtok as the global state gets in a mess.

[QUOTE=LordHunter317]Look at the boost::tokenizer library part of the freely available C++ libraries part of boost.org.  It ought to be available via the universe repository.   This ought to be able to do what you want, and it's infinetely better than strtok().  Also, boost::tokenizer is templated, so it doesn't increase your run-time dependencies.[/QUOTE]
Another vote for the boost libraries.  I agree with LordHunter317 entirely on this point.  The boost libraries are well worth understanding and contain many good peer reviewed, free libraries.

---

### Post by josuealcalde on 2005-06-20
Thanks. I know about strtok, but it is c, and I don't like it.

I have a function to do it but I would want a library like the one you have said, but it is in universe, and you can say it is default. I should used it statically.

I will use the function find in gcc.gnu.org (a string c++ function). It will be the easiest.

What I am doing is a Deb Viewer (and then, a deb installer) and I need a string tokenizer to parse a lot of things.

---

### Post by thumper on 2005-06-20
[QUOTE=josuealcalde]Thanks. I know about strtok, but it is c, and I don't like it.

I have a function to do it but I would want a library like the one you have said, but it is in universe, and you can say it is default. I should used it statically.

I will use the function find in gcc.gnu.org (a string c++ function). It will be the easiest.

What I am doing is a Deb Viewer (and then, a deb installer) and I need a string tokenizer to parse a lot of things.[/QUOTE]
Seriously, take a look at boost.

I wouldn't necessarily grab the one from universe as it is a little out of date.

Go to the website ([http://www.boost.org](http://www.boost.org)), and build it from source.  Most of what you need is all template based anyway.

Go on, look at it.

---

### Post by LordHunter317 on 2005-06-20
[QUOTE=thumper]Even then you don't always want to use it.  One of the primary reasons that it is now generally avoided is that strtok uses global variables to remember state.  This means that you cannot safely call it from two different threads, or even have another call to strtok inside a loop where an outer loop is also calling strtok as the global state gets in a mess.[/quote]This is true of large portions of the standard C library, and of the POSIX standard itself.

C code written in that era practiced a philosophy of "functions shouldn't have side-effects".  This meant that functions that really needed to allocate storage on a per-call basis didn't do so.  The result being that they're not thread or signal safe.

Some functions have a reentrant-safe version called function_r that you can use.  Only they're not portable at all.

[quote=josuealcalde]I have a function to do it but I would want a library like the one you have said, but it is in universe, and you can say it is default. I should used it statically.[/quote]Most of boost (including boost::tokenizer) is templated.  This means that you don't increase your run time dependencies at all: the code **must** be compiled explictly for your data-types and application and is included in your code.

You can use it just fine even though the development library is in universe.  You'll notice there are no runtime files (or even static library files) unless you're looking at boost::threads, boost::python, or some other small bits.

> I will use the function find in gcc.gnu.org (a string c++ function). It will be the easiest.The functions provided by the STL will not be sufficent for your needs.

And why are you writing this anyway?  Debian packages are three tarballs in an ar(1) archive.  And, there's dpkg-deb to read all the information contained in them anyway.  What are you trying to achieve?

---

### Post by josuealcalde on 2005-06-20
It is a GUI, of course. Similar to Gdeb but redesigned showing more information in the same way that synaptic does (package properties dialog).

The idea is to use synaptic in non-interactive mode (like update-manager does) to check, solve and install the dependencies, and when they are solved, to install the deb local file(s) using dpkg -i,

---

### Post by LordHunter317 on 2005-06-20
[QUOTE=josuealcalde]The idea is to use synaptic in non-interactive mode (like update-manager does) to check, solve and install the dependencies, and when they are solved, to install the deb local file(s) using dpkg -i,[/QUOTE]You won't be able to use just dpkg(8).  You generally at the very least have to feed the installed package chocies through apt-get(8) or be prepared to handle dependency resolution and all install cases manually,  dpkg(8) on it's own can't install every possible legal situation.

---

### Post by josuealcalde on 2005-06-20
[QUOTE=LordHunter317]You won't be able to use just dpkg(8).  You generally at the very least have to feed the installed package chocies through apt-get(8) or be prepared to handle dependency resolution and all install cases manually,  dpkg(8) on it's own can't install every possible legal situation.[/QUOTE]

I know. I want to use synaptic gui as much as posible, but perhaps, it will be necessary to do some manual job.

Any way, now it is only a project and the first thing is to do a gdeb like tool, without dependency resolution as a way for viewing deb information and to make dpkg -i in a graphic way.

---

### Post by calvin.johns on 2005-06-29
[QUOTE=LordHunter317]No, **never, ever, ever, ever** use strtok().  It's crap, and it shouldn't be used in new applications ever.  Period.   

And C isn't C++.  While the standard functions are available, they should generally be avoided unless you're working with existing C applications.

Look at the boost::tokenizer library part of the freely available C++ libraries part of boost.org.  It ought to be available via the universe repository.   This ought to be able to do what you want, and it's infinetely better than strtok().  Also, boost::tokenizer is templated, so it doesn't increase your run-time dependencies.[/QUOTE]
 How do you install the boost libraries without having to do a build?

Is there a package?

---

### Post by LordHunter317 on 2005-06-29
Yeah, libboost-dev gives the core stuff.  There are several subpackages though.

Here's the Debian Sid notes:
[http://packages.debian.org/unstable/libdevel/libboost-dev](http://packages.debian.org/unstable/libdevel/libboost-dev)

---

