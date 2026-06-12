---
title: "acpi=off..... so can I use apm?"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by TREESofRIGHTEOUSNESS on 2011-10-08
Hi all... I decided to post this message here, because I figured it would get a response.
I have a compaq presario r3000, and I have Xubuntu Natty installed on it.  I have also run Lubuntu, and the regular Ubuntu (I think that one was Maverick, though) anyhow...  I have to edit my grub to include the infamous acpi=off, in order for the computer to turn on.  But then it will not poweroff.  It will run through everything, and say System Halted.  So.....  I used Puppy on the computer and it worked great.  It booted, and powered off.  So, my REAL question, is do I need to use APM?  I think I saw somewhere that apm is not in the kernel, but if it is, then I can just add apm=on after acpi=off.
Otherwise, where can I download the apm module to use modprobe, or add something to the grub file?  Or should I go poking around in my BIOS settings.... this is a pretty old computer, but after I was given it (because of windows being overwhelmed by viruses, and a dead battery... I can only use the power cord) I found a much improved system, once I wiped it clean and installed Ubuntu (save for my acpi problem... oh yeah and the whole b43 firmware issue).

Thanks very much for your time!!  I am so enjoying using Ubuntu on all my machines... I've always liked Debian, and Ubuntu is by far the most sleek out there, with such an intuitive easy install process. (even allowing the acpi=off in the install, which made it possible for me to install)

---

### Post by Redblade20XX on 2011-10-08
Looking at [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement), it seems as if apm is still included in the kernel. I think after you login to the buntu, install the apmd package and then you can try that option in the grub file to see if works or not. :p

-Red

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-09
well, fancy that... it seems there is apm support in the kernel after all.  so i will just add apm=on and see how it goes from there.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-16
well... maybe not.  apm=on didn't correct my issue.... i've tried a lot of the other options no apic, and some others...  does anyone else have this issue??

---

### Post by Greydog56 on 2012-04-13
I’m fairly novice with linux. I’d been searching forums looking for clues/suggestions to get my old Compaq R3000 laptop running the linux os, also to get my wireless Broadcom BCM436 working in linux.


        I’ll fast forward to the successful installation. I installed Xubuntu 10.04 Lucid 2.6.32-generic 32 bit. Ran system updates, opened System>Hardware Drivers. There were two choices for proprietary drivers. Broadcom B43 wireless driver and NVIDIA accelerated graphics driver ver 96. I installed both, rebooted, set the ssid, password and..boom. wireless worked/graphics no problems. 



System powers on and off with no issues.


        My wireless hardware is Broadcom BCM4306.


        I realise I used a different version of Xbuntu than Treesofrighteousness had mentioned in the post. I decided to make this post just in case someone searching forums was struggling to get their Compaq R3000 running linux with Broadcom wireless. Maybe just try Xubuntu 10.04 Lucid 2.6.32-generic 32 bit, it worked for me.

---

### Post by TREESofRIGHTEOUSNESS on 2013-04-13
10.04 worked quite well with the default 32 bit version... however, 10.10, 11.04, 11.10 did not work. (Kernel differences)

12.04 works perfectly, however I had to use the 64 bit version.
[http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/xubuntu-12.04.2-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/xubuntu-12.04.2-desktop-amd64.iso)
I also like Lubuntu (LXDE) but it requires more tweaking and some extra things to make it work (such as thunar for automounting DVDs and xcompmgr for transparency)
[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-amd64.iso)

And as @Greydog56 said you must install the wireless (b43) drivers.
```

sudo apt-get install b43-fwcutter firmware-b43-installer

```
However the nvidia drivers for 12.04 haven't worked as well as noveau has for me.

---

### Post by wildmanne39 on 2013-04-13
Thread closed. Please do not post in old threads.

---

