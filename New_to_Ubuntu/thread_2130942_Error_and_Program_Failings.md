---
title: "Error and Program Failings"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by Takamitsukai on 2013-03-31
Hi folks!

I'm excited to say I'm making the switch to ubuntu. I've been a lifelong Windows user and a Mac user at university. I've heard so many good things about linux that I simply HAD to try. I've recently installed 12.04 LTS and, unfortunately, have had nothing but problems. Few programs will open (some won't produce an error message). Luckily Terminal opens, but I've had no luck--things are "locked" or there is an error in processing. My Desktop doesn't show anything on it. My Wireless driver isn't being recognized. I'll go so far as to say that Ubuntu is not a functioning OS on my computer. Where do I start? What do you need from me in order to get this solved?

Specs:

Compaq Presario c500
dual boot with Vista
3 GB RAM
What other info is needed...

---

### Post by Bashing-om on 2013-03-31
Takamitsukai; Hi ! Welcome to the forum.

Dual booting with ubuntu is no big deal to accomplish IF one has made the prior preparations. ie Set aside space for ubuntu from the Windows' OS. May I suggest that you (re-)install ubuntu, after running ubuntu from the install medium in "try ubuntu" mode.
Documentation/tutorials:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Also (again) Prior Prudent Planning. Boot up the install medium -> "try ubuntu" mode; play with ubuntu insuring all devices work or indicating what problems you might encounter in the real (re-)install for some devices.

I would prefer to start a fresh as to work out probable corruptions in either/both operating systems.

Welcome to ubuntu also in particular.[INDENT=3]
just my opinion

[/INDENT]
[INDENT]
[/INDENT]

---

### Post by Takamitsukai on 2013-03-31
Ok. This will be my project on my next day off. ;) Thank you for the link, I will check it out and proceed accordingly. :)

---

### Post by Bashing-om on 2013-03-31
Takamitsukai;

Good thing. We will be here if you need any assistance.

See you here later.

---

### Post by Takamitsukai on 2013-04-02
Ok, so I've tested and reinstalled. Lots better. The link and advice really helped! Things are running as they should now...except wifi. Ever since I accidentally uninstalled it during the first install, my driver doesn't show up and and I've tried EVERYTHING to get it installed. Now what? I've tried the pre-installed broacom drivers and the b43 cutter. tried using synaptic to install and even tried manually installing through Terminal--no go. It's not a big deal for now, but I have no sound.

---

### Post by ManamiVixen on 2013-04-02
I looked up your Laptop's Sound chip and it dosen't look good. The chip found in the Presario c500 is only used in the c500 and is one of those specialty chips for better-than-average sound. Since this is a unique chip and is only found in this laptop, support is likely non-existent from ALSA, the audio sub system in linux that controls sound and sound drivers.

There is one shot, try the headphone jack, see if that works. Some laptops on linux cannot use their built-in speakers but the jack works.

---

