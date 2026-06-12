---
title: "Missing Operating System.."
date: 2016-03-25
forum: New to Ubuntu
---

### Post by brenda4 on 2016-03-25
I bought a new hard drive for an old laptop (Dell Inspirion N5040) and I have no operating system on it. I have downloaded Ubuntu 12.04 and put in my USB drive. Everytime I put it in my laptop it says "Missing Operating System" I know the USB isnt the problem since when I put it in my other laptop it shows properly.

---

### Post by yancek on 2016-03-25
> I have downloaded Ubuntu 12.04 and put in my USB drive.

How?  By USB drive are you referring to a flash drive or an actual hard drive?  Did you just create a bootable Live/Install CD or did you go through the process of installing Ubuntu?

---

### Post by Bucky Ball on 2016-03-25
Welcome. Sounds like your machine is trying to boot from the empty hard drive. Silly question, but you have set the BIOS to boot from USB?

Another question, this time not silly: why 12.04 LTS? 14.04 LTS is supported until 2019 and rock solid. 12.04 has another year but a longer upgrade path when it goes EOL. You'll need to go directly to 14.04 LTS and then to 16.04 LTS when the time comes. Installing 14.04 LTS will save you an upgrade/clean install and give you three years to think about it. :)

@yancek:

> **yancek said:**
> How?  By USB drive are you referring to a flash drive or an actual hard drive?  Did you just create a bootable Live/Install CD or did you go through the process of installing Ubuntu?

This might throw some light:

[QUOTE=brenda4]I know the USB isnt the problem since when I put it in my other laptop it shows properly. [/QUOTE]

USB installer appears to be fine. :)

---

### Post by sudodus on 2016-03-26
Welcome to the Ubuntu Forums :-)

Yes, the USB *shows* properly, but does the other computer *boot* from it?

Did you check with md5sum that the download iso file is correct? [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Please describe how you made the USB drive into a boot drive: which tool or method did you use?

See these links (and links from them) for more details,

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by trilok2 on 2016-03-26
I think you didn't made the bootable pendrive .. and ubontu should be .iso file to become bootable.. then only you can add window....

---

### Post by buzzingrobot on 2016-03-26
> **brenda4 said:**
> I bought a new hard drive for an old laptop (Dell Inspirion N5040) and I have no operating system on it. I have downloaded Ubuntu 12.04 and put in my USB drive. Everytime I put it in my laptop it says "Missing Operating System" I know the USB isnt the problem since when I put it in my other laptop it shows properly.

Take a look at the instructions here for making a USB stick that you can boot from and install Ubuntu: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Once that's done and the new drive is installed in the laptop, plug in the USB stick and reboot the machine.  At that point, you need to enter the Dell's BIOS setup menu,  That's accomplished by tapping a particular key as it boots.  That key varies from machine to machine, so if you don't know what it is you'll need to chase down a manual for the Dell and look it up. However, it's commonly something like F1 or F2, etc. (Very likely all Dell laptops use same keystroke.) (Needing to do this is not a peculiarity of Linux or Windows.  It's just a standard set for all PC's.)

Once you're in the BIOS setup, look around for a menu entry about "Boot Order" or something similar. What you want to do is tell the BIOS to use the USB stick to boot from, not the new hard drive. The USB stick may be identifiable by brand name, or the letters "usb" or something else.  It varies.

Once that's done, save the changes and reboot. (There will be an option shown to do that.)  If the Ubuntu install image was "burned" correctly to the USB stick, the laptop should boot into the Ubuntu,  You'll see a "Try Ubuntu" and an "Install Ubuntu" display. 


When you do run the installer, you will see a step that partitions the drive. If the new hard drive is the only drive in the machine (ignoring the USB stick) then you can select the option that is at the top of the partitioning menu, and the installer will use the entire drive for Ubuntu and create all the needed partitions automatically. This is the option you should take unless you have experience creating Linux partitioning schemes.

When the install complete, you'll be prompted to remove the USB stick and reboot into the new Ubuntu system.

---

