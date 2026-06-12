---
title: "My Experiences with an Old Computer"
date: 2008-07-22
forum: Other OS Talk
---

### Post by init1 on 2008-07-22
A few weeks back, I tried to save a friend's Windows ME computer. It was in horrible shape. I'm surprised that it had any functionality at all, due to all the viruses and spyware that was on it. I couldn't even format the drive without getting fatal errors. The only way to save it was to write over the entire disk with dd. After doing so, I tried a few distros to try to get it working again. 
Debian
I tried several times to install it. Eventually it installed, but X was messed up, and I didn't know how to fix it

Puppy
Every time someone asks what distro they should put on their old computer, someone suggests Puppy. Even with it's great reputation, it wouldn't run. It gave some errors upon booting, and never loaded anything. 


So, unable to fix it then, I came back today with some more ideas
DSL
Another commonly suggested distro. The resolution was fine, and the internet worked, but it was in 16 color mode. 

FreeDOS
I figured that as long as he only needed it for internet, he would be fine with Arachne. However the DHCP setup hanged, so I assume that the packet driver that was loaded didn't work.  

SliTaz
Finally something that worked. The computer had just enough RAM to run it. The resolution was a bit low, and I couldn't get flash working, but it was good enough. 

Never before have I experienced such a stubborn computer. Until I tried SliTaz, it seemed as though nothing would work. And even then, the solution was far from perfect. What he really needs though is a new computer.

---

### Post by fuzzyk.k on 2008-07-22
try antix itz a mephis & debian high breed of sorts developed for old computers. it should work

---

### Post by luscinius on 2008-07-22
I have a similar problem, my friends asked if I could help them to revive the old G3 Mac laptop made in about 99. I am also thinking of what distro to put onto it. Maybe Gentoo with XFCE? Though I have had no experience with Mac, I have always had PCs.

---

### Post by darrelljon on 2008-07-22
> **init1 said:**
> A few weeks back, I tried to save a friend's Windows ME computer. It was in horrible shape. I'm surprised that it had any functionality at all, due to all the viruses and spyware that was on it. I couldn't even format the drive without getting fatal errors. The only way to save it was to write over the entire disk with dd.
That's funny because last week [someone on the MSFN forum praised Windows Me]("http://www.msfn.org/board/Now-i-m-REALLY-convinced-that-9x-is-bett-t120581.html") for booting in 20 seconds. In fact a virus on it which would have worked on XP - failed to run and actually crashed on Me. The poster is now convinced Windows 9x is better than XP etc.

---

### Post by Joeb454 on 2008-07-22
So that means Ubuntu > Win 9x > XP > Vista?

I got an old PC recently (put together from all sorts of parts from other old PC's) it's not that bad spec now :) I put Xubuntu on it (debian didn't want to work)

---

### Post by Midwest-Linux on 2008-07-22
> **init1 said:**
> A few weeks back, I tried to save a friend's Windows ME computer.  

SliTaz
Finally something that worked. The computer had just enough RAM to run it. The resolution was a bit low, and I couldn't get flash working, but it was good enough. 

Never before have I experienced such a stubborn computer. Until I tried SliTaz, it seemed as though nothing would work. And even then, the solution was far from perfect. What he really needs though is a new computer.

How much ram was in the computer? I have a couple of stubborn computer projects I am working on. Thanks

---

### Post by 3rdalbum on 2008-07-22
If formatting the hard disk gave you problems, then the disk itself was probably in bad shape. This might have been a cause for some of your troubles with other operating systems.

Luscinious, you could try a basic Debian system. Check how much RAM is in that Mac, as the 1999 iMacs came with just 32 megabytes (not enough for anything on PowerPC Linux).

---

### Post by zmjjmz on 2008-07-22
> **luscinius said:**
> I have a similar problem, my friends asked if I could help them to revive the old G3 Mac laptop made in about 99. I am also thinking of what distro to put onto it. Maybe Gentoo with XFCE? Though I have had no experience with Mac, I have always had PCs.

Try an oldstable (woody) version of DebianPPC.

---

### Post by init1 on 2008-07-22
> **Midwest-Linux said:**
> How much ram was in the computer? I have a couple of stubborn computer projects I am working on. Thanks
192MB I think.

> **fuzzyk.k said:**
> try antix itz a mephis & debian high breed of sorts developed for old computers. it should work
Antix nearly useless though because there are so many broken packages. How can you release a distro where half of the programs in the repositories have unmeetable dependencies? I couldn't even install QEMU. Probably wouldn't have been an issue though since all he really needs is internet.  

What really annoys me is that I couldn't find a distro that works as well as Windows ME. Every distro I've tried is either too resource heavy, didn't work, or wasn't as easy to use.

---

### Post by anticapitalista on 2008-07-22
> **init1 said:**
> 192MB I think.


Antix nearly useless though because there are so many broken packages. How can you release a distro where half of the programs in the repositories have unmeetable dependencies? I couldn't even install QEMU. Probably wouldn't have been an issue though since all he really needs is internet.  

What really annoys me is that I couldn't find a distro that works as well as Windows ME. Every distro I've tried is either too resource heavy, didn't work, or wasn't as easy to use.

Which version of antiX did you try?

---

### Post by LaRoza on 2008-07-22
[http://ubuntuforums.org/showthread.php?t=867240](http://ubuntuforums.org/showthread.php?t=867240)

---

### Post by zmjjmz on 2008-07-22
The antiX repositories work fine, just open synaptic and disable the MEPIS repos.

---

### Post by anticapitalista on 2008-07-22
> **zmjjmz said:**
> The antiX repositories work fine, just open synaptic and disable the MEPIS repos.

True if using M7. Since then, M7.01, M7.2 and M7.5-test2 have been released with the Mepis repo disabled by default.

---

### Post by Bungo Pony on 2008-07-23
> **init1 said:**
> 
DSL
Another commonly suggested distro. The resolution was fine, and the internet worked, but it was in 16 color mode. 


A way to fix this would have been running the x setup (I believe it's called xsetup.sh - I could be wrong) Play around with the video settings (vesa) and see what you can get working. In worse case scenarios, replace the video card and try again.

---

### Post by Frak on 2008-07-23
I've actually found people claiming that Linux runs on older computers to be more of a fallacy, or in the least, an untied shoe. Here's what I mean:

You have a foot, but its a big foot; you have money, but you don't have much money. At first you find nice shoes, but they are too small and they are expensive, though they have very nice laces. You then try on another pair of shoes. They aren't great, but they fit. You're told to buy your own laces. Finally, you find another pair of shoes, they're cheap, they fit, and they have laces. Unfortunately, you think they're slightly atrocious and have short laces. Coming as close as you can, you buy the ugly shoes with short laces.

You have a computer, but its an old computer; you have the necessary hardware, but it isn't fast or efficient hardware. At first you come upon Ubuntu, but its big and requires a lot of resources, though it has a nice UI with nice programs. You then try DSL/Puppy/Vector, it doesn't look great, nor does it have a nice UI or good codecs and whatnot, but its fast. You're then told to find/compile your own hardware support programs (drivers, firmware, etc). Finally, you find AntiX, its resource efficient, it runs on old hardware, and it comes with codecs/the like. Though, hardware support still isn't complete, and it suffers from legalities. Coming as close as you can, you go with TinyME even though it may look horrid and still have incomplete support.

---

### Post by anticapitalista on 2008-07-23
Hey Frak,

I'm sure you were giving antiX a compliment, but to point out that antiX isn't ugly! The newest, antiX-M7.5-test2 isn't ugly at all! In fact I would argue it has (one of) the sweetest default icewm setup in linuxland and its fluxbox is pretty coooool too.

---

### Post by Frak on 2008-07-23
> **anticapitalista said:**
> Hey Frak,

I'm sure you were giving antiX a compliment, but to point out that antiX isn't ugly! The newest, antiX-M7.5-test2 isn't ugly at all! In fact I would argue it has (one of) the sweetest default icewm setup in linuxland and its fluxbox is pretty coooool too.
Sorry, I got AntiX and TinyME confused. I like AntiX, I **don't** like TinyME.

---

### Post by init1 on 2008-07-25
> **anticapitalista said:**
> Which version of antiX did you try?
Either Spartacus or Lysistrata

> **LaRoza said:**
> [http://ubuntuforums.org/showthread.php?t=867240](http://ubuntuforums.org/showthread.php?t=867240)
Why was this thread forked?

> **zmjjmz said:**
> The antiX repositories work fine, just open synaptic and disable the MEPIS repos.
I think I tried that once. I don't remember what happened though

> **Bungo Pony said:**
> A way to fix this would have been running the x setup (I believe it's called xsetup.sh - I could be wrong) Play around with the video settings (vesa) and see what you can get working. In worse case scenarios, replace the video card and try again.
I tried that, but I didn't have enough colors to read the font ;)
I suppose I could have tried using a virtual terminal though. 

> **Frak said:**
> I've actually found people claiming that Linux runs on older computers to be more of a fallacy, or in the least, an untied shoe. Here's what I mean:

You have a foot, but its a big foot; you have money, but you don't have much money. At first you find nice shoes, but they are too small and they are expensive, though they have very nice laces. You then try on another pair of shoes. They aren't great, but they fit. You're told to buy your own laces. Finally, you find another pair of shoes, they're cheap, they fit, and they have laces. Unfortunately, you think they're slightly atrocious and have short laces. Coming as close as you can, you buy the ugly shoes with short laces.

You have a computer, but its an old computer; you have the necessary hardware, but it isn't fast or efficient hardware. At first you come upon Ubuntu, but its big and requires a lot of resources, though it has a nice UI with nice programs. You then try DSL/Puppy/Vector, it doesn't look great, nor does it have a nice UI or good codecs and whatnot, but its fast. You're then told to find/compile your own hardware support programs (drivers, firmware, etc). Finally, you find AntiX, its resource efficient, it runs on old hardware, and it comes with codecs/the like. Though, hardware support still isn't complete, and it suffers from legalities. Coming as close as you can, you go with TinyME even though it may look horrid and still have incomplete support.
Yeah I agree. I have yet to find a distro that works on all computers. So although Debian, works fine on mine (and on most I've tried) it doesn't work on that old computer. It would probably work with some configuration or a driver though. 

> **anticapitalista said:**
> Hey Frak,

I'm sure you were giving antiX a compliment, but to point out that antiX isn't ugly! The newest, antiX-M7.5-test2 isn't ugly at all! In fact I would argue it has (one of) the sweetest default icewm setup in linuxland and its fluxbox is pretty coooool too.
Actually, I think the UI on Spartacus (might be Lysistrata) is horrible. 
The Fluxbox panel is way to small to be even remotely useful
Windows maximize over the panel (I think)
The terminal in the menu is transparent so you can't read anything with it unless you change the background 
It uses automount (which I hate with eternal passion)
It loads conky and although you can disable it in the menu, it still starts up each time

Most of these things can be fixed, but it's a pain to do so.

---

### Post by anticapitalista on 2008-07-25
Try the latest release antiX-M7.2 Vetëvendosje or antiX-M7.5-test2.

[http://antix.mepis.com/index.php/Main_Page](http://antix.mepis.com/index.php/Main_Page)

Once you have made your personal changes, they will stick. 5 mins work maximum, I guess.

---

### Post by init1 on 2008-07-27
> **anticapitalista said:**
> Try the latest release antiX-M7.2 Vetëvendosje or antiX-M7.5-test2.

[http://antix.mepis.com/index.php/Main_Page](http://antix.mepis.com/index.php/Main_Page)

Once you have made your personal changes, they will stick. 5 mins work maximum, I guess.
Hrm, I'll consider that.

---

