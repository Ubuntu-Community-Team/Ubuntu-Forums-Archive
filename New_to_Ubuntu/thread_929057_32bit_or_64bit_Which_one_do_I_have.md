---
title: "32bit or 64bit? Which one do I have?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by PT.Linn.A on 2008-09-24
How can I tell if I have a 32 bit or 64 bit computer? Which version should I Download?

---

### Post by knix on 2008-09-24
If you download 32-bit, you know it will work.
How to tell: If you sticker says AMD or Core 2, you have 64-bit. If pentium, plain core (e.g., core duo), or celeron, then 32-bit.
I'm not sure about AMD Semprons, but athlons and opterons are 64.

---

### Post by WRDN on 2008-09-24
Open the Terminal and type:

```
uname -a
```

This will list the ubuntu version (among other things), and tell you if you have a 32bit (all processors) or 64bit CPU. If the output contains "i686 is 32bit, while x86_64 is 64bit.
If you are wondering which to download, you can play it safe if you wish by downloading the 32bit version, as this will work with all compatibile processors. Otherwise, find the CPU, and research it to find whether it supports 64bit.

---

### Post by PT.Linn.A on 2008-09-24
> **WRDN said:**
> Open the Terminal and type:

```
uname -a
```

This will list the ubuntu version (among other things), and tell you if you have a 32bit (all processors) or 64bit CPU. If the output contains "i686 is 32bit, while x86_64 is 64bit.
If you are wondering which to download, you can play it safe if you wish by downloading the 32bit version, as this will work with all compatibile processors. Otherwise, find the CPU, and research it to find whether it supports 64bit.

My output reads:

Linux pla 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux


Is this telling me that I have installed the 32 bit version (which I did), or that I only have a 32 bit processor?

---

### Post by drs305 on 2008-09-24
If you can open gnome-system-monitor the main tab will tell you what type of processor you have. (System, Administration, System Monitor) or in terminal: gnome-system-monitor

---

### Post by TheLions on 2008-09-24
type cpuid in terminal to findout what CPU you have...

---

### Post by PT.Linn.A on 2008-09-24
OK. So, I have done both: Gnome System Monitor and CPUID

I am quite new, and unsure what I am looking at.

Gnome Monitor tells me that my Processor is: Genuine Intel T2250 1.73 GHz

CPUID tells me: The same, and MUCH more (that I don't understand).

Confused I am.  :(

---

### Post by TheLions on 2008-09-24
intel T2250 is 64bit CPU

---

### Post by PT.Linn.A on 2008-09-24
> **TheLions said:**
> intel T2250 is 64bit CPU

That's fantastic!

For my own knowledge though, may I ask how you know this?

---

### Post by TheLions on 2008-09-24
T2250 is Intel Core Duo family, and all Core Duo are x64

just Google/Yahoo/whatever it!

---

### Post by PT.Linn.A on 2008-09-24
I appreciate the nudge in the right direction. Thanks.

Now I just have to decide whether to install a 64bit Distro.

---

### Post by tuxxy on 2008-09-24
> **PT.Linn.A said:**
> I appreciate the nudge in the right direction. Thanks.

Now I just have to decide whether to install a 64bit Distro.

Of course you should! why would you want 32-bit!?

Heres a link to the [64-bit user group]("http://ubuntuforums.org/group.php?groupid=258") for when you take the plunge :)

---

### Post by PT.Linn.A on 2008-09-24
> **tuxxy said:**
> Of course you should! why would you want 32-bit!?

I'm sure that's an excellent question for most. However, more relevant to me at the moment would be: Why do I want a 64bit?  :)

Open for answers/suggestions here.

---

### Post by perlluver on 2008-09-24
> **PT.Linn.A said:**
> I'm sure that's an excellent question for most. However, more relevant to me at the moment would be: Why do I want a 64bit?  :)

Open for answers/suggestions here.

It utilises both cores of the processor, it compiles programs faster, and if you do anything intensive, it will do that quicker.  Also it supports above 4GB, of memory.  If you have a 64 bit processor, why not make the most of it.

---

### Post by HittingSmoke on 2008-09-24
> **perlluver said:**
> It utilises both cores of the processor, it compiles programs faster, and if you do anything intensive, it will do that quicker.  Also it supports above 4GB, of memory.  If you have a 64 bit processor, why not make the most of it.

Since when doesn't 32 bit use both processor cores? The way I understand it, it has more to do with memory addressing and I've heard some people who report better performance with 32 bit with 3GB or less RAM.

---

### Post by perlluver on 2008-09-24
Found some documentation on the differences, [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit), you can take a look at this.

---

