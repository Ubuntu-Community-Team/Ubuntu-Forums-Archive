---
title: "Anyone else tried PCLinuxOS Gnome?"
date: 2008-01-06
forum: Other OS Talk
---

### Post by 67GTA on 2008-01-06
I was playing with the live cd today, and I have to say that I'm impressed. I tried PCLinuxOS KDE when 2007 first went final. I could not keep Kwin from crashing, and the windows would always go off the screen(very buggy). I have always used Kubuntu. The new Gnome remaster is pretty nice. The live cd is very responsive. I don't care for the boot, login or splash screen. They are pretty ugly. The menus are not hacked up like with the KDE version. They kept the Gnome menu. Synaptic seemed a little faster also. It was painfully slow in  the KDE version. It still has the Mandriva Control Center along with the Gnome control center. If you liked PCLinuxOS, but dislike KDE, you should try it out.

---

### Post by kamaboko on 2008-01-06
I tossed it on a Compaq V6000 laptop two days ago for my dad.  I think it's a great distro except for one thing: Broadcom 1390 WiFi support.  I'm still trying to solve the problem.  This is the deal. I can get it connected to the Internet, but when I restart the computer, I have to go into network settings and reconnect it again.  I've tried several different options but it all comes down to the same thing: reconnect.  I just told my dad not to turn his laptop off.  

I like the computer management console.  The OS in general seems pretty responsive as well.  It also connected to my dad's WiFi HP printer...a big plus and I didn't have to fiddle around with it very much to do it either.

---

### Post by new2*buntu on 2008-01-06
I also played with it for a while, and thought it was nice, but I found that there was much more included with it than I needed, and APT/Synaptic were *much* slower than the Debian counterparts. I don't know why, but it just is slower than Debian (and every distro based off Debian). Just my 2 cents.

---

### Post by 67GTA on 2008-01-06
> **kamaboko said:**
> I tossed it on a Compaq V6000 laptop two days ago for my dad.  I think it's a great distro except for one thing: Broadcom 1390 WiFi support.  I'm still trying to solve the problem.  This is the deal. I can get it connected to the Internet, but when I restart the computer, I have to go into network settings and reconnect it again.  I've tried several different options but it all comes down to the same thing: reconnect.  I just told my dad not to turn his laptop off.  

I like the computer management console.  The OS in general seems pretty responsive as well.  It also connected to my dad's WiFi HP printer...a big plus and I didn't have to fiddle around with it very much to do it either.


You may have to add the needed module to start at boot time. PCLinuxOS has always came with a minimal kernel. I had to add the ndiswrapper module to start at boot for my freind's laptop because of the same problem.

---

### Post by 67GTA on 2008-01-06
> **new2*buntu said:**
> I also played with it for a while, and thought it was nice, but I found that there was much more included with it than I needed, and APT/Synaptic were *much* slower than the Debian counterparts. I don't know why, but it just is slower than Debian (and every distro based off Debian). Just my 2 cents.

It has always been slower than Debian, but it seems faster now than the KDE version. I guess the rpm's slow it down:lolflag:

---

### Post by 67GTA on 2008-01-06
I just found one flaw. No MP3 Nautilus preview out of the box(dang'it)

---

### Post by blooboy on 2008-01-28
Hi !

Can the Ubuntu & PCLOS  packages be shared with each other  ??

---

### Post by p_quarles on 2008-01-28
> **blooboy said:**
> Hi !

Can the Ubuntu & PCLOS  packages be shared with each other  ??
Technically, you could probably get most packages for one working on the other platform. It would take a lot of work, though, and you'd be risking an unstable system. There are much better ways of installing applications that are unavailable in the repos than mixing package types.

---

### Post by blooboy on 2008-01-28
> **p_quarles said:**
> Technically, you could probably get most packages for one working on the other platform. It would take a lot of work, though, and you'd be risking an unstable system. There are much better ways of installing applications that are unavailable in the repos than mixing package types.

The main reason I am sticking to Ubuntu 7.10 is that it has the most wonderful 'Aptoncd' to create offline repo cd/dvd. 

This really helps people like us who have broadband connection at Office and no connection at their home PCs. I'm not sure if PCLOS Gnome has got similar feature.

---

### Post by p_quarles on 2008-01-28
I'm not aware of anything similar to apt-on-cd for RPMs, though there may be something.

May I ask what interests you about PCLOS? If you're looking for something KDE-centric, but that's also compatible with with apt-on-cd, there are several options.

---

### Post by blooboy on 2008-01-28
> **p_quarles said:**
> I'm not aware of anything similar to apt-on-cd for RPMs, though there may be something.

May I ask what interests you about PCLOS? If you're looking for something KDE-centric, but that's also compatible with with apt-on-cd, there are several options.

Buddy I am not talking about KDE version of PCLOS, its the new Gnome version I am talking about. I have 2 HDDS in my PC, one with Ubuntu and other with PCLOS (KDE). I just wanted to enquire if the aptoncd disk I've made on my Ubuntu works with PCLOS Gnome or not. I dont want to install PCLOS Gnome over PCLOS KDE if the files are not compatible with Gutsy.

---

