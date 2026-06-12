---
title: "Desktop livecd issues."
date: 2011-06-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by philinux on 2011-06-13
I just burned the daily live desktop for a clean reinstall. 
Get to login screen and only unity 2d will load. Gnome says failed to load gnome session. Ubuntu option hangs 

Also once in 2d my partitions are inaccessible.  No permissions. Gksudo nautilus crashed put to tty. 

I know its alpha but anyone else seeing this.

NVIDIA 8600GT.

---

### Post by Harry33 on 2011-06-13
> **philinux said:**
> I just burned the daily live desktop for a clean reinstall. 
Get to login screen and only unity 2d will load. Gnome says failed to load gnome session. Ubuntu option hangs 

Also once in 2d my partitions are inaccessible.  No permissions. Gksudo nautilus crashed put to tty. 

I know its alpha but anyone else seeing this.

NVIDIA 8600GT.

You obviously have nvidia-current installed?

---

### Post by philinux on 2011-06-13
> **Harry33 said:**
> You obviously have nvidia-current installed?

No, this is booting the livecd prior to reinstall.

---

### Post by Harry33 on 2011-06-13
> **philinux said:**
> No, this is booting the livecd prior to reinstall.

So it is xserver-xorg-video-nouveau then.
That may be the reason for non-3D.

However, it does not explain the permission issue nor the root nautilus crash.

---

### Post by philinux on 2011-06-13
> **Harry33 said:**
> So it is xserver-xorg-video-nouveau then.
That may be the reason for non-3D.

However, it does not explain the permission issue nor the root nautilus crash.

I guess nouveau might explain lack of unity 3d. Gnome session ain't sure.
Plan is to wipe existing data from natty now and reinstall. Go from there. :p

I'll run the livecd and try to bug report from there first.

---

### Post by mc4man on 2011-06-13
It's likely that gksudo nautilus fails on the live session because it can't write to/create /root/.config/
The way around that is to use  a root gedit to create and save a file, then /root/.config/ is created and gksudo nautilus will then work

(- with supported nvidia adapters unity 3d works on the live session after installing the mesa3d lib and a logout/in

---

### Post by jerrylamos on 2011-06-13
Some place I read that 2D was default on the live CD because that's what support is on the CD.  3D uses up gobs of CD space (and processor cycles).  

Actually here, live gives me a choice of Ubuntu and Ubuntu 2D.  I always choose the latter since Alpha's are flaky enough without getting into all that (infamously buggy) Compiz stuff.

Jerry

---

### Post by jerrylamos on 2011-06-13
13 June 32 bit Live up and running here, wired internet.  I'll see if it does wireless tomorrow.

Famous last words, no crashes yet....

Jerry

---

### Post by coffeecat on 2011-06-14
> **jerrylamos said:**
> Some place I read that 2D was default on the live CD because that's what support is on the CD.  3D uses up gobs of CD space (and processor cycles). 

Where did you read that? I think that whoever wrote that was misunderstanding something.

I can get the 13th June 32-bit desktop ISO to boot into 3d Unity. That's on a machine with an ATI Radeon HD4350 which has given me good compiz with the default open source driver since Lucid. Rather unexpectedly, it booted to the login screen, which doesn't seem right. You have to know that the live "ubuntu" account has a blank password. First time I absent-mindedly entered my usual installed password and was dumped to a virtual console.

I'll try the ISO on another machine with Intel graphics that runs 3d Unity later.

**EDIT**: that above was with the ISO written to a USB. Out of interest I burnt the ISO to a DVD-RW and booted with that. I still get taken to the login screen, and I can still login to 3d Unity on the same machine.

---

### Post by philinux on 2011-06-14
I gave up on testing the livecd it kept crashing to tty so just installed.

Next!!!

Had to use gksu gedit to get gksu nautilus to work. And Jockey says "You are not authorised to perform this action". 

So that was gksu jockey-gtk to get that sorted lol.

---

### Post by coffeecat on 2011-06-14
> **philinux said:**
> I gave up on testing the livecd it kept crashing to tty so just installed.

I didn't even get that far! It booted up OK on my laptop with Intel graphics and even gave me 3d Unity, but crashed to a tty after I'd opened two nautilus windows. So I rebooted and once back in Unity opened a terminal to check which partition I wanted to install to and it promptly crashed to a tty again - I hadn't even finished typing "sudo".

I'll try logging into 2d Unity. Perhaps that'll be more stable.

**EDIT**: Nope. Unity 2d collapsed just as quickly when I opened a terminal.

But some good news: "sudo shutdown -h now" works as expected from the tty. :lol:

---

### Post by jerrylamos on 2011-06-14
14 June 3.0-0-generic 32 bit Live up and running.  nm applet crashed connecting to wireless, ifconfig wlan0 crashed lightdm.  

lightdm stop & start, logged in, used BFB selected Network to connect to wireless O.k.  Yes I filed a launchpad bug #797167.

Hmmm.

Jerry

---

### Post by shuttleworthwannabe on 2011-06-14
I had the exact same issue used the Desktop 10 June 2011 build--on 12 June install (there were no recent builds). I just abadoned the process was not in the mood to troubleshoot late at night. Hardware also has nvdia card (dell vostro 3700).

---

### Post by jerrylamos on 2011-06-14
Date-Time also crashes on 14 June daily build Live, either from the destop applet or from the BFB icon selection.  Launchpad bug #797287. I just set the time zone from command line but the top panel is still 4 hours off.  I'll see next time I reboot.

Jerry

---

### Post by sparker256 on 2011-06-14
> **jerrylamos said:**
> Date-Time also crashes on 14 June daily build Live, either from the destop applet or from the BFB icon selection.  Launchpad bug #797287. I just set the time zone from command line but the top panel is still 4 hours off.  I'll see next time I reboot.

Jerry
Logout and back in should fix that. It did on my live USB for the 14th.

Bill

---

### Post by CreativeReach on 2011-06-14
Is fall back for gnome on the cd at all?

---

### Post by cariboo on 2011-06-14
For those of you that use Tomboy, it is being dropped from the Live CD until it is updated to GTK-3, it will still be available from the repositories, it just won't be installed by default.

> Hi,

During the desktop team meeting today we discussed deprecated libs and
CD space, tomboy is keeping libgnome, libgnomeui, libbonobo,
libbonoboui, libgnomecanvas on the CD in oneiric and will until upstream
switches to gsettings which seems to have no mono bindings yet. 

Since that work has been stalling for a while, we need CD space and we
want to get ride of the deprecated library we decided during the meeting
to drop tomboy from the CD at least until it's ported to gsettings.
Tomboy will still be easily installable and will not get away for users
upgrading, that will just concern new installation during the oneiric
unstable cycle.

There will probably be other discussions about tradeoffs we can make in
the default installation in the next weeks as well since we are short on
CD space still and some of changes planned for this cycle didn't land
yet.


---

