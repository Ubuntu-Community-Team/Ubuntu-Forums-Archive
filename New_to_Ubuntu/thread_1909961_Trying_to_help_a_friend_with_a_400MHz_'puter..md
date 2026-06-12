---
title: "Trying to help a friend with a 400MHz 'puter."
date: 2012-01-16
forum: New to Ubuntu
---

### Post by L Campbell on 2012-01-16
I have a friend who is interested in trying Ubuntu but he has an older computer with only 400MHz.

If you could give me a suggestion of a version of Ubuntu that might work for him I would appreciate it.

TIA.

---

### Post by Lars Noodén on 2012-01-16
[lubuntu](http://lubuntu.net/) is the lightest pre-packaged Ubuntu.  It uses LXDE.  You might take it a step further and not use a full desktop environment and use only a window manager instead.  You can choose from Fluxbox, Openbox, FVWM-crystal, and others.  They're harder to customize, usually, but much smaller and faster. IIRC Oroborus is the smallest.

You might add extra RAM to help things out, too.

---

### Post by Fernhill Linux Project on 2012-01-16
Lubuntu is the lightest official distro, but may still be a bit demanding for that. 

We would recommend trying Lucid Puppy, it should run ok on that machine (depending how much ram it has) - [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

or even Bodhi Linux, although it can be a bit sketchy, it is very light and runs ok if you don't mess and tweak too much [http://www.bodhilinux.com/system.php](http://www.bodhilinux.com/system.php)

---

### Post by Cheesemill on 2012-01-16
Can you give us any more specs?

CPU type, RAM, etc.....

---

### Post by mörgæs on 2012-01-16
There are several distros for old computers, but this one is too weak. Is it approaching 15 years of age? 

Since it is possible to get 5-6 years old hardware almost for free I would not spend time on this one.

---

### Post by Double.J on 2012-01-16
You've had some really good suggestions, I'll add in mine with [crunchbang]("http://crunchbanglinux.org/") - it's the lightest I've used in terms of RAM, which is hard to compare to the cpu I know, but openbox, it's window manager is one of the very lightest.

I'll warn you crunchbang is basic - it'll run anything ubuntu will... but it won't look pretty!

If these don't work, and you have no way to cheaply upgrade/overclock SAFELY then I find it's usually best to stick to the OS it came with such as XP.. though of course these are unsupported nowadays :-k

Edit: if it's an old PPC mac you may have more luck - my old 700Mhz ppc is still just about usable with lubuntu, our old 1ghz Pentium is a no go now for non server use:(

---

### Post by Fernhill Linux Project on 2012-01-16
We have just started posting on ubuntu forums, although I have read many articles and followed lots of posts personally. I very much like the friendly community spirit and helpfulness and find ubuntu forums a credit to the linux community....and the replies to this post just reminded me... :o)

---

### Post by Paddy Landau on 2012-01-16
> **gnu/mirow said:**
> ... I find it's usually best to stick to the OS it came with such as XP.
Lubuntu is fast compared to XP on the same hardware. If XP works, Lubuntu will work well.

You can also look at [muLinux]("http://www.micheleandreoli.it/mulinux/"), which is extremely basic but also made for very old computers (just 8**M**b RAM).

---

### Post by mastablasta on 2012-01-16
400 Mhz and low ram... yeah i am not sure it's worth it moreover if any new Ubuntu will actually run on it. Support for osme older porcessors was even dropped.

Other low resource Linuxes besides the ones already menitoned:
Slitaz
Bohdi linux (ubuntu based, but the DE still needs some work)
TinyCore

basicaly you need something stronger for a modern os or to experience anythign meaningfull beyong common install. Unless you pump it with RAM and new graphics card... :-)

---

### Post by mörgæs on 2012-01-16
As I mentioned before I don't think it pays to work with this one. 

However, some good ideas are appearing in this thread. Do you people feel like adding them in
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
if they are not in there already?

This way we have one thread to link to, every time this question comes up.

---

### Post by Paddy Landau on 2012-01-16
> **mörgæs said:**
> Do you people feel like adding them in
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Good one. I've posted muLinux.

---

### Post by L Campbell on 2012-01-17
> **Lars Noodén said:**
> [lubuntu](http://lubuntu.net/) is the lightest pre-packaged Ubuntu.  It uses LXDE.  You might take it a step further and not use a full desktop environment and use only a window manager instead.  You can choose from Fluxbox, Openbox, FVWM-crystal, and others.  They're harder to customize, usually, but much smaller and faster. IIRC Oroborus is the smallest.

You might add extra RAM to help things out, too.

Thanks for the suggestion here. I downloaded the .iso file, did the MD5sum check and burned a disk.

Then I decided to try the disk in my HP desktop machine, which has 1800MHz and the disk wouldn't boot up. All I got was about 6 lines of print.

Next I put a different hard drive in the machine and tried the disk again 
but got the same result.

Now I'm REALLY confused.    :-)

---

### Post by Double.J on 2012-01-17
Hi there, have you tried re-burning the disk? do you get a chance to get the gist of what it's saying before it cuts out?

---

### Post by Double.J on 2012-01-17
> **Paddy Landau said:**
> Lubuntu is fast compared to XP on the same hardware. If XP works, Lubuntu will work well.

In most cases, I agree; I definitely didn't mean it as an advert for XP lol. I just meant that looking at the older Windows disks that it came with may be the way to keep it going, after all xp home had the same minimum requirements as ubuntu server edition currently does; so the op may be able to get XP running if crunchbang/lubuntu wont. :)

---

### Post by Paddy Landau on 2012-01-17
> **L Campbell said:**
> ... All I got was about 6 lines of print.
Hmm, there is something wrong.

Does the computer have a USB port? It may work if you create a Live USB instead of CD (the instructions are on [the download page]("http://www.ubuntu.com/download/ubuntu/download")).

> **gnu/mirow said:**
> ... I just meant that looking at the older Windows disks that it came with may be the way to keep it going...
Ah, sorry. I understand now.

---

### Post by L Campbell on 2012-01-18
> **Paddy Landau said:**
> Hmm, there is something wrong.

Does the computer have a USB port? It may work if you create a Live USB instead of CD (the instructions are on [the download page]("http://www.ubuntu.com/download/ubuntu/download")).


Ah, sorry. I understand now.

Thanks for your interest, Paddy.

It seems that I made a really dumb error and left a disk in my DVD ROM.

Having now removed it my Lubuntu CD is working perfectly in the CD ROM.

Kind regards.

---

