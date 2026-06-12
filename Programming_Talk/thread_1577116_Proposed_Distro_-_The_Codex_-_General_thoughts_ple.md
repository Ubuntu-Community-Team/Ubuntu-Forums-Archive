---
title: "Proposed Distro - The Codex - General thoughts please?"
date: 2010-09-18
forum: Programming Talk
---

### Post by carlsmith on 2010-09-18
The Codex would be a GNU/Linux distro that aims to offer the user the functionality of a classical, home computer, the Spectrum 48K, but with modern specifications, for the purpose of increasing general computer literacy.
Codex uses an OS Cart, a USB stick containing only the operating system and normally used in a read only mode, as well as one or more HD Carts, more USB sticks for holding user data. This isolates the operating system for safety and allows different OS Carts to be used where that is advantageous.
Codex boots to the CLI, much like the Spectrum 48K did, but Codex uses Python2.7 as it's standard scripting language, with BASIC and BASH available too. The former for old times sake, the latter for practicality.
The selection of included Python modules would be vast and comprehensive, but would be striped of functionality that Codex never uses, networking being a good example.
Graphical applications will run in full-screen without exception and no two graphical applications will run simultaneously.
Hardware running Codex, normally a laptop or notebook, would be cheap to purchase secondhand as it would not have any use for a hard drive (nor really need a battery). Further, the lack of a windows manager etc. will lower the minimum system requirements enormously.
Codex would be aimed both at people who wish to learn to program as well as the Home Brew gaming community. It is designed to be run on cheap, accessible hardware and is not meant to be any kind of alternative to a modern OS. It is for developing creative, independent minds, promoting computer literacy and having fun, playing games and doing cool stuff.

---

### Post by Bachstelze on 2010-09-18
I don't get it. How would that be any different from doing Python, BASIC or Bash in any OS?

---

### Post by carlsmith on 2010-09-18
The idea is that you would be able to learn and play on a device you could afford to really mess up on. If you're Joe Normal, say 15 years old, and want to learn a bit of hacking, and say Dad's bought the family a new Dual-Core with Windows 7 that "Joe is not to keep messing around with" etc., then he can grab a no battery, no hard drive or caddy Laptop from ebay for a few quid, pop Codex on a stick and start playing around.
I like writing Python with gedit, using Ubuntu 10.4, but I can't afford to buy a laptop that will do that without lagging all over the place and especially not just to practice coding on. Modern graphical OS's drink RAM like it's free and abundant, mostly to do unnecessary things, but switching to a CLI based system leaves you with a technical nightmare getting any graphics you do want to see to work well. What the old set-up's had, that isn't available anymore, is the capacity to display graphics easily, despite operating the system from the CLI generally.
I know a lot of people would have no use for it, but quite a few people might.
It's still just an idea after all.

---

### Post by worseisworser on 2010-09-18
It seems you're looking at something like Debian or the Ubuntu Alternate installer without a desktop. Untick "Graphical Desktop" when installing Debian; you'll end up with a CLI-only install; go for e.g. DirectFB from there.

[http://www.directfb.org/](http://www.directfb.org/)

---

### Post by carlsmith on 2010-09-18
> **worseisworser said:**
> It seems you're looking at something like Debian or the Ubuntu Alternate installer without a desktop; untick "Graphical Desktop" when installing Debian.

You'll end up with a CLI-only install; go for e.g. DirectFB from there.

[http://www.directfb.org/](http://www.directfb.org/)

Nice one, DirectFB looks really interesting, I had tried to find something like this and got as far as matchbox-window-manager which isn't really going to cut it here. I've not had time to look into DirectFB, nor similar offerings, so I'll do that now and thank you very much for the pointer.

Could you offer any insight into how much work would be involved in getting this working silently, such that any Python script that would ordinarily output graphics in full-screen, will do so still, but without the author having to know anything about the DirectFB library? I'm expecting the answer will be to learn the DirectFB API, then write a Python module for it, but I'm unsure. Any (good) advice would be greatly appreciated.

---

### Post by absolutezero1287 on 2010-09-18
Making your own distro from scratch is downright painful. Unless you want to make it based off an already existing distribution. Check out Linux from Scratch so you can get some insight on what it means to make your own distro. [http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

---

### Post by carlsmith on 2010-09-18
I don't think DirectFB is what I'm looking for. I understand what you're saying about building a new distro, but what I'd like to do is not so ambitious. You can get a minimal Linux OS booting from a stick without much trouble and putting more Python modules on there isn't difficult. Removing stuff will be more difficult, but that isn't an immediate concern, even if anything that wasn't useful was removed, the only overt gain would be, maybe, having a smaller size OS Cart. Getting an OS that will boot from a USB stick that has a nicely expanded Python library should be the easy bit. This system will happily read and write from and to any other sticks available so you'd half way there.
The problem is that once you log in to this system, run nano, write a python script that would normally display graphics in full-screen, then flush it, leave nano and then run the script, I'm pretty sure you're not going to be treated to a full screen of pure chrome, but instead, you'll be given CRUNCH: some bloody exception...
I just want to write a script that can display graphics without running Compiz to achieve it. Please help???

---

