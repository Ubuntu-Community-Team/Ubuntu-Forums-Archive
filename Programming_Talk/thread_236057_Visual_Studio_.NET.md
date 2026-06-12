---
title: "Visual Studio .NET"
date: 2006-08-14
forum: Programming Talk
---

### Post by salvo1 on 2006-08-14
Hi ppl.

I've a big problem.

I've only ubuntu (as OS) on my notebook Toshiba. My HD is divided into 3 partitions:

[img]http://www.box.net/public/static/f3t2qairgr.png[/img]

I use: 
/  as OS
/dati  for music, movies... (/data)
/scuola  for university notes (/school)

I need to install, for work issues, Visual Studio .NET; in particular, i need to modify a really big web-based ASP application. Solutions are:
- To emule it (how? wine? Would be low?)
- To install WinXP.

In the last choise, i could cut 5 GB from partition /dati and boot up using WinXP-CD and install it in this 5 GB partition (are 5 GB enough?).

I've never done this operation. Have I to reconfigure grub? How?

Are there any alternatives? Maybe Mono?

---

### Post by LordHunter317 on 2006-08-14
5 GiB will not be enough for Windows + VS .NET + MSDN.

I would recommend VMWare.

---

### Post by Engnome on 2006-08-14
> **LordHunter317 said:**
> 
I would recommend VMWare.

+1 for WMware, search the forums for the how to.

---

### Post by ember on 2006-08-14
Well, 5 GB is really a little short, yet it is possible.

Visual Studio .NET (2003) takes about 2 GB, Windows XP plus some basic will take about 1 GB. Yet you will have no projects accounted then and no MSDN Library installed (which I highly recommend unless you have a permanent internet connection).

If you can spare 8, I'd say go with installing Windows, because Visual Studio eats ressources like a grasshopper plague eats plants.

---

### Post by darkninja on 2006-08-18
You can now download VMware Server for Linux for free, so it seems to be the best option.

[http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)
And to get a product-key e-mailed to you:
[http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

Create a virtual disk wherever you have some free space, install Windows and VS .Net

---

### Post by jeffnt on 2006-08-18
vmware is the best way.

---

### Post by TheApe on 2006-08-20
VMware is not the best way.
It wil only give you headache!
I've installed it and tried to use it, 'cause I need some ASP programming and developping some sites in Macromedia Flash.
But it's slow as hell!
I have Pentium 4 1.6 with 512 memory, Disabled all of windows xp visual effects and it was still a nightmare to use it.
Vmware sucks! :evil:

---

### Post by Daverz on 2006-08-20
I use vmware all the time.  It's plenty fast enough for me, and I often use it remotely from my powerbook over gigabit ethernet.  The host machine is an amd64 3200 with 1G RAM (running 32-bit Dapper).  The other things I've tried (win4lin and kqemu), are much too slow.  I was planning on using it for a .NET class coming up, so I guess I'll find out how it handles Visual .NET.

---

### Post by LordHunter317 on 2006-08-20
> **TheApe said:**
> But it's slow as hell!
I have Pentium 4 1.6 with 512 memory, Disabled all of windows xp visual effects and it was still a nightmare to use it.
Vmware sucks! :evil:You probably gave the virtualized OS way too much RAM.

---

