---
title: "Freezing with Live CD"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Pbethe on 2008-06-30
I have tried several species of Ubuntu over the years, starting with Dapper Drake.  I have never been able to install Ubuntu, though, because thing grind to a halt very soon after booting into Linux.  I have searched the forums and not found anything exactly like me problem.  What will happen is that I see my desktop and can move the pointer with the mouse, but nothing happens.  Before the lockup, I have managed to capture some log files, most recently with Xubuntu 7.10.  I will attach them.  OOps, I can't attach them; I think they are too big.  I can attach one of my older attempts.  The result is the same.  There is some problem with my DSDT, but turning off ACPI does not help.  I end up with an error on "hdd", which is my CD drive.  This drive seems to work fine when I run Windows.  What happened?

---

### Post by stoneybroke on 2008-06-30
Did you do a hash check when you downloaded the .ISO file to make sure that it was not corrupted? if you didn't then try downloading again and check it. Also burn it to CD with the options set to slow and re-check it once its burnt to CD if everything is ok you should have no problems. I see you are using a 64bit computer so try Ubuntu-8.04 64bit version.

Hope that helps..

---

### Post by nowshining on 2008-06-30
also - a tip - if it's too big - try compressing the txt files, etc.. into a zip file, etc.. which should dramatically decrease the size.

---

### Post by Pbethe on 2008-07-01
> **stoneybroke said:**
> Did you do a hash check when you downloaded the .ISO file to make sure that it was not corrupted? if you didn't then try downloading again and check it. Also burn it to CD with the options set to slow and re-check it once its burnt to CD if everything is ok you should have no problems. I see you are using a 64bit computer so try Ubuntu-8.04 64bit version.

Hope that helps..

I lack the software to do the hash check before I burn the CD, so I check it when I first boot up.  Going by that I have three good disks and a bad burn of Gutsy Gibbon.  The edited log that I posted was Dapper Drake, I think.  I get very similar results from the other 2 good ones, so I figure it is not a random error on the CD.  I am thinking the things go wrong when I get the text in the logs:

  hdd:  status timeout:  status=0xd0 {Busy }

Things just grind to a halt, and I have to reboot.

Thanks,
Paul

---

### Post by stoneybroke on 2008-07-01
Hi Paul, when you download a .ISO image you check the hash file of the download with the official hash number this link will explain how its done.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Hope that helps..

---

### Post by wpshooter on 2008-07-01
Have you checked to see if there is a firmware update available for your CD-drive ?

---

### Post by Pbethe on 2008-07-03
> **wpshooter said:**
> Have you checked to see if there is a firmware update available for your CD-drive ?

Now, I have.  Searching the web, it looks like there is a version 7 of the firmware, and I am using v2.  Something tells me that I need to do a really good backup and try 7 out.  I will post what happens.  Thanks!

---

### Post by Pbethe on 2008-10-06
Well, I downloaded a firmware update for my CD drive, and got an executable and a .hex file.  The .exe runs, but it complains that it can't open the file.  All of this is running in MS-DOS.  I'm not sure the drive is the problem.  Usually, it works just fine.  It even booted from a Knoppix CD and ran without problems for about a day.

---

### Post by Pbethe on 2008-11-11
> **nowshining said:**
> also - a tip - if it's too big - try compressing the txt files, etc.. into a zip file, etc.. which should dramatically decrease the size.

Well, I have been up and running with the Xubuntu Intrepid Ibex CD for several hours now with no freezing.  I have had some strange things happen, like my menu disappearing off of the screen.  I was able to open a terminal by right clicking on the desktop, and I have compressed syslog.  It looks like this version deals with my 383M of memory by killing processes when it runs out.

---

### Post by Pbethe on 2009-03-01
I will mark this one as solved.  By adding a swap file on a USB thumb drive, I can get a reasonably stable session.  I do wish I could figure out how to upgrade the firmware on my cd drive, but that does not seem to be the big problem.

---

