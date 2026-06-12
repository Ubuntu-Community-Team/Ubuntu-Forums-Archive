---
title: "Ubuntu 12.04 Antivirus &amp; Firewall Do i need them!"
date: 2013-06-16
forum: Recurring Discussions
---

### Post by justme22 on 2013-06-16
Hi I recently Installed Ubuntu 12.04 i just want to know if i need Antivirus & a Firewall. Or is ubuntu 12.04 secure already as it is. And if not what are the best antivirus and firewall for ubuntu.

---

### Post by Impavidus on 2013-06-16
Have a look at the security section of this forum and read the stickies.

In short: Ordinairy desktop computers don't really need anti-virus software. It adds to the bloat without really offering added security. A firewall is probably build into your router. The main thing to keep in mind considering security in Ubuntu is only installing software you can trust and not using your root permissions when you don't understand why.

---

### Post by matt_symes on 2013-06-16
Thread moved to **Security Discussions**.

---

### Post by ShadowVegan on 2013-06-16
They aren't necessary but if you do want extra security see [Basic Security]("https://wiki.ubuntu.com/BasicSecurity") and [Security](https://help.ubuntu.com/community/Security). A popular antivirus software is [ClamAV]("https://help.ubuntu.com/community/ClamAV").

---

### Post by justme22 on 2013-06-16
Ok thank you

---

### Post by jll339 on 2013-06-18
Yeah I would just say don't bother with Linux. It causes more problems than its worth! Some can really slow down the computer and make it prone to freezing!

---

### Post by 3mutts on 2013-06-18
Unless you are running a server, you don't "need" a antivirus suite however, if you are sending alot of files to Windows users then its a good idea to install a on demand scanner (like Clam AV) to scan files before sending it to them or transfering files to your Windows machine. I would enable the firewall as it is simple and blocks all the harmful ports.

---

### Post by sh4d0w808 on 2013-06-19
*"..Yeah I would just say don't bother with Linux. It causes more problems than its worth! Some can really slow down the computer and make it prone to freezing!..."*

It depends on your hardware. Previously, I tried a lot of things written here by bodhi.zazen and my Athlon64 X2 7750 CPU loaded by 1-2% additional work and need 300 additional MB of RAM. I have 8 GB RAM, so it was not really important. Theoretically, if you have 4 GB RAM and at least a CPU as I have, you can play with security, you will learn a lot...

---

### Post by Velnias on 2013-06-19
Well, so far the best answer about antivirus generally is  :eek: [Johns McAfee]("http://www.youtube.com/watch?v=bKgf5PaBzyg")

---

### Post by KARNVORbeefRAGE on 2013-06-30
ClamAV with gufw.

---

### Post by cariboo on 2013-06-30
This topic has been discussed so many times, it's now a recurring discussion. Moved.

---

### Post by deadflowr on 2013-07-01
> **justme22 said:**
> Hi I recently Installed Ubuntu 12.04 i just want to know if i need Antivirus & a Firewall. Or is ubuntu 12.04 secure already as it is. And if not what are the best antivirus and firewall for ubuntu.

No. You don't need a firewall or anti-virus.
But they're nice to have.
Ubuntu comes with a firewall, ufw, a command line program to control a firewall.

There are various anti-virus programs you can run, starting with clam and also ones from avg, avast, and bitdefender among others.

---

### Post by craig10x on 2013-07-01
Download gufw fron the software center and just turn it on...ports are closed by default on the linux firewall but turning gufw on makes you more "stealth" (invisible)...
As far as anti virus scanners, only if you need to protect any windows user against something you might send him...linux doesn't respond to windows viruses....of course, most windows users use anti-virus so they should be protected on their end anyway...that's why i never bother with that...just turn on the firewall and i am done...

---

### Post by BR8 on 2013-07-09
If you go to a lot of shady sites and download anything you see, then yes, it's probably a good idea. If you have a good idea who made the package you're installing, probably not. They're nice to have, especially if you have any sort of paranoia.

---

### Post by NormanFLinux on 2013-08-16
On Linux and Mac OSX, the only thing you need to do is set up the firewall.

There is no need to run AV since viruses and trojans are seldom written for these operating systems.

---

