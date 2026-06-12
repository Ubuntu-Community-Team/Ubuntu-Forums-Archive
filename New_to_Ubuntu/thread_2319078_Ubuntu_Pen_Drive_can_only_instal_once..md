---
title: "Ubuntu Pen Drive can only instal once."
date: 2016-03-31
forum: New to Ubuntu
---

### Post by cyan2 on 2016-03-31
Hello,

I am new to Ubuntu. I used the USB Installer (Pen Drive) to install Ubuntu on a 8GB thumb drive with a 4 GB Casper Drive. (would not allow me to use the entire thumb Drive, only 4GB). I used the Try Ubuntu before installation to make sure it works with all the hardware on my computer.  It worked very well with no issues so i wanted to try a full install. I tried to install Ubuntu several times (we will work on those issues in a separate Post)  my Question for this post is after each install the Pen Drive no longer works and is completely corrupt and crashes right after the POST about a 2 seconds after the Ubuntu menu comes up. I could not even launch try before instantiation. The simple fix is re-use the USB installer and reinstall it, however that is getting frustrating to have to log back into windows and load the USB installer to keep reinstalling over and over again after each installation. Why can't it be used for more than one install?

Thank you,
Cyan

---

### Post by goofprog on 2016-03-31
I would do it the old fashioned way and find a USB drive that is about the same data size and use the dd tool to reconstruct it on USB.  dd just copies the data to the device in its whole some state.  I just noticed that even unetbootin did not work for me.  It just would not work.  You can try it.  It is on on the current tree too.
**sudo apt-get install unetbootin**
put drive in usb slot
**sudo unetbootin**

---

### Post by grahammechanical on 2016-03-31
I have found that with USB memory sticks if the USB stick is not "ejected" before removal it will become corrupted. We need to shut down Ubuntu so that the machine powers off and then remove the USB stick. I have also noticed that sometimes it can take several seconds for the machine to shutdown. If we hit the power button before the machine has shutdown we will likely corrupt the USB stick.

Regards.

---

### Post by cyan2 on 2016-03-31
> **grahammechanical said:**
> I have found that with USB memory sticks if the USB stick is not "ejected" before removal it will become corrupted. We need to shut down Ubuntu so that the machine powers off and then remove the USB stick. I have also noticed that sometimes it can take several seconds for the machine to shutdown. If we hit the power button before the machine has shutdown we will likely corrupt the USB stick.

Regards.

Right, I understand that, but this is not the issue that I am referring to here. It is the process of the installation. Once I perform an installation from the USB drive I can no longer use it until I re-install it. this happens on every install, it was not a coincidence.  

Thank you.

---

### Post by RobGoss on 2016-04-01
Have you try formatting that thumb drive and reinstalling the ISO again? When I have these problems this seems to work for me

Last but not least you might have to replace that thumb drive if all else fails. Somethings are not worth all the headaches if it's a simple thing as replacing a thumbnail drive

Hope this helps.

---

### Post by cyan2 on 2016-04-10
Yes, each time I attempted an install I reformatted the thumb drive and and reinstalled the ISO to the thumb drive. I have done this many many times. I have done this on two different thumb drives with the same result which Is why I thought the ISO did this on purpose for some reason that I couldn't figure out.  From the responses on this thread, I am getting the impression that you have experienced this and that you have been able to reuses the the thumb drive and install Ubuntu multiple times without having to reinstall. the ISO, is that correct?

Thank you

---

### Post by yancek on 2016-04-10
There is no reason you cannot use a Live CD on a flash drives multiple times.  I've created bootable Linux flash drives to install system and then left them lying in a drawer for months and then used them again.   You mention not being able to use more than 4GB of the 8GB drive.  That would most logically be attributable to having persistent file on a FAT32 filesystem which is the limit on FAT32.

Not properly removing the flash drive as mentioned above is one possibility.  If  you use the pendrive with Ubuntu to install Ubuntu to a hard drive and do not safely remove or eject it before unplugging it, this can happen.

You aren't clear as to how or where you are installing Ubuntu when you use the pendrive.  Are you installing to an internal or external drive?  Any other operating systems on the drive(s)?

It isn't clear from your posts whether you have actually been able to use the pendrive to successfully install Ubuntu.  If so, why are you repeatedly installing it?  If not, are you sure you aren't trying to install to the same drive you are installing from?  That would certainly explain this, it is certainly not expected behavior.

---

### Post by Geoffrey_Arndt on 2016-04-10
USB Flash-Sticks are used extensively (and multiple times) without issues such as you describe.   But as of the last couple years some of the tools used to create the boot-able flashdrives have not been maintained as usual.   A tool with a great rep is "mkusb" . . . worth a try (uses dd backend).

---

