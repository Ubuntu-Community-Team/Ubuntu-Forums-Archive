---
title: "LiveUSB Install Won't Start"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-11-17
I just downloaded LiveUSB Install ([http://live.learnfree.eu/]("http://live.learnfree.eu/"), recommended by OMG! Ubuntu!) through the deb package, and installed the needed software through sudo apt-get install -f, but it won't start up. Any suggestions?

-DG

---

### Post by wolfen69 on 2011-11-17
Are you wanting to put ubuntu on a usb stick? Ubuntu comes with the startup disk creator. But the most reliable way *I've* found is to just use the dd command to make live usb sticks.

---

### Post by Jacobonbuntu on 2011-11-18
.....with Ubuntu indeed you can make a startup usb, works perfectly. You probably also have to change the bios settings to startup from the usb drive.

---

### Post by cbanakis on 2011-11-18
> **jacobonbuntu said:**
> .....with ubuntu indeed you can make a startup usb, works perfectly. You probably also have to change the bios settings to startup from the usb drive.
+1

---

### Post by nixblog on 2011-11-18
> **Jacobonbuntu said:**
> .....with Ubuntu indeed you can make a startup usb, works perfectly. You probably also have to change the bios settings to startup from the usb drive.

Most modern computers will have a function key dedicated to the task of displaying the BIOS boot menu options - f8 for my PC and f12 for my laptop but yours may differ.

---

### Post by Nixarter on 2011-11-18
Have you tried unetbootin? That's what I use.  A laptop of a friend of mine won't boot OS's from a live USB, regardless of settings.

Some other common keys for entering BIOS on startup (typically you just keep taping the button until the bios comes up): F2, Delete, space bar, escape.   There are others as well, but one of those mentioned so far will probably work.

---

### Post by prookie on 2011-11-18
> **doppel.ganger said:**
> I just downloaded LiveUSB Install ([http://live.learnfree.eu/]("http://live.learnfree.eu/"), recommended by OMG! Ubuntu!) through the deb package, and installed the needed software through sudo apt-get install -f, but it won't start up. Any suggestions?

I haven't tried to make bootable USB directly from Ubuntu, but I've used "Universal USB Installer" from:
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
and I've used UNetbootin from:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I had a problem that booting from USB failed on my desktop PC. The error was reported about configuration file. 
Is this similiar to your problem?

On the other hand, booting my laptop from the same USB passed successfully without any problems, and no matter which installer I've used.

---

### Post by doppel.ganger on 2011-11-23
Sorry if I sound impatient, but can you please help me run it?

---

### Post by doppel.ganger on 2011-11-23
Sorry, never mind, got it to work be reinstalling :)

---

