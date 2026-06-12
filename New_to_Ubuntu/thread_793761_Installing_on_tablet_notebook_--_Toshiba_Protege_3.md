---
title: "Installing on tablet notebook -- Toshiba Protege 3505"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by tyronenguyen on 2008-05-14
I'm trying to install Xubuntu on a Toshiba Protege 3505.  I've read numerous threads that seem to indicate that people have no issues installing Ubuntu on this laptop.  But, I am having issues.

I also tried Ubuntu install, but that gives me the same error.

This is a screenshot of the portion of the install where it hangs:

[IMG]http://i25.tinypic.com/2vxotna.gif[/IMG]
[http://tinypic.com/view.php?pic=2vxotna&s=3](http://tinypic.com/view.php?pic=2vxotna&s=3)

I have used noacpi and pci=noacpi, noapic, acpi=force and the install always hangs there.

The numbers in the square brackets seem to change between the different options though.  

Can someone shed some light on my issue?  Maybe I'm not waiting long enough?  I'll let it hang there overnight and see if it magically unhangs itself.

---

### Post by bjm1904 on 2008-05-14
Judging by the message it hangs on, are you sure it isn't down to your hardware (i.e. your RAM?). If Windows worked fine with it before, then great, but if you've messed about under the hood, then that may be your problem.

Try using the latest version of your distro if at all possible - and by the looks of it the 'alternate CD' might be more up your alley - can you say how much RAM you have - if it's 256MB or less, then that would explain it (as the graphical installers tend to need more than that)

---

### Post by tyronenguyen on 2008-05-14
> **bjm1904 said:**
> Judging by the message it hangs on, are you sure it isn't down to your hardware (i.e. your RAM?). If Windows worked fine with it before, then great, but if you've messed about under the hood, then that may be your problem.

Try using the latest version of your distro if at all possible - and by the looks of it the 'alternate CD' might be more up your alley - can you say how much RAM you have - if it's 256MB or less, then that would explain it (as the graphical installers tend to need more than that)

I ran the memtest to 48% and I figured that it meant my RAM was probably good.  I'll run it overnight to 100% and see if I get any errors.

It did run winxp before.  I would think 512MB p3-1.3Ghz would be OK to run the GUI Xubuntu install since my 256MB p2-266Mhz thinkpad ran the GUI just fine.

---

### Post by tyronenguyen on 2008-05-15
Well, I installed winxp on it w/o any trouble.  What to do.. what to do...

---

### Post by tyronenguyen on 2008-05-15
> **tyronenguyen said:**
> Well, I installed winxp on it w/o any trouble.  What to do.. what to do...

Well, I finally got xubuntu installed.

I follow a guide on how to install ubuntu by installing grub, the ubuntu boot loader, and the .iso of the install cd.

grub started up and took me to ubuntu install, but there was never an option to install off the .iso on the hd.  So, I plugged in my pcmcia dongled dvdrom and installed off that.

What I guess the original problem was with the pcmcia dvdrom?  Maybe if you disconnect it before you hit "install xubuntu", and then plug it back in when it asks you for the cdrom, that would work.

Well, now to figure out how to get wpa working with my orinoco_cs driver... "it just works"... maybe in the future.

---

