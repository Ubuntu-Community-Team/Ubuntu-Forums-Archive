---
title: "Ubuntu 9.04 Requirements...."
date: 2009-04-25
forum: Recurring Discussions
---

### Post by DracoJesi on 2009-04-25
Yes, I went there, obviously I'm not having problems seeing as they're so low you can run it on hardware generations old...

you see, I often get asked about how one can secure or fix Windows, which OS to use, and which I use, and whenever Linux comes up, you can imagine the comments, like "I can't run Linux, I don't know how to code" or "Gaming sucks on Linux" or "Linux GUI isn't pretty or easy to navigate as Windows" but usually I hear "What the (insert) is Linux?

with so many people telling me their so sick, of Vista but aren't sure what to do about it, so I've decided to write an article to post on the various networking sites I'm on.. to show people they really do have a choice in the matter, and that with package managers and Distros like Ubuntu (user friendly yet very powerful, and easily customizable...) Linux isn't just for coders anymore....

but I can't find any requirements for Ubuntu except the 256MB memory requirement... and is that the lowest value? or a conservative one...

it will be an article, not a book, but I want it to go over the basics... a bit...

I'll cover, in brief detail...

1. Minimum requirements for XP,Vista Home/Business/Premium, Windows 7 and Ubuntu, mentioning my experience with XP Home/Professional, Vista Home Premium and Ubuntu and weather or not I think the W requirements are completely truthful, after Vista performance is the issue isn't it? well, and security...

2 What is Linux, and the philosophy behind it...

3 Ubuntu, Kubuntu, Ubunto Studio, oh my, what's the differences, and how they are all the same at the core (yay session manager!)

4 comparison of Windows layout vs Gnome (I thought Gnome would make transition easier)

5 Installing programs by packages, and a brief on manually using make, make install, and configure

6. Stability, Windows vs Linux, the concept of a virus free world, no defragging every two weeks or so..

7 Compatibility using Wine (and VMware if itt doesn't get to long)

8 cross-platform and Linux applications...

9 Compiz of course

and mention of the cool live cd, and whatever else I can fit in.. and hey, maybe someday when I'm reading maximum pc or the like, I'll see Linux mentioned , instead of seeing windows mentioned every single page....well ok, to be fair Ubuntu was #50 of the greatest PC innovations, they listed......... and I do see Linux from time to time, but I could count the times I've seen on one hand...


anyway, think I can fit all that in?

---

### Post by CatKiller on 2009-04-25
Good luck with the article!

> **DracoJesi said:**
> but I can't find any requirements for Ubuntu except the 256MB memory requirement... and is that the lowest value? or a conservative one...

The problem, if you can call it a problem, is that the GNU/Linux system is so flexible. You can choose different window managers for a spectrum from lightweight to full of bling, or no window manager at all, or a full Desktop Environment. A compositing window manager like Compiz, or KWin, or Enlightenment, actually reduces the requirements, since it offloads the drawing of windows to dedicated hardware rather than doing it all on the processor. But then Compiz' animations and effects (especially if you enable them all) require much more processing power than just drawing the windows.

As I understand it, the minimum RAM requirements are just that; a minimum to get a reasonable environment. Not **fast**, but reasonable. Xubuntu's is lower than Ubuntu's because XFCE as a desktop environment is lighter than Gnome, but DSL's requirements are lower still. The RAM requirements are higher for running off the live cd than for a hard drive install since for anything to run at all it needs to be loaded into memory, and for the live session **everything** has to be loaded into memory; there's not the option of caching the data to the hard drive, and CD drives are really slow.

Again, as I understand it, there's no real need to specify a minimum processor speed, since having a motherboard that supports the appropriate amount of RAM means that the processor must be fast enough to run Linux. In my limited experience, RAM is much more of a performance booster in Linux than processor speed. The more RAM you can throw at it, the better the experience you'll have.

Just my unscientific opinion, anyway.

---

### Post by Sef on 2009-04-25
1) > ...RAM is much more of a performance booster in Linux than processor speed. The more RAM you can throw at it, the better the experience you'll have.
That is correct.

2) Moved to Recurring Discussions.   Those questions have all been asked before.

---

### Post by DracoJesi on 2009-04-25
> **CatKiller said:**
> Good luck with the article!



The problem, if you can call it a problem, is that the GNU/Linux system is so flexible. You can choose different window managers for a spectrum from lightweight to full of bling, or no window manager at all, or a full Desktop Environment. A compositing window manager like Compiz, or KWin, or Enlightenment, actually reduces the requirements, since it offloads the drawing of windows to dedicated hardware rather than doing it all on the processor. But then Compiz' animations and effects (especially if you enable them all) require much more processing power than just drawing the windows.

As I understand it, the minimum RAM requirements are just that; a minimum to get a reasonable environment. Not **fast**, but reasonable. Xubuntu's is lower than Ubuntu's because XFCE as a desktop environment is lighter than Gnome, but DSL's requirements are lower still. The RAM requirements are higher for running off the live cd than for a hard drive install since for anything to run at all it needs to be loaded into memory, and for the live session **everything** has to be loaded into memory; there's not the option of caching the data to the hard drive, and CD drives are really slow.

Again, as I understand it, there's no real need to specify a minimum processor speed, since having a motherboard that supports the appropriate amount of RAM means that the processor must be fast enough to run Linux. In my limited experience, RAM is much more of a performance booster in Linux than processor speed. The more RAM you can throw at it, the better the experience you'll have.

Just my unscientific opinion, anyway.

seems pretty scientific to me, theres experiments (experience through messing around, trial and error, analysis, and your hypothesis based on experience, yep pretty scientific :)

anyway, it's pretty incredible that graphic powerhouse like Compiz actually boosts CPU performance like that, but it makes sense, it reminds me of AMD's new Fusion platform (love the mascot/logo) of having the CPU/GPU's directly communicate in a whole way... amazing stuff, so it's not exactly the same but hey, it is in way..

the Ram makes sense to, with all the leaks and overall bad memory manage I've noticed running windows, you can imagine it kind of defeats the whole purpose of RAM in a way, I mean whats the point of storing information if you can't find it? come to think of it, it's kind of like all your ram is the CPU Cache, well maybe not exactly, but with memory management in Linux the way it is... it's like all the data in the memory is right there, no lag, and then your right, RAM would be more important,because if the data  is right there, all the time, the CPU never has to re-process it, it's a one time deal... so the CPU gets used allot less than say in Windows or OSX, once its in the memory it's good to go, the CPU just grabs it and makes it happen...

is that what you were getting at or did I completely miss the point :(

I forgot about just stripping down the GUI lol

and thanks...

---

