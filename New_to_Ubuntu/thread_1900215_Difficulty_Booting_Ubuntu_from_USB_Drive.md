---
title: "Difficulty Booting Ubuntu from USB Drive"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by WKID on 2011-12-25
I just received Ubuntu 11.10 on USB drive in the mail a few days ago. I used it several times on my computer, without issue, by pressing F11 when the computer starts prior to loading Windows. I was just running the Live USB function; I didn't install Ubuntu. 

Yesterday, when I tried to shut down my computer from within Ubuntu, nothing happened. It just sat there, so I ended up shutting down by holding down the power button.

Today I loaded Ubuntu in the same manner. It stayed on the boot screen and never got to the menu to choose to install or to try it out. The following message was displayed under the Ubuntu emblem:

**Waiting for network configuration...**

A while later, the following displayed:

[B]Unattended-upgrade in progress during shutdown, sleeping for 5s

[/B]It remained on this message for a long while before switching to what appeared to be a command line. The final line was this:

**ubuntu@ubuntu:~$**

There was a place to input something afterward. I'm not sure what I was supposed to input.

I cannot get Ubuntu to load.

Any help solving this issue would be much appreciated.

Thanks a lot,
Caleb

---

### Post by lsemmens on 2011-12-25
It looks like your BIOS is trying to boot from a network, you may need to modify the boot order in BIOS to set your USB device to boot first.

As for the unattended upgrade bit, are you certain you did not select the option to install Ubuntu onto your computer?

Do you know how to get into BIOS?
What sort of machine are we talking about?

---

### Post by WKID on 2011-12-27
[INDENT]*"It looks like your BIOS is trying to boot from a network, you may need to modify the boot order in BIOS to set your USB device to boot first."*
[/INDENT]This message displayed after the USB had already booted. It was on the Ubuntu boot screen.
[INDENT]*"As for the unattended upgrade bit, are you certain you did not select the option to install Ubuntu onto your computer?"*
[/INDENT]I am sure. I have been using the try it function and running Ubuntu off of the USB. The USB does have the persisting between boots feature, if that matters.
[INDENT]*"Do you know how to get into BIOS?"*
[/INDENT]No[INDENT]*"What sort of machine are we talking about?"*
[/INDENT]It's a SONY Vaio laptop Model: PCG-71911L 
with Windows 7 Home Premium SP1, 
500GB Hard Drive, 
4GB RAM

Thanks a lot.

[I][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][/I]

---

### Post by ashok.ericsson on 2011-12-28
hi all,
I am having the same problem. My system is HP Elitebook 2540p. I tried with different 8 GB flash drives (Transcend, sandisk, kingston). All same problem, I downloaded the ISO twice, MD5 is ok. Used Universal USB installer. What could be the problem? Need help urgently as some of network testing tool i planned to use for my work runs in linux only. Now I am stuck.

---

