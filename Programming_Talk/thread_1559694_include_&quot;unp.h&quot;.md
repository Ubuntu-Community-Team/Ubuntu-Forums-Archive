---
title: "include &quot;unp.h&quot;"
date: 2010-08-23
forum: Programming Talk
---

### Post by ggankhuy on 2010-08-23
Guys I am trying to do some network programming. THe book calls for including "unp.h" file in the c file. --> #include "unp.h".
But compiler can not find it, what package do I have to install so that unp.h is installed in the appropriate folder?  Can someone give me a hint? Thanks!

---

### Post by monkeyking on 2010-08-23
Doesnt your book include a cdrom, or a website where you download it?

---

### Post by jon zendatta on 2010-08-24
[http://socketprogrammer.blogspot.com/2009/04/unix-network-programming.html]("http://socketprogrammer.blogspot.com/2009/04/unix-network-programming.html")

---

### Post by ggankhuy on 2011-08-22
looks like this post has been active a while ago. Here I am in dire need to get some info about the book.
I obtained the source for unp.h but when i compile it under ubuntu11 i get stream of endless errors which i resorted to modifying the unp.h a lot to go ahead. Still at this time, I am unable to get the file built. Does anyone know what unix distribution and version the source it is designed? Thanks,

---

### Post by Bachstelze on 2011-08-22
We can't help you if we don't have the code. ;)

---

### Post by dwhitney67 on 2011-08-22
> **ggankhuy said:**
> looks like this post has been active a while ago. Here I am in dire need to get some info about the book.
I obtained the source for unp.h but when i compile it under ubuntu11 i get stream of endless errors which i resorted to modifying the unp.h a lot to go ahead. Still at this time, I am unable to get the file built. Does anyone know what unix distribution and version the source it is designed? Thanks,

The unp.h is a file that (re) declares utility functions; undoubtedly it was written for use under (older) Unix systems, maybe Linux (prior to ver 2.6.x).

If you want to proceed with socket programming, the file is *not* required.

P.S. Refer to this guide: [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by ggankhuy on 2011-08-22
> **Bachstelze said:**
> We can't help you if we don't have the code. ;)

not sure posting code will help, it will suck you all into endless debugging tasks. so far i tried with gcc, bcc each has different error outputs. i will try with cc. and see what happens.

---

### Post by ggankhuy on 2011-08-22
> **dwhitney67 said:**
> The unp.h is a file that (re) declares utility functions; undoubtedly it was written for use under (older) Unix systems, maybe Linux (prior to ver 2.6.x).

If you want to proceed with socket programming, the file is *not* required.

P.S. Refer to this guide: [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

Not sure about the fact the file is not required. Obviousy unp.h file is not included in the std linux headers which I initially mistakenly thought so. Are you saying all the definitions in the unp.h is not required? I am at work now, I will try removing "include unp.h" line and try building it once I get home and post the result. thx.

---

### Post by karlson on 2011-08-22
> **ggankhuy said:**
> Guys I am trying to do some network programming. THe book calls for including "unp.h" file in the c file. --> #include "unp.h".


When you post something like this one might have a natural question of "Which book?"

> 
But compiler can not find it, what package do I have to install so that unp.h is installed in the appropriate folder?  Can someone give me a hint? Thanks!

If you have copied the code from a CDROM that came with the book it should have an "include/" directory that contains this file.

If you are trying to write your own code I would very seriously suggest not to use that header at all as you have noted yourself it's not part of Linux standard headers...

---

### Post by dwhitney67 on 2011-08-22
> **ggankhuy said:**
> ... I am at work now, I will try removing "include unp.h" line and try building it once I get home and post the result. thx.

Undoubtedly you will encounter other compiler errors/warnings with the other code you got from the book.  Is this book by any chance written by Richard Stevens?

Anyhow, Linux is *not* Unix; thus there are differences in data structures, and no doubt you might discover these when you attempt to compile the code.

If you want to learn how to develop servers and clients, refer to the online documentation I offered earlier.

---

### Post by ggankhuy on 2011-08-22
> **karlson said:**
> When you post something like this one might have a natural question of "Which book?"



If you have copied the code from a CDROM that came with the book it should have an "include/" directory that contains this file.

If you are trying to write your own code I would very seriously suggest not to use that header at all as you have noted yourself it's not part of Linux standard headers...

It is Unix Network Programming by Richard Stevens. 3rd ed. 
you can put the unp.h file same folder as the source code.
and to include "unp.h".
I bought used version of the book and no cdrom. Not sure if brand new version of the book contains cdrom. I found unp.h file from internet and also book has appendix has the content of unp.h printed. compared and it matches.

---

### Post by dwhitney67 on 2011-08-22
> **ggankhuy said:**
> It is Unix Network Programming by Richard Stevens. 3rd ed. 
you can put the unp.h file same folder as the source code.
and to include "unp.h".
I bought used version of the book and no cdrom. Not sure if brand new version of the book contains cdrom. I found unp.h file from internet and also book has appendix has the content of unp.h printed. compared and it matches.

Google for R. Stevens... I'm sure the source code is available somewhere.  However, I can tell you now, it will not compile under Linux.

If you want to play with Socket Programming, under Linux, you can play around with the code I dabble with from time to time.  Please refer to the attached file.

---

### Post by areYess platter on 2012-10-09
hey, u must be going through book of UNIX network programming by STEVEN's..
the header <unp.h> is mentioned there. 
that header file includes all the headers needed for network programming.
go through the source of that file and include the header accordingly.

i hope that satifies you.

---

### Post by areYess platter on 2012-10-09
you can do one more thing.
1. cd unpv13e/lib folder contains "unp.h".
2. copy this header file and paste it the folder where your source code is.
foe eg:- u try to make a new program xyz.c in say :- desktop/programs paste the unp.h header file from above in this folder.
3. in ur source code xyz.c, include "unp.h".
4. gcc xyz.c -o xyz
5. volla..!! .. . :D

---

