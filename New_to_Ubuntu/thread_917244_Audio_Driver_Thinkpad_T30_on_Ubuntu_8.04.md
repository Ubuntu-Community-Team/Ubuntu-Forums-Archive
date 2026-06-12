---
title: "Audio Driver Thinkpad T30 on Ubuntu 8.04"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by darkblueturbo on 2008-09-11
Hi there,
I'm an absolute beginner on Linux, having been living in a Windows world my entire life.
I came across a laptop, an IBM T30, that I wanted as just a browsing machine so I thought I'd try Ubuntu rather than a heft XP install.

So far it's going fine - had a nightmare getting the Netgear wireless card to work, but managed to sort it out in the end thanks to lots of Googling and searching these forums.

The only problem I have now is that I noticed today that there's no sound coming from the speakers when I tried to watch a video on YouTube (same deal with any CD's or MP3's).
I've done some more Googling and forum searching and have found things such as ALSA and OSS - however, I'm having lots of problems trying to install them*, and what am I meant to do when they are installed to find and install my drivers. 

HELP! I've been spoiled by .msi and .exe files you just click on and do everything 

* When running the 'config' script in a terminal for the ALSA install I get: configure:1678: error: C compiler cannot create executables
See `config.log' for more details.
I downloaded the .tar file for OSSv4 and extracted the files OK, but when trying to run sh /usr/lib/oss/build/install.sh, per the instructions, I get the message
cd: 9: can't cd to /usr/lib/oss/build
install.sh: 27: /usr/sbin/ossvermagic: not found
ln: creating symbolic link `/usr/lib/oss/objects': No such file or directory
ln: creating symbolic link `/usr/lib/oss/modules': No such file or directory
Error: OSS core module for NOREGPARM kernel are not available


I've also tried the rpm and deb files for OSSv4 but have other problems installing them as well. I'm a bit rubbish (whisper it quietly, but I work in IT!)

---

### Post by spiderbatdad on 2008-09-11
I have been using the same T30 for ubuntu distros since Breezy. I think it is a great machine for linux. I highly recommend Intrepid Ibex. You can get sound working in Hardy, but it is a pain with the present kernel. With intrepid it should work out of the box, as well as visual effect, if you want them. Do you boot your T30 with the options "lapic pci=routeirq" on the kernel line in /boot/grub/menu.lst?

If you want to get sound going in Hardy...I believe, open synaptic and take a look at the alsa packages...I installed 2 or three of the obvious ones...sorry I don't remember exactly which...not oss packages, anyway Alsa-common, etc. reboot, then set your sound options in system>>preferences to alsa or auto detect. Good luck.

---

### Post by darkblueturbo on 2008-09-12
Thank you spidery-chap :)

I'll give that a go this evening, still feeling my way around the OS, but the synaptic package manager is a good'un. I'll go from there and let you know how I get on.
If I have trouble, I'll give upgrade to Ibex a go - didn't realise it was released yet(!)

As for the boot options, I have no idea. I booted from the CD and installed everything with the standard setup.
If I'm not, should I be?

---

### Post by darkblueturbo on 2008-09-12
It works, it works, it works...

Thank you very much!!

---

### Post by eli_d on 2009-03-16
Just wanted to post another note for other users about T30 audio problems...

After upgrading to intrepid or installing some new updates (not sure which ones), my audio quit working.

I remedied the issue by opening up synaptic and doing a search for "alsa" ... I then right clicked on each package that was installed and clicked "mark for re-installation" ...


Audio is back!  Yippers!

---

### Post by tlois on 2009-03-30
Thanks, Eli!!  I have an old t30 that I use as a netbook (has a 10gb hard drive I salvaged when the other crashed and still is only half full- love that).  I had just let the lack of sound go lately- it used to work, I was thinking, but ok...

Just now too lazy to get up and go to another computer to watch a video on cnet, so found your post and back in business in my favorite chair.  Hooray!

Reinstalled all the Alsa stuff as you said, ctrl alt backspace, and the drums played on.


Editing to add the vid i was trying to watch, which makes me love love love my ubuntu even more!

[http://cnettv.cnet.com/2001-1_53-50005626.html?tag=TOCmoreStories.0](http://cnettv.cnet.com/2001-1_53-50005626.html?tag=TOCmoreStories.0)

---

