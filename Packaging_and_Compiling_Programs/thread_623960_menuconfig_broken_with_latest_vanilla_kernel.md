---
title: "menuconfig broken with latest vanilla kernel?"
date: 2007-11-26
forum: Packaging and Compiling Programs
---

### Post by fftb on 2007-11-26
Hi, 

I tried to configure the latest piece from kernel.org (linux-2.6.23.8) with 

[FONT="Courier New"]$ sudo make menuconfig[/FONT]

it compiles fine, but it failed when it comes to display the ncurses interface. It seems broken, arrow-keys don't work, cluttered. See screenshot enclosed.

So I tried different terminals like urxvt and the virtual console on two different machines but without luck. xconfig and gconfig are no options. Google gives me no hints with this issue.

I'm running Gutsy. *libncurses5* and *libncurses5-dev* are installed.

Anybody experiencing the same? Any hints or ideas on how to solve this?

Benjamin

---

### Post by fftb on 2007-12-13
Issue solved with 2.6.23.9

:P

---

