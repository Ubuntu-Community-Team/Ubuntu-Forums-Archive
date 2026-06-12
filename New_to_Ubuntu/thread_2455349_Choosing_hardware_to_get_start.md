---
title: "Choosing hardware to get start"
date: 2020-12-17
forum: New to Ubuntu
---

### Post by sairfan1 on 2020-12-17
I have been working on MS based environment for years, now want to setup Linux/Ubuntu based machine for first time forever, so I do not have any idea of Linux/Ubuntu world.

**What I want to do: **I want to setup a machine where I can install 

Web Service/Server like Apache etc (finally i would like to publish server on the internet, everything is just to learn)
PHP
MySQL
Nodejs 
VS Code
Use Serial Port
And some IoT related things 

First of all i have to choose hardware, for that i googled but i was not clear what processor types are well supported, here i want some hardware (PC) that has good support for Ubuntu so that i do not waste my time and get into it quickly.
I want to know if _processors families like Core i3, i5 or i7 from 2011 to 2013_ has good support for latest version of Ubuntu?
I also want to know support for _Xeon processor family_ as those workstations looks good to run 24/7 for example _Xeon 5620_ or i should consider something newer like E3, E5 v3

And lastly if any other advise that something i should consider.
thanks

---

### Post by CelticWarrior on 2020-12-17
> [COLOR=#000000]I want to know if [/COLOR]_processors families like Core i3, i5 or i7 from 2011 to 2013_[COLOR=#000000] has good support for latest version of Ubuntu?[/COLOR]
[COLOR=#000000]I also want to know support for [/COLOR]_Xeon processor family_[COLOR=#000000] as those workstations looks good to run 24/7 for example [/COLOR]_Xeon 5620_[COLOR=#000000] or i should consider something newer like E3, E5 v3[/COLOR]

ALL CPUs are supported, Intel or AMD or others. Just stay away from the Intel Atom 64-bit families that are usually paired with a 32-bit UEFI but you really don't want those for your project anyway. Any of the ones you mentioned have really good support.

What you should be thinking of first and foremost is definitely not CPUs. It's the network card: Prefer Intel. All the others are supported but Intel's hardware for networking is just better (this is unrelated to Ubuntu or any other OS).

---

### Post by CatKiller on 2020-12-17
> **sairfan1 said:**
> (everything is just to learn)

Use hardware that you already have, or grab a raspberry pi. Once you've learned what you want to learn and have a particular application in mind, you'll have a much better idea of what hardware you'll need for it.

---

### Post by CelticWarrior on 2020-12-17
> **CatKiller said:**
> Use hardware that you already have, or grab a raspberry pi. Once you've learned what you want to learn and have a particular application in mind, you'll have a much better idea of what hardware you'll need for it.
This ^^^ is am excellent idea (and very cheap).

---

