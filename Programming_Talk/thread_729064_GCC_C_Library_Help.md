---
title: "GCC C Library Help"
date: 2008-03-19
forum: Programming Talk
---

### Post by buntu_Geek on 2008-03-19
Hi Friends,

I want to know where can i find the list of header files and their respective documentation... that is, the functions that they provide, what all they do, what all arguments they need to do their function.... and stuffs like that...

For example in Borland TC there is something called as help ... which has list of all headers constants... functions...( the help screen can be got by right clicking the screen..)

So please give me some suggestions on where can i find the documentation and stuffs for GCC. C Libraries....( any IDE that has this.... or any help file wud do...)

---

### Post by Hospadar on 2008-03-19
erm, they are probably in /usr/include or /usr/share/include, but to be honest, I think you would be much better off just using the googletron to find info.

For example, a quick google search for "math.h", the first result is [http://www.cplusplus.com/reference/clibrary/cmath/](http://www.cplusplus.com/reference/clibrary/cmath/) which is way more helpful than just looking at the header.

Another thing too, using online reference documentation will help you avoid depricated functions, stubs, and other functions not generally intended for use.  Also, headers installed on your system probably have minimal comments since they are intended to be small, and not intended to be convenient for learning c.

If you are using libraries that arn't in the standard C/C++ libraries, you are much better off using the library maintainers documentation (from the website generally) than installed files.

If there is documentation installed, it will generally go to /usr/share/doc

---

### Post by buntu_Geek on 2008-03-19
Yeah i know where the header files are there....( in include...)
But i want the docs and i m not askin for the comments in the headers...

Anyways i always search thro the TRON before posting here.... 

I need the documentation alone....GCC C library Documentations... where can i get it from..... :-o

---

### Post by igknighted on 2008-03-19
[http://www.acm.uiuc.edu/webmonkeys/book/c_guide/](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/)

This help?

---

### Post by LaRoza on 2008-03-19
See the sticky in the Programming Talk.

(And my wiki has references for the standard and Posix headers)

---

### Post by buntu_Geek on 2008-03-20
Thank you igknighted was quite helpfull but was not i asked...

i want the docs of all headers in gcc.... C headers

If you refer the /usr/local/include or in some other location ( the include directory) has many headers for which there are no common documentation....
and the man/info pages doesnt have many things to say about them....

---

### Post by lnostdal on 2008-03-20
```

root@ibmr52:~# aptitude search manpages | grep dev
p   manpages-de-dev                 - German development manpages               
i   manpages-dev                    - Manual pages about using GNU/Linux for dev
p   manpages-fr-dev                 - French version of the development manual p
p   manpages-ja-dev                 - Japanese version of the manual pages (for 
p   manpages-pl-dev                 - Polish man pages for developers           
i   manpages-posix-dev              - Manual pages about using a POSIX system fo
p   manpages-pt-dev                 - Portuguese Versions of the Manual Pages   

```

..what you want to do is:

```

sudo aptitude install manpages-dev manpages-posix-dev

```

now you can do:

```

man -k pipe
man 2 pipe
man 7 pipe

```
..etc..

(if this is not mentioned in the FAQ it should be added)

---

### Post by WW on 2008-03-20
There is also [gcc-doc](http://packages.ubuntu.com/gutsy/gcc-doc), but I'm not sure if this has the information that you are looking for.

---

### Post by LaRoza on 2008-03-20
> **lnostdal said:**
> 
(if this is not mentioned in the FAQ it should be added)

Find the thread on C and C++ (link in the sticky) and ask it to be added.

---

### Post by buntu_Geek on 2008-03-21
i havnt got any satisfactory solutions...
Btw i want to know how you guys know what all are the functions provided in the library files..... :-o
How do you code....?? Prototypes, etc, etc.....( i dont think that you guys keep writing your own functions...!!! )

Please help.... this newbie..... :(

---

### Post by LaRoza on 2008-03-21
> **buntu_Geek said:**
> i havnt got any satisfactory solutions...
Btw i want to know how you guys know what all are the functions provided in the library files..... :-o
How do you code....?? Prototypes, etc, etc.....( i dont think that you guys keep writing your own functions...!!! )

Please help.... this newbie..... :(

The standard library? We know from experience what is in there, or we use a guide (like the ones I have in my wiki)

There aren't that many standard library functions for C, and some are used all the time. 

Yes, when following structured programming we do write functions, obviously. Typically, a functions related to a specific purpose are in one file, with a separate header file. This file is compiled into a module that can be used in other programs.

---

### Post by lnostdal on 2008-03-21
hmf .. maybe you want 
```
info libc
```

online version is here:
[http://www.gnu.org/software/libc/manual/](http://www.gnu.org/software/libc/manual/)

can download it:

```

sudo aptitude install glibc-doc

```

..leading you to   file:///usr/share/doc/glibc-doc/html/index.html    (use your web browser)

---

### Post by sq377 on 2008-03-22
For the common/standard libraries, use "man functioname".  If it is something more complex, there is usually documentation for the package
for example:
sudo apt-get install devhelp libgtk2.0-doc libgtk2.0-dev
now run devhelp and you can search the api documentation for gtk.

---

