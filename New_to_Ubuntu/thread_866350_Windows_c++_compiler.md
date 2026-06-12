---
title: "Windows c++ compiler"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-07-21
I'm studying C++ atm

I'm using g++ for compiler and gedit  for writing which suits me fine

but does anyone know of a compiler which will allow me to compile programs on linux to be run on windows computers?

---

### Post by ibuclaw on 2008-07-21
There is, but there isn't.

I advise that if you wish to use programs for both, you'll have to make sure that the **sourcecode** is compatible with both systems. Then you just transport the sourcecode and compile on both to get your separate binaries.


You **could** try WINE, however.
```
sudo apt-get install wine
```
and use **wineg++** from that.

You'll need quite a few dev packages though, and there is no guarantee that it will compile alright.

Regards
Iain

---

### Post by Primefalcon on 2008-07-21
I alreay have wine installed I'll give this a try, sigh so theres no simple answer dang

---

### Post by Primefalcon on 2008-07-21
didn't work :-( ok damm what is a good free c++ compiler for windows

---

### Post by ibuclaw on 2008-07-21
**Dev C++** :D

[http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)

Sorry, I almost forgot about this...

It should install and run under WINE pretty smoothly!

[EDIT]
Or if you don't wish to install, you can get DevC++ Portable here:
[http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable)

It's exactly the same, but it is all within one executable binary that you can take anywhere you want.

Regards
Iain

---

### Post by Primefalcon on 2008-07-21
sweet thx :-)

---

