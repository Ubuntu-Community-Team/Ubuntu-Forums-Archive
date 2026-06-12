---
title: "Error during installation: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by professorfish on 2013-07-12
I have successfully downloaded the ISO disk image for Lubuntu 32bit 13.04 and burned it onto a DVD (using Power2Go at 4x speed, on a fairly modern Asus laptop). When I put the DVD in and choose a language, a menu with the Lubuntu logo at the top appears. When I select any of "Try Lubuntu without installing", "Install Lubuntu" or "Check disk for errors", the following happens:

1. The menu freezes for a few minutes.
2. The following message is displayed on a black background in a console font:
[     7.196413] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
3. An underscore endlessly flashes below this message.

I have not had any previous experience with Linux, and I have got this far thanks to Ubuntu Wiki.
The computer I am trying to install Lubuntu on is about ten years old (I am doing this in a desperate attempt to speed it up) has:
Windows XP Home Edition
about 10GB space on C:\
about 30GB space on D:\
480 MB RAM
Intel Celeron

How can I solve this and install Lubuntu? Is the problem to do with the way I burned the DVD or just the restrictions of the computer?

Thank you in advance!

---

### Post by professorfish on 2013-07-15
132 views, no replies - do I need to provide more information?

---

### Post by Rex Bouwense on 2013-07-15
I'll give it a go.  First, you said that you had a successful download.  How do you know that this is true?  Did you do an MD5Sum on the download?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Many failures to install are because of a bad download and the MD5Sum was never checked.  Second step of course is to burn the ISO to a CD or to make a bootable flash drive at the slowest possible speed.  You have done this.
Are you trying to install Lubuntu on the entire disk or are you trying to install Lubuntu next to Microsoft Windows or are you trying to install Lubuntu inside of Windows using WUBI?

---

### Post by grahammechanical on 2013-07-15
There are also a couple of other things to check off. Is this Celeron CPU a non-pae CPU? If so, according to this you are better off using Lubuntu 12.04.

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Are you using the Alternate ISO image to install? It is the method recommended for machines with less than 700 MB of RAM.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

One more thing. When you get to that TRY -  INSTALL - CHECK screen press F6 and at the bottom right a small menu will appear. Try experimenting with the options in that list. Select one and press Enter, then press ESC to get back to the TRY - INSTALL screen. Experiment with different combinations.

Regards.

---

### Post by professorfish on 2013-07-16
> **Rex Bouwense said:**
> I'll give it a go.  First, you said that you had a successful download.  How do you know that this is true?  Did you do an MD5Sum on the download?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Many failures to install are because of a bad download and the MD5Sum was never checked.

Thank you!
winMd5Sum tells me that the md5sum doesn't match. What do I do?


> **Rex Bouwense said:**
> Are you trying to install Lubuntu on the entire disk or are you trying to install Lubuntu next to Microsoft Windows or are you trying to install Lubuntu inside of Windows using WUBI?

I am trying to install it alongside Windows.

---

### Post by Rex Bouwense on 2013-07-16
If the MD5Sum doesn't match it means that you have a bad download and you must download the ISO again.  I would recommend using a torrent.  They are more reliable.  Checking that is the very first thing that you should do when downloading any linux system.  If it is bad then all things after that will be screwed up.Good luck.

---

### Post by fourdoops on 2013-09-27
I have the same problem.

---

### Post by Jonathan Precise on 2013-09-27
> **professorfish said:**
> Thank you!
winMd5Sum tells me that the md5sum doesn't match. What do I do?

Re-download the ISO. Check the md5sum of the new ISO.

[QUOTE=Rex Bowense]I would recommend using a torrent.[/QUOTE]

I have had many problems with torrents, which is why I quit using them. So I do **NOT** recommend them.

---

### Post by Jonathan Precise on 2013-09-27
> **fourdoops said:**
> I have the same problem.

Check the md5sums. If they do not match, re-download.

---

### Post by mörgæs on 2013-09-28
As a small side note: Lubuntu fits to a CD, so there's no need to use a DVD for installation if the USB approach does not work.

---

