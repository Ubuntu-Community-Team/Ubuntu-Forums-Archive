---
title: "Eclipse system requirements"
date: 2005-03-10
forum: Programming Talk
---

### Post by Ron W on 2005-03-10
Does anyone know what the minimum system requirements are for Eclipse? I can't seem to find any info on their site.

At the moment I'm just wanting to use Eclipse SDK 3.0.1 to write programs in Java (will also download Sun's SDK 5.0).

Thanks

Ron

---

### Post by pighead3 on 2005-05-23
\\:D/ 
< eclipse 3.0 :sun jsdk 1.4.x
eclipse 3.1.x :sun jsdk 5.0

---

### Post by mendicant on 2005-05-23
It does eat up ram.  Top says resident and shared for my 3.1M7 currently running:
```

123m  53m

```
So, I would think you'd like at least 512MB of ram, and more is always better of course.  I have a GB of ram on my development machines.  It runs fine on a 1.8 Ghz Centrino laptop.

---

### Post by schentuu on 2005-06-16
Hi!

I'm using Eclipse on an older Notebook with 192 MB RAM and a 400 MHz Intel Celeron (Coppermine) CPU

And i have no Problems with that!

I'm not running Ubuntu, but i registred to this board to tell you that 512 MB are absolutely not needet.

Im running
gentoo linux, kernel 2.6.9
gnome 2.8.0
eclipse 2.1.3

Used Memory:
74,5 MB before starting eclipse
97,2 MB after starting eclipse
102 MB during compiling a simple GUI

Used Swap:
0 MB


I can't emagine that eclipse 3.1 needs so much more memory!


I hope my report did help you a little bit.

best wishes

schentuu

---

### Post by LordHunter317 on 2005-06-16
Eclipse requires 2X the amount of RAM you have, and at least a 100MHz faster processor.

And no, I'm not joking, and it's always true.  Eclipse has this funny habit that if you throw more resources at it, you'll find more ways to waste them.  On Windows, I've never seen eclipse not eventually force heavy paging after a full day (8 hours) of development.  This on both 512MB and 1GB RAM boxes.  Eclipse is also a leaky bitch.

FWIW, on Windows, running JBoss, Eclipse, and Firefox is extremely painful with 512MB.  1GB is only marginally better -- things are slow, but I don't have to wait more than about 3 seconds for everything to page back in.

Linux isn't likely to be extremely better.

It depends heavily on what you're doing, of course.

---

### Post by mendicant on 2005-06-16
I work fine with Eclipse up for a week at a time on Linux.  I think this was with 3.1M7 or one of the RC's.  Maybe twice a week, I'll close all the editors, but I never do anything special, otherwise.  But it is a bit of a memory hog--only firefox is worse on my system.

---

### Post by LordHunter317 on 2005-06-16
I find it doubtful firefox is actually worse.  Really.

Also, you can and should use JDK 5.0 regardless of what version of eclipse you're using.  Note that only the 3.1 pre-releases understand 5.0 constructs, so you may want to install a 1.4.2 JVM and use that for development.  However, running eclipse in a 5.0 JVM will make life much nicer.

---

### Post by mendicant on 2005-06-16
Counting only resident size as reported by top, yes, firefox is worse, 232m vs 203m for eclipse.  Virtual size, eclipse can be bigger--I just started a new one, and it's at 298m vs 303m for firefox, but that can change by giving the approriate command line VM argument to give a bigger heap.

---

### Post by mendicant on 2005-06-16
I should note that I do have a bunch of extensions running--a newly opened firefox without extensions (besides the English (GB) language Pack) takes up only 26m resident.

---

### Post by LordHunter317 on 2005-06-16
[QUOTE=mendicant]I should note that I do have a bunch of extensions running--a newly opened firefox without extensions (besides the English (GB) language Pack) takes up only 26m resident.[/QUOTE]
 Yes, lots of extensions (esepecially leaky ones) can make firefox ballon in memory usage.
So can open threads with lots of images, there used to be a bug where FF didn't properly reclaim all the memory.

---

### Post by schentuu on 2005-06-16
Hi its me again!

because i'm teaching my girlfreind java, i installed eclipse on her notebook.
And this is an realy old one:
Pentium MMX 233 MHz, 92 MB RAM

because she's running Win98 [IMG]http://ubuntuforums.org/images/smilies/icon_redface.gif[/IMG]  , i downloaded eclipse3.0.2 win32 (i found no older verion)
I thoght that this would never run, but i gave it a try.

And its running!
O.K. its nasty slow, but it works.

never say never  ;-) 

i think the linux-vesion of eclipse3.0.2 should run also.
So more memory would be nice, but it isn't absolutely nessesery.
Eclipse shuold run even on realy old boxes, it's just a matter of time  :grin:

---

### Post by LordHunter317 on 2005-06-16
I wouldn't ever try using eclipse on 92MB of RAM, nor Windows 98.  Java performance is so pitiful on that platform it's not even worth considering IMO.  I can only imagine what the delays must be like, and how much the harddrive must be grinding.

You have far more patience than I do.

---

### Post by warfly on 2005-06-19
[QUOTE=LordHunter317]I wouldn't ever try using eclipse on 92MB of RAM, nor Windows 98.  Java performance is so pitiful on that platform it's not even worth considering IMO.  I can only imagine what the delays must be like, and how much the harddrive must be grinding.

You have far more patience than I do.[/QUOTE]
Eh, are you still bashing Java again? :) I still keep my old Windows 98 SE partition along with Ubuntu one, and from time to time I'm using Eclipse to build and package my applications on Win32 platform. I haven't found any significant performance difference between those platforms. Actually it runs bit more smoothly on Windows.

IMO to do any serious work in Eclipse on any platform, you will need 128m ram as minimum. On Linux with GTK+ version, just don't use pixmap theme with it and it will run fine.

---

### Post by LordHunter317 on 2005-06-19
[QUOTE=warfly]Eh, are you still bashing Java again? :)[/quote]No, but the virtual size of the javaw.exe on Windows is > 70MB on startup.  I can't see that being comfortable on Windows 98 with that paltry amount of RAM.

I refuse to do Java development on anything less than 512MB of ram, FWIW.

---

