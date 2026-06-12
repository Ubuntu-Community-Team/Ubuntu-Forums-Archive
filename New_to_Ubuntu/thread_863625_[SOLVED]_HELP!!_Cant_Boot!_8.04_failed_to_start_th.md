---
title: "[SOLVED] HELP!! Cant Boot! 8.04 failed to start the x server"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Jimtuv on 2008-07-18
I have been running Ubuntu 8.04 for a couple months with very little problem. Today I was adding the package Virtualbox ose and it said that it needed other files I went into the synaptic package manager and searched for the file it requested and marked it for installation. After installing the system asked for a reboot. Now when booting it stops at a screen that says Failed to start the x server.

What do I do? can I reverse whatever the synaptic package manager did? Please help I am really new to all this and haven't a clue what to do next.

---

### Post by waspbr on 2008-07-18
hmmm
don't worry, this is probably fixable. first thing I would do would be to selected the recovery boot mode from grub right at the begining. there you can choose for fix your xorg, after you do that it may be also a good idea to check for any broken packages, select the option that fixes broken packages.

let us know how that goes

---

### Post by Jimtuv on 2008-07-18
Thanks for the quick answer. I am going to try that right now. I will let you know how it goes.

---

### Post by Jimtuv on 2008-07-18
I am in now. I am not sure what I should do next to make sure there is no real damage. Should I uninstall the virtual box? Or is that asking for trouble?

---

### Post by Jimtuv on 2008-07-18
I am going to reboot to make sure it worked.

---

### Post by Jimtuv on 2008-07-18
Ok I can boot and log in and out. It trashed all my compiz settings

---

### Post by cwmoser on 2008-07-18
That reminds me -- I have in the past had trouble with xorg.conf.

So, I've made a backup copy of my file:

cd /etc/X11
sudo cp xorg.conf  xorg.conf.SAVE.18July2008


Carl

---

### Post by Jimtuv on 2008-07-18
I did too but every time I copy it back to be the xorg.conf it gives me that same error failed to start x-server and I have to rebuild it.

---

### Post by Jimtuv on 2008-07-18
The nvidia kernel is failing to load. Not sure what to do about it. Any time I try to restore my backup of the xorg.conf the x-server gives that error.

---

### Post by Jimtuv on 2008-07-18
My sound is toasted as well. what do I do?????

---

### Post by Jimtuv on 2008-07-18
I am totally lost here. I tried reinstalling the nvidia drivers but have no clue what I am doing. Everytime I try anything I end up with that failed to start x-server and I have to go to recovery mode and fix it. which undo's everything I did. I can't restore my backup xorg.conf file everything I do sends me back to the same problem. I am ready to toast the whole thing!!!!

---

### Post by sdowney717 on 2008-07-18
weird.
Try installing ENVY for the drivers
at a terminal prompt you can type 
envy -t  for text mode. It will install the proprietary drivers and automatically reconfigure xorg.

If all you get to is a command prompt. You can type in
sudo apt-get install envy

---

### Post by Jimtuv on 2008-07-18
I think the virtualbox hosed my kernel. 

This is what I installed virtualbox-ose-guest module for linux-image-2.6.24-19-generic 

Can I reinstall my Linux kernel? Is there a way to test it with out to much trouble?

---

### Post by Jimtuv on 2008-07-18
> **sdowney717 said:**
> weird.
Try installing ENVY for the drivers
at a terminal prompt you can type 
envy -t  for text mode. It will install the proprietary drivers and automatically reconfigure xorg.

If all you get to is a command prompt. You can type in
sudo apt-get install envy

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package envy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  envyng-core envyng-qt envyng-gtk
E: Package envy has no installation candidate

---

### Post by sdowney717 on 2008-07-18
oh, yes it is now called envyng!

---

### Post by Jimtuv on 2008-07-18
That got the video working again. Now all I have left is the sound to fix (I think)

---

### Post by Jimtuv on 2008-07-18
Ive done the aplay -l and got No sound card 

Then I did lspci -v and got

02:03.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
	Subsystem: Creative Labs SBLive! Player 5.1
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at b800 [size=32]
	Capabilities: <access denied>

so Ubuntu can detect it.

 modprobe snd-emu10k1
FATAL: Module snd_emu10k1 not found.
FATAL: Error running install command for snd_emu10k1

don't have a clue what to do next. It seems to be missing the driver.

 modinfo soundcore
filename:       /lib/modules/2.6.24-19-386/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.24-19-386 mod_unload 486 

It's in the kernel. not sure where to go next

---

### Post by Jimtuv on 2008-07-18
I fixed the sound by doing the following.

Please be sure all needed kernel modules are installed to make this check and install them:
Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r)

give your user password when requested, you don't see nothing when you type it, then press enter.

Then reboot your pc.

Now I think I understand what happened. The install of that virtual kernel must have knocked out one of the kernel modules and by doing that last command it was replaced.

Now I think I can call this Solved.

---

