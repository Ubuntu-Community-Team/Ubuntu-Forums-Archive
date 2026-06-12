---
title: "offline reference manual for g++?"
date: 2006-01-25
forum: Programming Talk
---

### Post by glinsvad on 2006-01-25
I used to code with Borland C++ Builder (3 back in 98' :D), which came with an extensive and phenomenal reference manual for all functions/headers/libraries etc. 

Now I'm using g++ in Linux Ubuntu, which works fine for me so far. I know there are excellent online documentations (e.g. [http://man-wiki.net/]("http://man-wiki.net/")) , but I don't always have internet access so I need an offline doc as well.

Anything you can recommend? I guess the best thing would be a Help-file, like the one that comes with Ubuntu...

EDIT: Added a poll to find out what you use.

---

### Post by Viro on 2006-01-25
apropos and man are all you need ;).

---

### Post by glinsvad on 2006-01-25
Well don't I feel silly... the manual has its own manual :p
```
man man
```

> apropos and man are all you need
To the best of my understanding, no they are not. man and apropos provide information on executables (e.g. commands like cd, ls) and file naming-conventions. If there were a secret door leading to the rest somewhere, then this would be me trying to find it: ](*,)

I need documentations for stuff like Standard Library Routines for GNU C++, which tells you what functions/routines to call, which classes to use, type of datastructures etc.

To give an example on sprintf from [http://www.cplusplus.com/]("http://www.cplusplus.com/"):
 > 
```
 int  sprintf ( char * buffer, const char * format [ , argument , ...] ); 
```

**Print formatted data to a string:**
Writes a sequence of arguments to the given buffer formatted as the format argument specifies.

**Parameters:**
*buffer*
    Buffer where to store the resulting formatted string. 
*format*
    String that contains the text to be printed. Optionally it can contain format tags that are substituted by the values specified in subsequent argument(s) and formatted as requested. The number of format tags must correspond to the number of additional arguments that follows.

The format tags follow this prototype:
*%[flags][width][.precision][modifiers]type*
...


This is really bumming me out :-|

---

### Post by toojays on 2006-01-25
If you want documentation for the standard C library, install the package libc-doc. Then you will have all the man pages (i.e. you can do "man sprintf" and get what you expect), as well as the (more comprehensive) info file for libc (which you can view using Emacs or the info program).

Alternatively, you can get the same information in two massive hardcover volumes: [ GNU C Library: Application Fundamentals](http://www.gnupress.org/clib-fund.html) and [GNU C Library: System & Network Applications](http://www.gnupress.org/clib-system.html).

---

### Post by Gilward Kukel on 2006-01-25
[QUOTE=toojays]If you want documentation for the standard C library, install the package libc-doc.[/QUOTE]
I think the package is called glibc-doc. And it is only for C, not for C++.
For C++, I think you need to install the package libstdc++6-4.0-doc.
Then look at file:///usr/share/doc/gcc-4.0-base/libstdc++/html_user/index.html
Here is the online version: [http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/index.html](http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/index.html)

---

### Post by Viro on 2006-01-26
[QUOTE=glinsvad]Well don't I feel silly... the manual has its own manual :p
```
man man
```


To the best of my understanding, no they are not. man and apropos provide information on executables (e.g. commands like cd, ls) and file naming-conventions. If there were a secret door leading to the rest somewhere, then this would be me trying to find it: ](*,)
[/QUOTE]


Install the development documentation. I think it's manpages-dev, and you will have the standard C documentation. For C++ documentation, just use the libstdc++ docs you can find on the GNU website.

---

### Post by glinsvad on 2006-01-27
thanks guys, that was just what the doctor ordered...

---

### Post by henok on 2009-10-06
> **Gilward Kukel said:**
> For C++, I think you need to install the package libstdc++6-4.0-doc.
Then look at file:///usr/share/doc/gcc-4.0-base/libstdc++/html_user/index.html
Here is the online version: [http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/index.html](http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/index.html)
It turns out manpages-dev is what I needed. But I installed libstdc++6-4.1-doc earlier and I was wondering how I can use it? What's the command?

---

### Post by dwhitney67 on 2009-10-06
> **henok said:**
> It turns out manpages-dev is what I needed. But I installed libstdc++6-4.1-doc earlier and I was wondering how I can use it? What's the command?

Try loading this document from your web browser:
```

file:///usr/share/doc/gcc-4.1-base/libstdc++/html/index.html

```
Btw, why did you install the 4.1 version?  Version 4.3 is available (although it probably discusses the same API).

---

