---
title: "stdafx.h missing!!"
date: 2009-06-15
forum: Programming Talk
---

### Post by Dark-Byte on 2009-06-15
[SIZE=3]Hi I am getting a problem with the g++compiler because I wrote a program in C++ that makes use of the stdafx.h library and when I try to compile the program it displays an error:
*test.cc:1:20: error: stdafx.h: No such file or directory*[/SIZE]
[SIZE=3]
How should I fix this?[/SIZE]

---

### Post by jespdj on 2009-06-15
As far as I know, stdafx.h is a Microsoft Windows-specific header file. It does not exist on Linux or other operating systems.

What does your code look like? Why does it need stdafx.h? Are you trying to compile a program written for Windows on Ubuntu?

---

### Post by Zugzwang on 2009-06-15
> **Dark-Byte said:**
> How should I fix this?

Rewrite it such that it doesn't use unportable code - "stdafx.h" is something that only exists in Microsoft's VC++ environment. In the future, only use portable libraries if you actually want to port your code.

You might also want to look at the replacement header files in some other packages of Ubuntu:

[http://packages.ubuntu.com/search?searchon=contents&keywords=stdafx.h&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=stdafx.h&mode=exactfilename&suite=jaunty&arch=any)

I don't know what these do. Do not expect full compatibility!

---

