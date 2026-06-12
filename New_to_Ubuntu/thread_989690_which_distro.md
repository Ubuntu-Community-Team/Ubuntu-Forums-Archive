---
title: "which distro?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by tyro12 on 2008-11-21
I'm just starting to use linux, and im wondering what distro has easy cuztomization, is not demanding, and still generally is powerful and looks good.

i have the following comp specs: 

- 256 mg ram
- 30 gigs hdd
- 800 MHz Pentium 2 (terrible i know)


so what can I do with this? (a friend of mine recommended "kubuntu," but i'm not sure)

thanks

---

### Post by Rokurosv on 2008-11-21
Perhaps Puppy Linux
[http://www.puppylinux.org/](http://www.puppylinux.org/)
It's very lightweight and perfect for old or not too powerful PCs, perhaps you could give that a try

---

### Post by doas777 on 2008-11-21
mabey DSL.
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by Dr Small on 2008-11-21
Nothing runs good on 256MBs of RAM and a 800MHz CPU.
But, you could try your hand at Fluxbuntu. For me, I would just install a bare-bones of Ubuntu (or ArchLinux) and build from there. Saves alot of load the CPU for installing, and you don't get all the bloat. But for you, just starting out with Linux, you probably don't want to go that route.

Let's just see what some of the other fellas think, first ;)

---

### Post by blendmaster on 2008-11-21
I'm going with [Xubuntu]("http://www.xubuntu.com/") on this one. :)

You can use all those choices, but in the end it comes down to personal preference.

---

### Post by oldos2er on 2008-11-21
Vector Linux Standard.

---

### Post by mikjp on 2008-11-22
* Vector 
* Zenwalk
* Debian

See my signature for more info.

Greetings,

mikko

---

### Post by mikjp on 2008-11-22
> **blendmaster said:**
> I'm going with [Xubuntu]("http://www.xubuntu.com/") on this one. :)

You can use all those choices, but in the end it comes down to personal preference.

Xubuntu is too much for 800 MHz / 256 Mb, at least it was too much for my 1 GHz CPU + 256 Mb.

Mikko

---

### Post by sbsaxman on 2008-11-26
Ok, here goes my first contribution to a Linux forum (whew!)

First: you're doing the right thing.  You'll find, with a little patience, that your machine can run a highly secure, highly productive OS, without too much fuss. 

I started with Xubuntu on my Pentium II, 300 MHz, 192 MB RAM, and what you get is a state-of-the-art operating system that automatically updates, and gives you a nice GUI to install free software written by some of the best programmers in the world!

What you don't get is blazing speed.  Xfce seems to have a lot of graphics overhead that (to this physics PHD) doesn't really add any value. Keep reading...though.

You can fix that nicely by playing with Xubuntu for a while (and numbing yourself to the delay), then installing a lighter-weight window manager.  I tried FVWM-Crystal, Fluxbox and ICEWM.  To install, just type "sudo apt-get install icewm".  If you go back-and forth to Windows machines, ICEWM will look most familiar, and it's very fast, so start there.  FVWM-Crystal is also very fast, and it comes with a suite of desktop menus installed, but it'll take some getting used to.  Fluxbox has its proponents; if my day was 28 hours long, I'd try to figure it out.  None of those window managers will see your Xubuntu applications (say, you've installed OpenOffice...) until you run "sudo apt-get menu" to get the Debian "menu" program that makes all your installed apps visible to all your window managers.

If all that sounds too daunting, try Puppy!  If all you need is an "appliance" (web browser, email, basic documents), and EASY-EASY-EASY, then you'll be up and running very quickly with Puppy.  Another very important advantage to Puppy is that it can install side-by-side with any other OS, including Windows, Xubuntu, whatever!  Just set your BIOS to boot from the CD first, save to the HD after you've configured machine-specific info (screen, keyboard, network...), then anytime you put that CD in and boot up, you're woofing along with puppy!  Version 4 is a nice improvement in look & feel over v.3.

In the end, on MY system:
Automatic hardware recognition: Puppy
Basic applications: Puppy
All the media formats you're used to in Windows, ready to go (mp3, Flash/YouTube): Puppy (get the "medibuntu" package to do this stuff in (x)ubuntu)
Regular security updates: (X)ubuntu
Snappiness: Puppy, tied with ICEWM/Xubuntu
Feels like a real OS, with real file structure, login, etc.: (X)Ubuntu (hands-down)
Variety of installable apps: (X)ubuntu (though be advised that a lot of these start calling processor-intensive graphics that might be out of your league).

My choice, going forward: Keep the Xubuntu installation updated with some regularity. Run ICEWM when I want to use Xubuntu to edit any documents (as I'm doing right now).  Run Puppy most of the time, and see how long till I get frustrated by its limitations... could be a while, though!

Good luck, and don't retire that P-II yet!

---

### Post by Junkieman on 2008-11-26
hi tyro, as blendmaster said it comes down to personal preferenece, your P2 isnt that bad actually, i have done some crazy stuff on low end machines, even running GUI OS'es on old 66 MHz with 4MB or RAM ;)

i cant mention any distributions that aren't already recommended, and great at that!

your system will work okay, but your bottleneck is just the memory since it will do a lot of paging to & from the swap (virtual memory stored on disk). 

see if you can increase the RAM - if you or anyone has an old memory module lying around. this would help immensely :biggrin:

---

### Post by Sorivenul on 2008-11-26
#1.) [Look at this Sticky]("http://ubuntuforums.org/showthread.php?t=575456")
#2.) Pick one that looks interesting and functional for you.

My suggestions, in order, on this one are:
DeLi
DSL
Puppy

---

### Post by j.miller565 on 2008-11-26
In my opinion, try out: 
Damn Small Linux (DSL)
Puppy Linux
SlaX
or Zenwalk

those distributions should run quite well on your system. Hope that helps

---

