---
title: "Upgrade from 8.04 to 8.10"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by richg on 2008-10-31
Hi All

The below method did not work using Terminal. The stuff I put in Terminal just went away and I was back to the desktop. The iso CD I burned worked fine using Live CD. I also had the iso file on the desktop.
-------------------------------------------------
Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1. Download the alternate installation CD
   2. Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
          *

            If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

            sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.
--------------------------------------------------------------------

I upgraded using Alt F2 to open Terminal then update-manager -d. Took about 137 minutes. All files and settings preserved. Really nice.
All settings and files preserved. I do not use a email application. I use web based email.

Rich

---

### Post by talsemgeest on 2008-10-31
If you used the live cd, then are you sure you had downloaded the alternate install cd? You must have that cd/iso to upgrade, it will not work with a normal live cd.

---

### Post by richg on 2008-10-31
> **talsemgeest said:**
> If you used the live cd, then are you sure you had downloaded the alternate install cd? You must have that cd/iso to upgrade, it will not work with a normal live cd.

I first ran the CD live to see if the download was ok. I also used that CD to do a complete new install, use all the drive, on a backup computer I use for playing around.

I also had the iso download on the desktop of the computer I wanted to upgrade The instructions say you can do an upgrade right from the iso if you do not have internet connection. Read between the dash lines. That is from a Ubuntu installation page.

Have you actually used the Ubuntu process between the dash lines?

Rich

---

### Post by talsemgeest on 2008-10-31
I'm still not sure if you understand me though. There are two different types of Ubuntu cds, there is the main, live cd that lets you try Ubuntu out running from the cd but does NOT let you upgrade, and there is the alternate cd which does not let you run it from the cd, but it does let you upgrade an existing installation.

I think you have downloaded the wrong cd. All of the Intrepid images are here: [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

I would suggest downloading this one: [http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso](http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso)

---

### Post by richg on 2008-10-31
I did the upgrade like I said. I got what I want.

Rich

---

### Post by talsemgeest on 2008-10-31
> **richg said:**
> I did the upgrade like I said. I got what I want.

Rich
Oh, I see. In that case, can you mark this thread as solved?

---

