---
title: "64 or 32 bit"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by xoger on 2008-07-25
hi i installed ubuntu 8.04 
i want to install graphics drivers for my nvidia geforce 6800gt card
on nvidia's driver download site is asks wheather i have 64 or 32 bit linux. which do i choose?

---

### Post by aeiah on 2008-07-25
it depends which version of linux you have. you may want to install them via the restricted drivers manager in linux to make things easier for you though, or if you want the newest, you may find that tseliot's script called Envy will be the best way to go about it.

[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by sdennie on 2008-07-25
For a 6800GT, I would advise against using anything but the default drivers that are available in Ubuntu via System->Administration->Hardware Drivers.  That card has been well supported for many years and switching to the drivers manually downloaded from the nvidia website will be a very large hassle for probably no benefit whatsoever.

---

### Post by xoger on 2008-07-25
but i need the latest drivers to play games in 1024x768

edit

i downloaded the drivers but when i tried to install them it said i had to install the libc header, how do i do this

---

### Post by sharks on 2008-07-25
i think u can use 32 bit on a 64 bit.

---

### Post by philinux on 2008-07-25
> **xoger said:**
> but i need the latest drivers to play games in 1024x768

edit

i downloaded the drivers but when i tried to install them it said i had to install the libc header, how do i do this

What does it say under System>Admin>Hardware Drivers.

Is the default driver in use and enabled?

---

### Post by xoger on 2008-07-25
it is but i need the latest drivers

---

### Post by Archmage on 2008-07-25
> **xoger said:**
> i downloaded the drivers but when i tried to install them it said i had to install the libc header, how do i do this

If you are not a Linux crack, I would suggest to use envyng. This way you'll get the latest driver.

---

### Post by Joeb454 on 2008-07-25
You could try EnvyNG, although I believe you need to reinstall the drivers after every kernel update (linux-image etc.)

Also to find out if you're using 64 bit or not, open a terminal (Applications &#8594; Accessories &#8594; Terminal) and enter ```
uname -m
``` If it returns "x86_64" then you're running a 64 bit system

---

### Post by adamogardner on 2008-07-25
and if it runs i686 after "uname -m" ?

---

### Post by philinux on 2008-07-25
> **adamogardner said:**
> and if it runs i686 after "uname -m" ?

Then you're running a 386 system

---

### Post by decoherence on 2008-07-25
> **philinux said:**
> Then you're running a 386 system

aka, a 32 bit system

---

### Post by adamogardner on 2008-07-25
686, means 386, which actually means 32.  32 goes into 386 12.0625.  that makes sense but where does the 8 hundredth value come in with 868?

---

### Post by decoherence on 2008-07-28
as far as i know, these naming conventions are mostly historical.

386 was the first 32-bit x86 processor. If a package is marked as being for 386, you know it will run on any x86 from the latest Core 2 Duo down to an ancient 386. Software for 686 takes advantage of improvements since the 386 days. Such software won't run on anything older than a Pentium Pro.

Lots of people use 386/686 interchangeably in the context of 32-bit vs 64-bit systems. They are also commonly referred to as IA32 (intel architecture 32-bit.)

To make matters more confusing, 64-bit processors are commonly referred to as x64, AMD64 (regardless of if it's an intel or amd processor) EM64T and others. There is even less good reason for the multitude of names than there is on the 32-bit side ;)

The simplest accurate way to refer to the different families are "x86-32" and "x86-64"

---

### Post by ibuclaw on 2008-07-28
> **xoger said:**
> it is but i need the latest drivers

Why on earth would you need the latest drivers for?

There is no benefit whatsoever in doing so...


and 386 comes from historical naming conventions.
Correct me if I'm wrong, but I believe it's full name is Intel 80386. Then the 80486's came out (named 486).
Next came the pentium processors... (Pent = 5 ):)
etc, etc...

As for benefits, it's all down to your Motherboard + BIOS and what you want to get out of it on the lower level processes.

For me, I was in need to have CPU freq scaling enabled.
To achieve, I had to flash my BIOS to the most recent version, and have the 64bit version of Ubuntu installed...

Regards
Iain

---

### Post by CatKiller on 2008-07-28
> **xoger said:**
> but i need the latest drivers to play games in 1024x768

This is very unlikely. Much more likely is that you need to do some configuration with the driver you're already using.

Installing a driver by any method other than through the package management system is going to almost always be more trouble than it's worth.

Perhaps if you described the particular game you are trying to run in a different resolution, and what led you to believe that a different driver would help, someone would be able to help you solve your problem.

---

