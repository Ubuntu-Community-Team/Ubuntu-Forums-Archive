---
title: "HP Photosmart 7260 problem"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by spacegypsy on 2008-07-28
Hi;

I've a photosmart 7260 printer who was auto detected by Hardy, the printing work just fine.
After a restart the printer did not work anymore; I got a message in the text balloon; printing error "media-jam" which changed in "other" after a few minutes.

So I tried the solution in this thread, [http://ubuntuforums.org/showthread.php?t=835872&highlight=printing+hardy](http://ubuntuforums.org/showthread.php?t=835872&highlight=printing+hardy) with the same results.

The only solution I found is that when the error message appears. To stop the queued documents in the printing menu, unplug the power of my printer, replug it and start the printing procedure over.

any ideas?

thanks

---

### Post by cpo2812 on 2008-07-29
Hi,

I have the same problem as described by spacegypsy.
I'm using the HPLIP and I posted my problem on HPLIP Launchpad
([https://answers.launchpad.net/hplip/+question/38687](https://answers.launchpad.net/hplip/+question/38687)).

Probably the newest version of HPLIP will fix this problem,
but I didn't try it out yet.

So if anyone has an idea how to fix this problem let me know how...

---

### Post by oldsoundguy on 2008-07-29
First off, am using 7.10 .. have 4 HP printers residing on my network of 3 Gutsy boxes and two XP boxes.  NO print problems, whatsoever.
Try un pluging the printer and then UN INSTALLING the HP utilities.  Then plug it back in and re install your utilities.  It MAY work as sometimes the handshake with the chip in the printer goes awry.  Make sure your cups driver is installed correctly also.
It does sound like a utilities issue with a bogus "paper jam" message.

---

### Post by gjoellee on 2008-07-29
isntall the latest HPLIP version: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by spacegypsy on 2008-07-30
Thanks for replies.

When extracting hplip-2.8.6b.run as non root I get the following message;

> guy@guy-desktop:~$ sh hplip-2.8.6b.run
Creating directory hplip-2.8.6b
Verifying archive integrity... All good.
Uncompressing HPLIP 2.8.6b Self Extracting Archive....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Extraction failed.
Complété


So I tried with sudo and then I got;

> guy@guy-desktop:~$ sudo sh hplip-2.8.6b.run
[sudo] password for guy: 
Creating directory hplip-2.8.6b
Verifying archive integrity... All good.
Uncompressing HPLIP 2.8.6b Self Extracting Archive..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
warning: hplip-install should not be run as root.

HP Linux Imaging and Printing System (ver. 2.8.6b)
HPLIP Installer ver. 3.3

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Wed-30-Jul-2008_20:50:22.log

|error: You are running the installer as root. It is highly recommended that you run the installer as
error: a regular (non-root) user. Do you still wish to continue?
Continue with installation (y=yes, n=no*, q=quit) ? q


Should I continue the installation and ignore the warning?

I forgot to start extraction from directory.........](*,)](*,)](*,)

---

### Post by cpo2812 on 2008-07-31
Thank you for your replies.

I've installed the newest version of hplip (2.8.7). I'll try it out and report if this will fix the problem.

Best regards

---

### Post by cpo2812 on 2008-07-31
The update will not fix the problem. My printer still hangs up...

---

### Post by spacegypsy on 2008-08-01
It seems doing it for me.

strange..

---

### Post by spacegypsy on 2008-08-01
2.8.7 ??

Mine is hplip-2.8.6b

---

### Post by myspacejmagenst on 2008-10-08
I have the same problem with hp photosmart 7260. It's giving me a "media jam" error message when I try printing a document on OpenOffice.Agreeing again with the first post, I have to cancel print job, disconnect the power from the printer and reconnect (how archaic).  What is currently installed is hplip 2.8.2. to avail. My search has come up short as I still don't have a functioning printer. My current solution: I'm using WinXP through VirtualBox.

---

### Post by jrb114 on 2008-11-09
Hi there,

Just to add a me too, to this post.

I've reported this as a bug. And to those who need to print out work to deadlines, this is a showstopper.

[https://bugs.launchpad.net/hplip/+bug/296077](https://bugs.launchpad.net/hplip/+bug/296077)

J

---

### Post by pedrogfrancisco on 2010-02-01
See workaround at: [https://answers.launchpad.net/hplip/+question/98527](https://answers.launchpad.net/hplip/+question/98527)

---

