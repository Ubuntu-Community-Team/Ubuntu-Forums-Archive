---
title: "Grub Customizer Error"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by mesanomad on 2014-01-01
I'm very new to Ubuntu have been trying for days to make Ubuntu 13.04 my default OS, rather than Chrome OS.  Finally gave Grub Customizer a try and got the following error...

"Please Inform the author about this problem. The following information could be helpful: exception '9Exception' with message 'grub cfg dir not found' in /build/buildd/grub-customizer-4.0.3/src/Model/ListCfg.cpp:116"

Hopefully someone can help.  Thanks.

Steve

:confused:

---

### Post by grahammechanical on 2014-01-01
Was Chrome OS pre-installed? What are your machine's specifications? I can offer advice for machines with the old BIOS boot system but I would not make a suggestion regarding machines with the newer UEFI boot system.

Do you get a Grub menu? On machines with the BIOS boot system and Linux operating systems using Grub as the boot menu there are some general principles. Such as, the last installed Linux OS puts its Grub into the MBR and its Linux at the top of the Grub menu. Another principle is, to put a particular Linux OS at the top of the Grub menu load into that Linux OS (Ubuntu) and run two commands to re-configure Grub and re-write the Grub menu and that will put that particular Linux OS at the top of the Grub menu.

I have used these two commands myself because I have several installs of Ubuntu and I like a certain version to be the default. I also have a machine with a BIOS boot system. I hesitate to tell you the commands because I have no experience of running these commands on a machine with a UEFI boot system. I also have no experience of Chrome OS.

Regards.

---

### Post by mesanomad on 2014-01-01
It is an Acer C710 Chromebook.  I am truly a beginner, and while good with computers, a lot of what you are discussing above...I just don't know.  I've tried to look up your question about the boot system, but I can't answer for certain.  Do I get a grub menu?  I understand the premise behind a grub menu, but don't know how to find or work with it.  I appreciate the reply and could likely fix this with the right help.  Thanks!

---

### Post by mesanomad on 2014-01-02
Starting to feel like I've lost data at some point.  Anything having to do with grub seems to not exist.  Or I just don't know how to find it.  "Command not found" seems to be a regular occurrence in the terminal.

---

### Post by Bucky Ball on 2014-01-02
So you are booting with Grub at the moment? How are you installing Grub Customizer and at what point are you getting that error? If you are attempting to compile, you could be using a PPA.

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

Get into your BIOS (re. grahammechanical's post) and have a look in there for anything that might refer to UEFI, GPT boot. Chromebook might be fiddling somehow with the boot sequence or startup (never used it so unsure). Chromebook was preinstalled? Then that might be UEFI. Tried 13.10? It might cope better and is upgradeable to the next long-term support release 14.04 LTS next April.

You would have explored the BIOS to get the machine to boot from disk or whatever you installed from so presuming you know how to have a look.

If you want to attach a screenshot of Gparted that will show us your partitions ('Go Advanced'>paperclip icon>attach screenshot).  Better still, run [Bootinfo.script](Bootinfo.script) and post the result.

---

### Post by mruiz408 on 2014-01-02
If all you did was try to install grub, you should not have lost data. If you tried to install ubuntu and repartitioned your HD then you are out of luck. GRUB us kind of tricky to install in my experience. I just fixed my GRUB installation that got corrupted by inserting a Live CD of ubuntu, clicking TRY UBUNTU (don't install it lol), going to terminal and getting a program called Boot-Repair.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
It is the best method of installing GRUB that I know, I can never get things going with a GRUB CD or even editing the entries from Terminal. Good luck!

---

