---
title: "Installing 11.10 failure"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by CannibalGreg on 2011-10-20
I'm trying to install 11.10 to an old HP tower, 1ghz Pentium 4.
It boots, reads the cd, and then I see "ISOLINUX 4.04 20110518 ETCD" followed by the flashing cursor. I have looked through the bios for options to change but nothing has helped.
Ctrl+alt+del reboots the system. Nothing else has worked.

I downloaded ubuntu-11.10-desktop-i386.iso, and used PowerISO to burn a bootable cd.

I've let it sit for over an hour with no change. What should I do?

---

### Post by hyper2hottie on 2011-10-20
Try verifying the iso.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If its corrupted download a new one and check it.  If it's good then try that iso.

---

### Post by CannibalGreg on 2011-10-20
Verified. c396dd0f97bd122691bdb92d7e68fde5
As expected from [http://releases.ubuntu.com/oneiric/MD5SUMS](http://releases.ubuntu.com/oneiric/MD5SUMS)

How do I check the disc?
Any other ideas?

---

### Post by mörgæs on 2011-10-21
How much memory does the computer have? If less than 512 MB you should go for Xubuntu or Lubuntu.

---

### Post by ahmed.cnbd on 2011-10-21
I agree I had the same problem and changed to lubuntu

---

### Post by Supergoo on 2011-10-21
You might want to try the alterative install, I have had some computers that would not install from the Livecd but installed fine from the alterative iso. 



supergoo

---

### Post by CannibalGreg on 2011-10-21
I have 1024mb ram. 2 256 cards, 1 512 card. all 133mhz.

---

### Post by CannibalGreg on 2011-10-21
Tried ubuntu-11.10-alternate-i386 with no success. md5sum checked out, but all I got when trying to boot was the flashing cursor in the top left.

---

### Post by mörgæs on 2011-10-21
If you want to solve the problem, this thread is the place to look:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

However, trying another distro might be easier, if you are new to Buntu.

---

### Post by jfgencarnacao on 2011-10-30
I am having the same problem on a 4gb ram computer. I checked the MD5 and everything is ok, as I know it would as I used that very same cd to install Oneiric in other machines. I am suspecting of my motherboard which always had some issues with ubuntu but every time a new ubuntu comes, I have less and less compatibility issues.

Will update this if I find any way out.

PS: Haven't tried the alternative disk, will do soon, although I seriously doubt it will work.

Note: This computer had 11.04 installed, and I upgraded it to 11.10, but the upgrade caused me some issues, which I am now trying to fix with a fresh install of Oneiric

---

