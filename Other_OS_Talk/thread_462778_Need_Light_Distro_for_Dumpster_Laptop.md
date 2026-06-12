---
title: "Need Light Distro for Dumpster Laptop"
date: 2007-06-03
forum: Other OS Talk
---

### Post by Liniment on 2007-06-03
Earlier today I found a HP Laptop in a dumpster. No, I was not just randomly rummaging though dumpsters...I was walking to pick up a pizza and I saw a nice chair sticking out of a dumpster so I went over to check it out and then I found the laptop. Ok so I guess that could qualify as randomly rummaging, but whatever.

The laptop has a 850 mhz AMD processor, a 20 gig HD, and 128 megs of RAM. Right now it has XP installed on it but it is, as expected, horribly slow running on that little of RAM. I wanted to install Ubuntu on it, but I read that Feisty requires 256 megs of RAM minimum. So I went looking around on the web trying to find a small, fast, yet not too bare bones distro. I have read up on Puppy, MEPISLite, and DSL, but I can't decide which one I want and I was hoping someone here could help me.

The computer is bad, but its not horrible. Therefore I would like to use a nice looking window manager like Gnome or KDE, be able to run the newest Firefox, use Pidgin for chatting, be able to play movies/music, and use OpenOffice or something equally as good. First of all, is this realistic with having so little RAM? Second, if it is possible, which distro should I install. You can't boot from USB on it so I would like a distro that runs off the hard drive.

Thanks in advance!

---

### Post by kano on 2007-06-03
I'd take a look at Arch Linux :)

[http://www.archlinux.org/](http://www.archlinux.org/)

I'm not sure if you're going to get GNOME/KDE running smoothly though with only 128mb of ram regardless of distro...

---

### Post by Titus A Duxass on 2007-06-03
It's all down to your taste.
I would go with puppy.

It will run okay on that "old" laptop.

---

### Post by kerry_s on 2007-06-03
Wow, that's a nice find. I paid $50 for a vaio pcg-f430 450mhz 64ram 6gig hd, so of course i upgraded it, 256ram 20gig hd, total spent $125.

Anyways, to get the best performance you want to go custom. I'm running a custom debian-fluxbox install and this thing just flies. It took me a couple of weeks to learn the quirks of the laptop, so i could use the best settings, but i think i'm just about there. ;)

You should try learning how to use the net installer and build the machine to your needs.

Net-> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso)

xfce4-> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

Don't think about the evironment, just concentrate on getting it to do what you want, figure out what your needs are.

---

### Post by Liniment on 2007-06-03
To Kano: I can't seem to find the minimum requirements of Arch on the site...

To Kerry_S: Can you upgrade a laptops ram by yourself or do you have to take it to some place? Also, while I like the idea of a super fast, super clean OS customized just for my machine. I also am a very, very lazy man :D

Hmm...I also just read about Fluxbuntu ( [http://fluxbuntu.org/](http://fluxbuntu.org/) ). Perhaps I could use this. Has anyone here tried it?

---

### Post by kerry_s on 2007-06-03
Yes, i upgraded it myself, the hard part was the hard drive, this model has no hd access, i had to dismantle it to get to the hd under the keyboard in this kind of cage thing. When i bought it the old hd was dead already, so i had nothing to lose by trying, i was running dsl in ram with a usb key as the swap while i was shopping for the hd. ;)

---

### Post by kano on 2007-06-03
> **Liniment said:**
> To Kano: I can't seem to find the minimum requirements of Arch on the site...


Basically, all you need is an i686 processor and a way to install it. A 850MHz AMD processor is an Athlon T-Bird (most likely) which is i686.

Also, does the laptop have a net connection? Arch is all about the rolling-release thing, and having a network connection to keep it up to date is pretty much necessary, unless you want to be DLing packages with another computer and burning them to a CD every couple weeks :s

---

### Post by RAV TUX on 2007-06-03
> **Liniment said:**
> Earlier today I found a HP Laptop in a dumpster. No, I was not just randomly rummaging though dumpsters...I was walking to pick up a pizza and I saw a nice chair sticking out of a dumpster so I went over to check it out and then I found the laptop. Ok so I guess that could qualify as randomly rummaging, but whatever.

The laptop has a 850 mhz AMD processor, a 20 gig HD, and 128 megs of RAM. Right now it has XP installed on it but it is, as expected, horribly slow running on that little of RAM. I wanted to install Ubuntu on it, but I read that Feisty requires 256 megs of RAM minimum. So I went looking around on the web trying to find a small, fast, yet not too bare bones distro. I have read up on Puppy, MEPISLite, and DSL, but I can't decide which one I want and I was hoping someone here could help me.

The computer is bad, but its not horrible. Therefore I would like to use a nice looking window manager like Gnome or KDE, be able to run the newest Firefox, use Pidgin for chatting, be able to play movies/music, and use OpenOffice or something equally as good. First of all, is this realistic with having so little RAM? Second, if it is possible, which distro should I install. You can't boot from USB on it so I would like a distro that runs off the hard drive.

Thanks in advance!

try [**[B]Wolvix Cub**[/B]]("http://wolvix.org/").

---

### Post by Landser on 2007-06-03
Well, you can run XFCE with 128 MB of RAM... So you can try Xubuntu, you have to use the Alternate install CD though.

---

### Post by ugm6hr on 2007-06-03
> **Landser said:**
> Well, you can run XFCE with 128 MB of RAM... So you can try Xubuntu, you have to use the Alternate install CD though.

XFCE is as close to GNOME as you will get on this hardware.  So Xubuntu is a reasonable choice.

PuppyLinux is a very good choice, but I think it's an IceWM distro.  It tends to take slightly longer to boot (not sure why), but runs very quickly when loaded.

Both will allow you to do what you want, apart from run OpenOffice well.  I would recommend AbiWord / Gnumeric, and save OpenOffice for when you need it (e.g. presentations, higher power word processing etc).

---

### Post by happy-and-lost on 2007-06-03
Debian netinst + Fluxbox = SPEED

---

### Post by kerry_s on 2007-06-04
> **happy-and-lost said:**
> Debian netinst + Fluxbox = SPEED

Yep, that's why i use it. 
Have a question for you though, do you get alot of zombie processes? 
I seem to get alot, but now i use "and"(auto nice daemon) to kill them off by renicing them down.

---

### Post by Liniment on 2007-06-04
I have tried out Fluxbuntu and Puppy. Fluxbuntu was ok, but I think Fluxbox kinda looks like something a robot vomited up :) Puppy on the other hand is a good contender. It is really fast and lightweight and it seemed to be able to do most of what I wanted. 

I want to try Xubuntu as some of you have suggested, but the install disc is 685 meg and I only have a 650 meg CD-RW. Is it possible for me to trim out some files in the iso so that I can get it to fit? If so what files would you suggest?

---

### Post by kerry_s on 2007-06-04
Try the net installer, it can install any supported ubuntu-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by happy-and-lost on 2007-06-04
> **kerry_s said:**
> Yep, that's why i use it. 
Have a question for you though, do you get alot of zombie processes? 
I seem to get alot, but now i use "and"(auto nice daemon) to kill them off by renicing them down.

It's not a problem I've had. The occasional memory leak from XMMS and Xorg, and Iceweasel freezing (that's down to my Savage card, though). Then again, I don't have many processes running at any given time, I've tweaked it alot to get the most out of this box.

---

### Post by kerry_s on 2007-06-05
> **happy-and-lost said:**
> It's not a problem I've had. The occasional memory leak from XMMS and Xorg, and Iceweasel freezing (that's down to my Savage card, though). Then again, I don't have many processes running at any given time, I've tweaked it alot to get the most out of this box.

Thanks, i don't think it's processes, i'm running a custom install, nothing but the minimum. I switched out the apps that seem to zombie more and now it seems okay.

Pic, that's everything that's running->

---

