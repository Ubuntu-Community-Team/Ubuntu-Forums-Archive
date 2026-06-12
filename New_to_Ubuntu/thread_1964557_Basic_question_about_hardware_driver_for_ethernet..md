---
title: "Basic question about hardware driver for ethernet."
date: 2012-04-24
forum: New to Ubuntu
---

### Post by sithone on 2012-04-24
I recently installed Ubuntu 10,04 alongside Win7.  I cannot get an internet connection, and 'lshw -C network' says that my Network is UNCLAIMED.

Browsing the forum I suspect that this is a driver issue. I have downloaded a driver Broadcom BCM57781 Ethernet PCIe (linux 3.122g) but I can't figure out how to install it.

My router is working, all lights on, and there are no problems using it in Win 7.

Regards.

---

### Post by audiomick on 2012-04-24
I gather you are talking about a wireless connection?

If so, I would suggest plugging in the machine with a cable to the router and let the Hardware drivers utility install the drivers for you.

---

### Post by sithone on 2012-04-24
No ... it is a wired connection.

Thanks.

---

### Post by sanderj on 2012-04-24
> **sithone said:**
> I recently installed Ubuntu 10,04 alongside Win7.  I cannot get an internet connection, and 'lshw -C network' says that my Network is UNCLAIMED.

Browsing the forum I suspect that this is a driver issue. I have downloaded a driver Broadcom BCM57781 Ethernet PCIe (linux 3.122g) but I can't figure out how to install it.

My router is working, all lights on, and there are no problems using it in Win 7.

Regards.

Is your hardware / networkcard new? If so, download Ubuntu 12.04 (=beta), live-boot it, and see if your networkcard works. A newer Ubuntu will support more newer hardware ...

---

### Post by audiomick on 2012-04-24
Ok. Don't know if I can help much, but what file format is the driver you got?

---

### Post by sithone on 2012-04-24
> **audiomick said:**
> Ok. Don't know if I can help much, but what file format is the driver you got?

I downloaded it from the Broadcom site ... the file is 3-122g.tar.gz

---

### Post by sithone on 2012-04-24
> **sanderj said:**
> Is your hardware / networkcard new? If so, download Ubuntu 12.04 (=beta), live-boot it, and see if your networkcard works. A newer Ubuntu will support more newer hardware ...

My internet connection is very slow, so this will take a while.  If I do this, will the new version detect the old version, and if so uninstall it?

Thanks.

---

### Post by sanderj on 2012-04-24
> **sithone said:**
> My internet connection is very slow, so this will take a while.  If I do this, will the new version detect the old version, and if so uninstall it?

Thanks.

For the test, you don't need to *install* the new version; just live-boot it from a CD (or USB-stick).

It will then be clear if it recognizes your ethernet network card automagically. If so, you can decide to install 12.04: a fresh install, or an upgrade of your existing 10.04.

If not, just reboot your computer from the harddisk and you'll have your 10.04 back.

HTH

---

### Post by audiomick on 2012-04-24
Trying it out from the 12.04 live environment is not a bad idea. If it works, go ahead and upgrade.

If you want to try installing the driver you have, I think you can extract it by right clicking on the file and choosing "extract here".

Have a look and see if there is a "read me" in amongst the stuff that gets extracted. There often is, I believe, with instructions on how to proceed.

---

### Post by sithone on 2012-04-24
> **audiomick said:**
> Trying it out from the 12.04 live environment is not a bad idea. If it works, go ahead and upgrade.

If you want to try installing the driver you have, I think you can extract it by right clicking on the file and choosing "extract here".

Have a look and see if there is a "read me" in amongst the stuff that gets extracted. There often is, I believe, with instructions on how to proceed.

I can extract the file in Ubuntu, but nothing happens.  In the readme file, it says to use something called "rpm" to install the driver, but I get an error message that says "rpm" is not installed.

---

### Post by audiomick on 2012-04-24
> **sithone said:**
> ... it says to use something called "rpm" to install the driver, but I get an error message that says "rpm" is not installed.
Bugger, wrong type of package.

Ubuntu uses the Debian system, in which the packages are .deb . That is referring to the system that I think Red Hat developed. Suse is one that uses it.

Where did you get the driver from? Maybe there is a .deb pacakge there as well.

Otherwise, try this
[https://help.ubuntu.com/community/RPM/AlienHowto]("https://help.ubuntu.com/community/RPM/AlienHowto")

I've never used it, but I believe it works

---

### Post by sithone on 2012-04-24
O.K. ... upgrading to 12.04 solved the Ethernet connection issue.  However, ver. 12.04 did not upgrade ver. 10.04, so I ended up doing a fresh install.

The main problem that I have now is that I can't download a driver for my video card (GTX 560 Ti). The log file associated with the error is attached ...

---

### Post by sithone on 2012-04-24
Solved!

"sudo apt-get install nvidia-current" did the trick.

Everything is up a running now!

Thanks to everyone who took the time to read and comment.

Cheers.

---

