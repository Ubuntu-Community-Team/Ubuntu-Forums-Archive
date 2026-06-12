---
title: "Wine error?"
date: 2017-10-22
forum: New to Ubuntu
---

### Post by chamuit on 2017-10-22
I am trying to run my son's algebra program using Wine. The Autorun.exe program starts to run and then stops with the error:

Title Bar -> Microsoft Visual C++ Runtime Library

Text Box -> Runtime Error!
Program: ...am Files (x86)\Teaching Textbooks\Algebra 1\Algebra1.exe
This application has requested the Runtime to terminate in an unusual way.
Please contact the application's support team for more information.

I have tried to do a search on Ubuntu and Wine forums but don't come up with any results.

This is new to me.  His computer crashed and I replaced his OS with Ubuntu.  Thanks for any help.

---

### Post by Impavidus on 2017-10-23
Have you checked the [Wine appDB]("https://appdb.winehq.org/")? Maybe someone else has tried the same application and found a workaround – or found that it's hopeless.

---

### Post by mastablasta on 2017-10-24
try running algebra1.exe instead of autorun.

also you need to know what the application is using to run. does it need NET framework? does it need flash maybe? is it browser based? does it maybe need java? does it need directx to run?

ubuntu is not windows and it is not a drop in replacement for windows. if one needs to run windows programs then you are better off using windows. if there is onyl one program oyu need to run in windows and if PC is good enough you could use virtualization (e.g. virtualbox).

luckily for the first year we have tasks online (in browser), so most work as they should though i noticed some would not load in linux. perhaps i would have to add pepperflash.

---

