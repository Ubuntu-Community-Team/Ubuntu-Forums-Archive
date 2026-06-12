---
title: "KDE distros that include proprietary stuff?"
date: 2007-05-28
forum: Other OS Talk
---

### Post by 67GTA on 2007-05-28
I have been on a mission to find a KDE distro that includes codecs,browser plugins,graphics drivers,etc. I have tried so far:
PCLinuxOS(liked it but keeps crashing)
Sabayon(didn't care for emerge/portage)
Sidux(based on debian, no non-free stuff included)
Mandriva(don't like it)
Knoppix(same as sidux)
Opensuse(didn't like package manager, graphics driver was a pain to install)

I saw that Linux Mint had a KDE desktop version, but is not fully developed yet. I also looked at Arch, but no non-free stuff. I know I can install everything myself, but it was really nice to have them already setup as with PCLinuxOS and Sabayon. Am I out of luck?

---

### Post by 67GTA on 2007-05-28
I was also wondering if I made another Feisty partition and used the commands on Psychocats tutorial [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde) to remove gnome and install kde will I have Kubuntu or something different? Would it be a pure KDE base on top of Ubuntu? Will it even work that way?

---

### Post by aysiu on 2007-05-28
Mepis has a lot of non-free stuff included.

And Linux Mint's KDE version is fully developed:
[http://linuxmint.com/20070420.html](http://linuxmint.com/20070420.html)

If you install KDE with Psychocats and use "pure KDE" from Psychocats, you will, in fact, have Kubuntu. Is that what you want? Kubuntu won't have all the non-free/proprietary stuff.

---

### Post by 67GTA on 2007-05-28
I didn't think Linux Mint KDE was ready yet. The last time I checked they were still trying to finish porting it. I will look again. Actually, I have tried Kubuntu since I loved Ubuntu so much, and knew how to get the proprietary stuff easily, but did not like the mods they made to it. I may try it again when 7.10 comes out. Have you tried Mepis?

---

### Post by aysiu on 2007-05-28
I used Mepis two years ago for about a month, and it was pretty good. In some ways, it's ahead of Ubuntu in terms of features (easy Grub reinstallation, easy and *reliable* partition and drive mounting). Now, it's based on Ubuntu and uses Ubuntu repositories, so the major differences between the two are the default applications and the use of root v. sudo.

---

### Post by meng on 2007-05-28
I tried MEPIS 2 weeks ago and it was fine from a multimedia/plugins standpoint.

---

### Post by 67GTA on 2007-05-28
Do Mint or Mepis have the graphics driver installed by default?

---

### Post by aysiu on 2007-05-28
Mepis has Nvidia and ATI. I don't know about Mint.

---

### Post by meng on 2007-05-28
What about Kubuntu + Automatix2??
Admittedly, I had to drop to the command line to add the Automatix2 repository GPG keys ... but otherwise it ,seemed to work okay. I was not a big fan of Automatix previously, but changed my mind when I needed to use 32-bit apps on a 64-bit install.

---

### Post by miggols99 on 2007-05-28
What about Linspire/Freespire? The next version is based on Ubuntu, so it will have all the advantages of Ubuntu (I think) and I think it has drivers and codecs preinstalled.

---

### Post by BarfBag on 2007-05-28
SimplyMepis is a KDE distro that has proprietary stuff.  It's great, and it's light years ahead of Ubuntu with 64 bit support.  The only complaint I have is odd error messages and the fact that it's Dapper based (which isn't necessarily a bad thing).

---

### Post by pbw on 2007-05-30
> **67GTA said:**
> I also looked at Arch, but no non-free stuff

Dunno what you mean there, try and install a media player and it'll pull in the package "codecs", it's a depends of xine-lib. It's also in main repo.

---

### Post by ThinkBuntu on 2007-05-30
Sabayon has everything media-wise, and I mean everything, preinstalled in both the Mini CD and the DVD.

---

### Post by mips on 2007-05-30
> **ThinkBuntu said:**
> Sabayon has everything media-wise, and I mean everything, preinstalled in both the Mini CD and the DVD.

mini has no java&flash

---

### Post by 67GTA on 2007-05-30
Sabayon seemed really nice and up to date, but I didn't understand the emerge/portage thing. I guess I should learn it. The mini cd had me running Beryl after it booted up.  Debian/Ubuntu has spoiled me as far as package management. I haven't found anything easier than Synaptic/apt-get. They did not have a lot of docs on the subject that I could find.

---

### Post by 67GTA on 2007-05-30
PLinuxOS was really nice also, but after the third or fourth reboot it would always crash for some reason. I installed it three times with no luck. It just didn't like me. I have never really used mandriva enough to know what commands to use to try to fix it. It would always start with the boot screen having white lines and xserver crashing, but would be fine with no changes to the system before. I guess it is some kind of bug.

---

### Post by init1 on 2007-05-31
> **67GTA said:**
> I didn't think Linux Mint KDE was ready yet. The last time I checked they were still trying to finish porting it. I will look again. Actually, I have tried Kubuntu since I loved Ubuntu so much, and knew how to get the proprietary stuff easily, but did not like the mods they made to it. I may try it again when 7.10 comes out. Have you tried Mepis?
Yes, I like mepis a lot. It is not a stable as ubuntu, but it has all the wireless drivers and everything else I need for wifi. I had given up on wireless in linux until I saw my wireless light turn on when I booted mepis. I guess those drivers are proprietary, but they are worth it for me.

---

