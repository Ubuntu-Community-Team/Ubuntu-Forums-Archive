---
title: "Create USB Boot image (Intrepid) It brakes after updates."
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Kosimo on 2008-12-01
I made a USB Booting flash by using intrepid USB Image creator.
Everything works great but after doing the updates everything brakes and it doesn't works anymore. I wanted to use it as a my (portable OS's) but looks like I can't update cuz then it won't boot again. (Kernel maybe?)

So, there is any way for make all the updates and then keep using it?

Thank you

---

### Post by Kosimo on 2008-12-02
Any help?

---

### Post by Kosimo on 2008-12-03
OK then let me ask a more general question.
It is possible to update a USB booting image?

---

### Post by earthpigg on 2008-12-03
great questions. i wouldn't mind an answer either ;)

---

### Post by kernelhaxor on 2008-12-03
I would guess that if you chose "persistent file system" while creating the USB boot image, it should update and remember your settings and files. I installed 8.10 on my usb stick too but haven't used it much .. Let me boot using that, update and check .. I'll let u know after tht

---

### Post by Kosimo on 2008-12-03
> **kernelhaxor said:**
> I would guess that if you chose "persistent file system" while creating the USB boot image, it should update and remember your settings and files. I installed 8.10 on my usb stick too but haven't used it much .. Let me boot using that, update and check .. I'll let u know after tht

After a kernel update it breaks.... 

So, this is the question :) It is impossible to totally update the system?

---

### Post by ibuclaw on 2008-12-03
Doesn't the USB Boot sticks store the entire filesystem in one large compressed file that gets extracted into memory on bootup? I haven't used boot usb sticks that often, but I'm certain that it works very much like a LiveCD. 

From what everyone is saying, I guess your answer is "yes", it is impossible to do an entire upgrade on LiveUSB sticks.

What you could try instead is lock all **Base System** packages.

Open Synaptic, click the "**Sections**" tab in the bottom left part of the window, and select "**Base System**", now sort all packages that are shown in order of whether or not they are installed and select all installed packages.

Now click on "**Package**" -> "**Lock Version**".

Do the same for **Base System (restricted)** and **Base System (universe)** too, if any packages are installed from those repos.

Now, hopefully, that will prevent any base system packages from breaking your system.


If you want to restrict your system upgrades even more, while still in synaptic, click **Search** and type in "**driver**" as your search string. Again, organise by installed packages and lock all packages in there.
That should prevent any upgrades of audio and video modules/drivers too.


You could also stop any upgrade that isn't a security upgrade.
Go into "**Settings**" -> "**Repositories**".
Click on the **Updates** tab, and uncheck **Recommended Updates (hardy-updates)** (note, it will say intrepid if you are on intrepid).


And lastly, you could just try not upgrading your installation full stop ;)

Hope that I have been of help to you.

Regards
Iain

---

### Post by slyron on 2008-12-04
I have this problem too, in fact, I can't save any changes!

---

### Post by Cincinnatux on 2008-12-16
One option, if your USB pendrive has at least 4 GB (preferably more) space on it, is to think of it as an external hard drive.  With the USB device plugged into your computer, boot using a LiveCD of Ubuntu.  At the menu, select "Install."  Follow the usual install routine, but be very careful when it comes time to partition.  MAKE ABSOLUTELY SURE you select your USB device, rather than the computer's hard drive.  As [snowpine]("http://ubuntuforums.org/member.php?u=479885") has commented [elsewhere]("http://ubuntuforums.org/showthread.php?t=1003243&highlight=usb+persistent"), you'll also want to make sure that when it gives you the option to install a boot loader (either GRUB or LILO), make sure you install this boot loader to the USB device, not the hard drive.  

My USB drive is now fully persistent, and has survived two major rounds of updates.  The one frustration is that USB drives are much slower than internal hard drives, especially when installing updates.  YMMV, but patience is definitely useful if you want to treat a USB drive as your portable computer workspace.

Now I'm off to apply some of Keir Thomas's Ubuntu Kung Fu (one of the more interesting/useful Ubuntu books I've found) to get my USB OS to be fully-featured......

Best of luck,

Cincinnatux

---

### Post by Kosimo on 2008-12-17
> **Cincinnatux said:**
> One option, if your USB pendrive has at least 4 GB (preferably more) space on it, is to think of it as an external hard drive.  With the USB device plugged into your computer, boot using a LiveCD of Ubuntu.  At the menu, select "Install."  Follow the usual install routine, but be very careful when it comes time to partition.  MAKE ABSOLUTELY SURE you select your USB device, rather than the computer's hard drive.  As [snowpine]("http://ubuntuforums.org/member.php?u=479885") has commented [elsewhere]("http://ubuntuforums.org/showthread.php?t=1003243&highlight=usb+persistent"), you'll also want to make sure that when it gives you the option to install a boot loader (either GRUB or LILO), make sure you install this boot loader to the USB device, not the hard drive.  

My USB drive is now fully persistent, and has survived two major rounds of updates.  The one frustration is that USB drives are much slower than internal hard drives, especially when installing updates.  YMMV, but patience is definitely useful if you want to treat a USB drive as your portable computer workspace.

Now I'm off to apply some of Keir Thomas's Ubuntu Kung Fu (one of the more interesting/useful Ubuntu books I've found) to get my USB OS to be fully-featured......

Best of luck,

Cincinnatux


Thanks for the explanation... I'm going to give it a try at soon as I can get a bigger USB pendrive. Sure it is really handy to have your computer in your pocket.

Maybe the usb creator will allow to to that in future versions.

---

### Post by slyron on 2009-01-21
I've learned from experience that only some USB drive brands will work for creating a persistent USB boot disk. Attache' models don't ever seem to work for me. All Corsair USB drives work for me.

---

