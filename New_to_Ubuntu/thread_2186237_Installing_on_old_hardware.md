---
title: "Installing on old hardware"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by fconnollyma on 2013-11-06
I have a very old machine I am trying to install ubuntu 12 on for practice. I've read a lot and watchec many vids on how to do it. SO why can't I do it! Sorry...a little frustration coming out. I put in the CD but I can not get it to boot to the machine. Is there a trick? Does anything else need to be installed on the machine for it to work? Please Help!
thank you in advance.

---

### Post by Adam_GUI on 2013-11-06
1) Have you made sure your machine meets the minimum requirements for Ubuntu?
[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html]("https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html")

2) Have you set your computer's BIOS to boot from the CD-ROM as the default device?

---

### Post by david98 on 2013-11-06
Need a bit more info than that have you been into bios an selected boot from cd/dvd drive ?

---

### Post by fconnollyma on 2013-11-06
Yes. It reads the CD but then boots into windows.

The machine has plenty of power.

---

### Post by david98 on 2013-11-06
Are you sure the cd's not faulty ?

---

### Post by fconnollyma on 2013-11-06
I have created it a couple of times. What file should it look for to boot to the disk? There is no install or setup file on the CD.

---

### Post by philinux on 2013-11-06
> **fconnollyma said:**
> Yes. It reads the CD but then boots into windows.

The machine has plenty of power.

You need to go into the bios at boot and change to boot order to cdrom first. Usually press del key or other.  Check the boot  messages for which key to enter setup.

---

### Post by david98 on 2013-11-06
I would download a fresh copy of ubuntu from here [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop). Just to make sure you did burn the file as an iso ?

---

### Post by aromo2 on 2013-11-06
> **fconnollyma said:**
> Yes. It reads the CD but then boots into windows.

The machine has plenty of power.

This means 3 things:
1.  Are you sure you downloaded the right ISO for your system architecture?  i386 really means 32 bit architecture (Intel or AMD), AMD64 really means 64 bit architecture (again, Intel or AMD).  If in doubt, download the i386 ISO image, which will run on 64 bit capable computers but not the other way around.
2. Is you computer able to boot from CD?  You may have to enter to the BIOS in order to enable your computer to boot from CD.  Can you boot from a known good bootable CD (e.g. a Windows installer CD)?
3. Are you sure you burned the ISO file as an image and not as a file?  If you browse your CD and see an ISO file in it, you didn't burn it properly.  You have to burn it as an IMAGE (tools like ImgBurn in Windows are fool-proof).

Hope these tips help you resolve the issue.  You won't regret trying out Linux.

---

### Post by mörgæs on 2013-11-06
Changed the title to a more informative one.

Since you call the computer very old I would suggest Lubuntu 13.10 in stead of Ubuntu (not that it solves you booting problem, just general advice).

---

### Post by philinux on 2013-11-06
I think we all need to see the machines specification.  :)

---

### Post by sudodus on 2013-11-06
'Very old computer' is vague. Please specify the computer hardware

- Brand name and model
- CPU
- RAM (size)
- graphics card/chip

It will make it much easier to give relevant advice. Otherwise we can only give general tips or guess what is your problem.

See the general tips (by *mörgæs*) in this link [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by king.of.random on 2013-11-06
I have Bodhi Linux installed on a very old (circa 2000) pc. Pentium III with less than 512 ram. It has the enlightenment desktop and looks so beautiful.... I'm in awe of what they've done :)

It may be worth also checking that the drive actually works and perhaps cleaning the lens if necessary. You can pick up suitable kits to do this from your local pc retailer. But the obvious issue maybe the boot order in the BIOS. the hdd must come after the cd/dvd drive.

As another thought is your drive dvd? As if it isn't that would be the problem as the iso is too large for a cd.

---

