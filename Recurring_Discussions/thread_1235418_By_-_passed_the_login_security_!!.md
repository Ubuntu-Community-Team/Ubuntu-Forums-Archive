---
title: "By - passed the login security !!?"
date: 2009-08-09
forum: Recurring Discussions
---

### Post by crystaldart on 2009-08-09
[FONT=Arial]Hai Friends,

How safe is Linux Login password?

In Windows  there are many ways to go around or reset the login password. Is it possible in UBUNTU 8.1 Linux ?

BCoz, at my office, when I go out I use Lock Screen Option, which prompt for a password to login again. A friend of mine ( I guess so :(..) somehow got in. :confused:

Is there any such tweaks for Linux to get in , may be through boot?  If yes, How can I make it Secure ?

I am in some real concern. Please provide me a solution.

Thank you all.
[/FONT]

---

### Post by TuckLive on 2009-08-09
> **crystaldart said:**
> Is there any such tweaks for Linux to get in , may be through boot?

If he has physical access to the computer, then a livecd will gain him access.  If this computer has personal or confidential information it needs to be locked up to where you only have physical access.  This is not a Linux problem, but all computers.

---

### Post by aysiu on 2009-08-09
Physical access is root access. It doesn't matter if you're using Ubuntu, Windows, or Mac OS X.

If you want to foil this co-worker, then lock your computer behind a door (leaving the monitor, keyboard, and mouse still out, of course), remove the recovery mode entry from Grub and add a Grub password, set your BIOS to disable booting from CD and USB, and add a BIOS password.

---

### Post by saulgoode on 2009-08-09
> **crystaldart said:**
> [FONT=Arial]Is there any such tweaks for Linux to get in , may be through boot?  If yes, How can I make it Secure ?

I am in some real concern. Please provide me a solution.[/FONT]
You will need to modify your BIOS so that it can not boot from any removable devices. You will then need to password protect your BIOS so that nobody can change your settings (do NOT forget your BIOS password). 

You will also need to set up GRUB so that a password is required to enter "rescue" mode and to boot with alternate kernel parameters.

---

### Post by drbin on 2009-08-09
> **aysiu said:**
> Physical access is root access. It doesn't matter if you're using Ubuntu, Windows, or Mac OS X.

If you want to foil this co-worker, then lock your computer behind a door (leaving the monitor, keyboard, and mouse still out, of course), remove the recovery mode entry from Grub and add a Grub password, set your BIOS to disable booting from CD and USB, and add a BIOS password.

or any other OS, at any orange book classification of security if I may add.
The good thing is that users don't know it or how, so systems are pretty safe (from a users point of view)

---

### Post by crystaldart on 2009-08-10
Thank friends. It gives some relief.

Can you please tip me as to how to Password protect the Grub?.

---

### Post by aysiu on 2009-08-10
> **crystaldart said:**
> Thank friends. It gives some relief.

Can you please tip me as to how to Password protect the Grub?. Install StartUpManager:
[http://psychocats.net/ubuntu/startupmanager](http://psychocats.net/ubuntu/startupmanager)

Then click on the security tab (see attached screenshot)

---

### Post by Bodsda on 2009-08-10
> **aysiu said:**
> Install StartUpManager:
[http://psychocats.net/ubuntu/startupmanager](http://psychocats.net/ubuntu/startupmanager)

Then click on the security tab (see attached screenshot)

Does that edit the menu.lst or some other configuration file?

Regards,
Bodsda

---

### Post by crystaldart on 2009-08-10
> **aysiu said:**
> Install StartUpManager:
[http://psychocats.net/ubuntu/startupmanager](http://psychocats.net/ubuntu/startupmanager)

Then click on the security tab (see attached screenshot)


But I searched for Start Up Manager in from Applications > Add/Remov (after following you link). There is no start up Manager there. :(

From some references on this topic, it's mentioned that you may not find Start Up manager on all versions. Is it true?

How can I install them from debian files? Is there any compactability issues or error using this?

Thank you again for your prompt help

---

### Post by aysiu on 2009-08-10
[All supported releases have StartUpManager in the Universe repositories.](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=startupmanager)

So if you're using 8.04, 8.10, or 9.04, StartUpManager's in there. If you're using 7.10 or 7.04, your release no longer even gets security updates, so you should upgrade to a newer version.

To make sure you have the Universe repositories enabled, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by crystaldart on 2009-08-12
> **aysiu said:**
> [All supported releases have StartUpManager in the Universe repositories.]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=startupmanager")

So if you're using 8.04, 8.10, or 9.04, StartUpManager's in there. If you're using 7.10 or 7.04, your release no longer even gets security updates, so you should upgrade to a newer version.

To make sure you have the Universe repositories enabled, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Ok, but I could'nt, for some reason, find the Startup Manager in the Universal Repositories.

I installed it manually through the terminal. Its doing good now.

But, Thanks for you helping hands.

---

### Post by Simian Man on 2009-08-12
Just slap him and tell him not to do that again :).

---

### Post by hoppipolla on 2009-08-14
> **TuckLive said:**
> If he has physical access to the computer, then a livecd will gain him access.  If this computer has personal or confidential information it needs to be locked up to where you only have physical access.  This is not a Linux problem, but all computers.

or you could just encrypt the filesystem. :)


Oh, and yeah a password on GRUB is a cool idea, but it will make no difference to a live CD/USB ._.

Sticking a pass on BIOS is also a good idea as saulgoode said, then he would have to actually open the PC and reset the CMOS to use his live device if you omitted or dropped it lower in the boot order ^_^

---

