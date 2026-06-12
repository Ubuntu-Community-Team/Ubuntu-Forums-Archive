---
title: "C++ GetOpt class?"
date: 2009-02-11
forum: Programming Talk
---

### Post by patryk77 on 2009-02-11
[quote=GNU C++ library]The GetOpt class provides an efficient and structured mechanism for processing command-line options from an application program.[/quote]

I found this **[COLOR="Blue"][online](http://www.chemie.fu-berlin.de/chemnet/use/info/libgpp/libgpp_39.html)[/COLOR]**.

Upon trying to use it in a program, I get an error saying the 'GetOpt.h' file does not exist, and I can't **locate** it either.

I have a 'getopt.h' file, in the C library.

Should I take it the GetOpt is deprecated and I cannot use it?

> User's Guide
to the GNU C++ Library
last updated April 29, 1992
for version 2.0

---

### Post by monkeyking on 2009-02-11
I don't think getopt is even close to beeing deprecated.

I've used it recently, but I didn't include it directly,
I think I used stdlib.h,unistd.h or just stdio.h

---

### Post by patryk77 on 2009-02-11
I mean the C++ GetOpt class, not the standard C getopt() function.

Referenced here:
[http://www.chemie.fu-berlin.de/chemnet/use/info/libgpp/libgpp_39.html](http://www.chemie.fu-berlin.de/chemnet/use/info/libgpp/libgpp_39.html)

In case you missed the previous link.

---

### Post by lensman3 on 2009-02-11
The getopt() is a C function. Do a "man 3 getopt", that will tell you which include you need.

Look like the GetOpt class is trying to make a perfectly adequate C library in to a C++ library.  By the looks of it, it is just a wrapper around the C function.

Using the Boost "boost::lexical_cast<int> optarg;" is a much better option (where <int> can be anything C++.

---

### Post by geirha on 2009-02-12
Searching for getopt in the repositories, I see there is a package called libgetopt++-dev which installs getopt++/GetOption.h: [http://packages.ubuntu.com/intrepid/i386/libgetopt++-dev/filelist](http://packages.ubuntu.com/intrepid/i386/libgetopt++-dev/filelist)

Might be a decendant of that getopt-lib your guide is talking about...

---

### Post by patryk77 on 2009-02-12
Ok, will go the C route.

Thanks for the replies.


Found this in the GCC libstdc++ FAQ:
> 1.6.
	

What happened to the older libg++? I need that!
	

The most recent libg++ README states that libg++ is no longer being actively maintained. It should not be used for new projects, and is only being kicked along to support older code. 

The GetOpt class was part of libg++, and while I think it's a shame that it's no longer implemented, I understand that they are simply trying to make the best lib following the stnadards.

Cheers!

---

