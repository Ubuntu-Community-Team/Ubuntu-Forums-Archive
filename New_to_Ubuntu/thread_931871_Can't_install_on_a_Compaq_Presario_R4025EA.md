---
title: "Can't install on a Compaq Presario R4025EA"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by vision105 on 2008-09-27
Hi!
I used Ubuntu last year on a PC but had to give up because the wireless network wouldn't work correctly.  I am having another go with V8.04 and trying to install it on a Compaq Presario R4025EA laptop.  I was given the option of installing within Windows XP and picked a user name/password and off it went.  About 10 seconds later Windows reported a problem and the installation failed.  The error message went off to Microsoft.

I am not an expert on dual booting and installing one operating system within another so I'm hoping the laptop is going to work after I switch it off and start it up tomorrow!

Is there an easy way to have Ubuntu and XP on the laptop without the errors?

How do I find out if Ubuntu will work with the installed wireless network which uses WPA2?

---

### Post by shifty_powers on 2008-09-27
do you mean you used wubi?

if so then you have nothing to worry about :D

---

### Post by zephyrcat on 2008-09-27
From what you said, it sounds like the Windows installer (called Wubi) just crashed, so trying it again might help. Then again, it might not.

As for wireless, we would need the model of the wireless card. Unfortunately, I have had no luck finding this information online.

---

### Post by shifty_powers on 2008-09-27
managed to find out it is a broadcom, but not sure which one...

---

### Post by vision105 on 2008-10-04
hi again!

I got the computer going again with a system restore and tried a few more times to install.
I had thought it might be zone alarm stopping the installation but I switched it off and got the same error. something just stops it.

The wireless card in this PC is a Broadcom, but no details of a model number anywhere.  It just has 802.11b/g WLAN.  The current Windows XP driver is v 4.100.15.5  October 2006.  I'll see if I can find the booklets.

I'm going to try again later on as I think ubuntu would fly on this PC compared to XP.

---

### Post by vision105 on 2008-10-04
*UPDATE*

I tried again and thought I had everything running.  When the PC restarted it give the option of running XP or ubuntu.  After picking Ubuntu it went through various stages of checking and got to the bit about formatting the space to be used by partition 1.  That's when it froze for about 30mins.  
I've now uninstalled Ubuntu and fortunately the PC works fine with XP.
The HD is formatted in NTFS if that makes a difference.

Can anyone think of a reason why the installation should stick at this point?

---

### Post by Sef on 2008-10-04
> The HD is formatted in NTFS if that makes a difference.

Can anyone think of a reason why the installation should stick at this point?GNU/Linux does not run on NTFS.  You should reformat the partition that Ubuntu will go on as the default for Ubuntu - ext3.

> After picking Ubuntu it went through various stages of checking and got to the bit about formatting the space to be used by partition 1.XP should be on the first primary partition.  Windows is picky about things like that.  It makes no difference to Ubuntu.

---

