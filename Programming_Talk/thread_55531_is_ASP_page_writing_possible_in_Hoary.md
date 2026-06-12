---
title: "is ASP page writing possible in Hoary?"
date: 2005-08-09
forum: Programming Talk
---

### Post by adamt222 on 2005-08-09
Hi all;
I've been trying (over the last few days) to get a simple yet effective means of writing and using ASP pages under Hoary. I also have a windows machine
but I only want to use APACHE web server on that box. I don't want IIS ever again, and Cassini was a waste of time- I'd like to do this in Linux... Ok..

I have installed Apache, and also have installed Mono.
I have "downloaded" xsp server- but was unable to compile and build.

Here's what I've learned:
I have been told that there are things required to develop ASP (or ASP.NET)-
Mono - i have that but have no idea how to use it to do web pages in ASP code.

To get ASP.NET going on Linux, you can do it using a module for apache called "mod_mono" which works if you have mono set up (which i do) AND....
if you have XSP installed (which has mod_mono), which I have been unable to do.

I am unable to complete the stage "./configure" for XSP server
The error kept telling me that a C# compiler was not available on the system.
Which makes sense, since XSP is written in C# code.

Then i tried to get mcs happening (mcs is a C# compiler) but that failed also...

So my overall question is .. 'Is there an easier way or does anyone know of a START TO FINISH tutorial of what to download & install and basic configuration tips?"

Thanks;
Adam

---

### Post by Reb on 2005-08-10
Try [http://www.gotmono.net/documentation/mod-mono-howto.html](http://www.gotmono.net/documentation/mod-mono-howto.html).

---

