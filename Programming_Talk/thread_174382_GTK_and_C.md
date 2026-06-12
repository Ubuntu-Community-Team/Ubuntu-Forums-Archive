---
title: "GTK and C?"
date: 2006-05-11
forum: Programming Talk
---

### Post by Sitix on 2006-05-11
Hey! I have been programming again in C, and came to the conclusion I want to make the step from terminal to GUI. I tried to look up how to program GUI in C, and I only got as far as the term 'GTK'. I looked it up, it seemed to have use and so, but couldn't find a way to use it myself in C.

Can anyone help me with that? Or is this a *really* dumb question? :-k

---

### Post by yaaarrrgg on 2006-05-11
glade is a visual gui designer (although there may be easier ones). it will generate calllbacks you can use.

here's a quick tutorial:
[http://www.writelinux.com/glade/](http://www.writelinux.com/glade/)

---

### Post by Omnios on 2006-05-11
Gnome GTK 
[http://developer.gnome.org/doc/GGAD/ggad.html]("http://developer.gnome.org/doc/GGAD/ggad.html")

---

### Post by Sitix on 2006-05-12
Thanks for the links, I decided to try Glade... but at the end of ./configure it says the following:

checking for libxml-2.0 >= 2.4.1 gtk+-2.0 >= 2.6.0... Package libxml-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libxml-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libxml-2.0' found
configure: error: Library requirements (libxml-2.0 >= 2.4.1 gtk+-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Could that be having to do with the fact I am using Kubuntu instead of Ubuntu? I think it does... because I checked Adept, and I have both libxml1 and libxml2 installed.

--
[b]Edit: Never mind the above.. it works now I installed Glade with Adept. But I still find it strange it gave that error and that it works with Adept?

How could that be? I've had it with more things...[/b]

---

### Post by llonesmiz on 2006-05-12
You need to install the "libxml2-dev" package. It contains include files and libraries needed to compile that program.

---

### Post by Sitix on 2006-05-12
That was installed. I checked that before compiling... so.. :P that wasn't the problem...

I still think it has something to do with my KDE instead of Gnome..?

---

