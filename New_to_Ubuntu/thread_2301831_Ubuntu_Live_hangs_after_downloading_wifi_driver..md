---
title: "Ubuntu Live hangs after downloading wifi driver."
date: 2015-11-05
forum: New to Ubuntu
---

### Post by Wraflov on 2015-11-05
Brand-new to Linux and Ubuntu.  I used UNetbootin to download Ubuntu 14.04 Live x64 to a usb stick.  No problem.  Booted Ubuntu on an old Dell laptop that still runs Windows XP.  Still no problem, however, the driver for the wifi card was missing.  Ubuntu found the driver by itself for me after I connected with a network cable, and installed it without any problem.

The problem occurs when I reboot the machine.  It hangs about 15 seconds into the boot.  Just sits there and won't fully load the OS.  I have to unplug the stick and hard reboot the laptop.

Tried it twice, same thing happens.

I know I must be doing something wrong, but I don't know what it is.  anyone have an idea?

---

### Post by v3.xx on 2015-11-05
Ubuntu may be too much for your old box, it uses a lot of resources.  What are your specs?  ram, video, cpu

---

### Post by yancek on 2015-11-05
It isn't clear from your post whether you just used unetbootin to put Ubuntu on a usb stick or if you then used that usb stick to install Ubuntu to the hard dirve, clarify that.
You downloaded the 64bit version of Ubuntu, is your computer hardware 64bit compatible?
When you reboot and it hangs and you do a hard shutdown. what boots?  xp or do you have Ubuntu actually installed to the hard drive and it boots.  If you have installed Ubuntu to the hard drive, why do you have the flash drive still plugged in?

---

### Post by Sweet_Baby_Jamie on 2015-11-06
Ubuntu is way too much for my old Dell that ran Windows XP.  I use a very light-weight respin of _L_ubuntu (called [LXLE]("http://lxle.net")) which makes this old computer fly fast and free.  My computer has only 512 RAM.  It won't run Ubuntu, but the light-weight alternatives like Lubuntu run great!  Make sure it's 32-bit, too!

---

### Post by Wraflov on 2015-11-06
Sorry, I should have been more specific.

Yes, I'm leaving Windows XP on the laptop.  I put the live version of Ubuntu on a memory stick.  When I booted from the stick, Ubuntu booted into memory without any problems.  However, it had no drive for the wifi card in the laptop.  so I connected via an Ethernet cable and searched for available drivers.  Ubuntu found the needed driver and installed it without any problems.

But when I rebooted, expecting to see a wifi option under network settings, Ubuntu wouldn't fully boot.  It just hung there half-way through.  So I disconnected the stick, shut down and tried again.  Same thing.  I thought maybe I had a bad stick, so I used UNetbootin a second time to download Ubuntu Live to another stick.  I booted the laptop from the stick and Ubuntu loaded fine, but again, there was no wifi driver.  So again, I connected an Ethernet cable, got the driver and rebooted.

The same thing happened.  Ubuntu hangs halfway through booting.

I'm beginning to think you're right.  The little old laptop can't handle the Ubuntu software.  I'm just guessing, though.

Sorry for the length of this post, but I think that answers the questions that were asked.

---

### Post by buzzingrobot on 2015-11-06
If you do an install with the Ethernet attached and active, the installer should find it and use it without intervention on your part.  Once the install is done and you are booting into Ubuntu, stay on Ethernet until you can install the appropriate wireless driver. 

When you plugged in the Ethernet and Ubuntu installed a wifi driver, that driver was installed in the live session that runs in RAM.  It doesn't survive a reboot.

CPU speed, RAM and drive capacity wouldn't affect the ability to create a network connection.

---

### Post by yetimon_64 on 2015-11-06
> **Wraflov said:**
> Sorry, I should have been more specific.

Yes, I'm leaving Windows XP on the laptop.  I put the **live version of Ubuntu** on a **memory stick**.  When I booted from the stick, Ubuntu booted into memory without any problems.  However, it had no drive for the wifi card in the laptop.  so I connected via an Ethernet cable and searched for available drivers.  Ubuntu found the needed driver and installed it without any problems.

But when I rebooted, expecting to see a wifi option under network settings, Ubuntu wouldn't fully boot.  It just hung there half-way through.  So I disconnected the stick, shut down and tried again.  Same thing.  I thought maybe I had a bad stick, so I used UNetbootin a second time to download Ubuntu Live to another stick.  I booted the laptop from the stick and Ubuntu loaded fine, but again, there was no wifi driver.  So again, I connected an Ethernet cable, got the driver and rebooted.

The same thing happened.  Ubuntu hangs halfway through booting.

I'm beginning to think you're right.  The little old laptop can't handle the Ubuntu software.  I'm just guessing, though.

Sorry for the length of this post, but I think that answers the questions that were asked.
**Edit** **{If}** you are running the live cd session (from the USB stick of course) and saving the drivers to the live session **Edit:** (cont.) that would be expected. 

To install drivers to a USB stick and keep them would require you partition and fully install to the USB stick. This is possible to do but a bit advanced. Normally the live version is to test run and install either to the hard drive or a USB stick (full install of OS runnable off the USB stick etc as compared to just booting the live image you are currently using)

When you reboot a live cd environment any downloaded and  installed drivers are lost on the next boot, that is normal.

**Edit 2**: I often wonder how useful "unetbootin" is. The few times I tried it I ended up with unreliable USB bootable images. Others here may be able to advise if that is the case or not now, I don't use it any more myself.

---

### Post by Sweet_Baby_Jamie on 2015-11-06
If you running Ubuntu "live" from a memory stick *without persistence*, then the "installed" wifi driver won't remain when you log out of Ubuntu.  Nothing you do in a Live session is saved!  Did you intall Ubuntu from the USB stick to the hard drive?

---

### Post by Geoffrey_Arndt on 2015-11-06
After reading this thread three or four times, I'm still not sure if the Original Poster _actually "installed" Ubuntu onto the hard disk drive_.   If he/she didn't, then the bad results are (as the other posters have already said) . . . . **to be expected**.

---

### Post by sudodus on 2015-11-07
> **yetimon_64 said:**
> ...

**Edit 2**: I often wonder how useful "unetbootin" is. The few times I tried it I ended up with unreliable USB bootable images. Others here may be able to advise if that is the case or not now, I don't use it any more myself.

Unetbootin can be installed from the Ubuntu repositories. Unfortunately it is not up to date there (I have filed a bug report about it). But you get the current version from the developer's PPA, and it works for me most of the time. See this link,

[Installation/FromUSBStick#Unetbootin](https://help.ubuntu.com/community/Installation/FromUSBStick#Unetbootin)

But there are other tools, that I find more reliable. Which tool are you using?

See also the following thread (the poll is closed, but some of the replies might be interesting for you).

[Selecting a tool to create USB boot drives from ISO files](http://ubuntuforums.org/showthread.php?t=2291946)

---

### Post by sudodus on 2015-11-07
@ Wraflov,

In order the make things clear, please copy and paste ***the output of the following terminal window commands*** into a reply.

```
df
sudo parted -ls
sudo lsblk -fm
```

***df*** is the simplest but also most important command. It will show which partitions are used by the system, and will show if it is a live system or an installed system. The other commands add important information, that will be useful in order to help you.

---

### Post by Wraflov on 2015-11-07
> **Sweet_Baby_Jamie said:**
> If you running Ubuntu "live" from a memory stick *without persistence*, then the "installed" wifi driver won't remain when you log out of Ubuntu.  Nothing you do in a Live session is saved!  Did you intall Ubuntu from the USB stick to the hard drive?

I did set up persistence when I downloaded Ubuntu to the stick.  It's possible that I didn't install the wifi drive in the proper way, but that doesn't explain why Ubuntu hangs on reboot.  It boots fine until I install the wifi driver.  Then it hangs.

> **Sweet_Baby_Jamie said:**
> If you running Ubuntu "live" from a memory stick *without persistence*, then the "installed" wifi driver won't remain when you log out of Ubuntu.  Nothing you do in a Live session is saved!  Did you intall Ubuntu from the USB stick to the hard drive?

No, I didn't install Ubuntu to the hard drive.  I am running it off the stick.

> **yancek said:**
> It isn't clear from your post whether you just used unetbootin to put Ubuntu on a usb stick or if you then used that usb stick to install Ubuntu to the hard dirve, clarify that.
You downloaded the 64bit version of Ubuntu, is your computer hardware 64bit compatible?
When you reboot and it hangs and you do a hard shutdown. what boots?  xp or do you have Ubuntu actually installed to the hard drive and it boots.  If you have installed Ubuntu to the hard drive, why do you have the flash drive still plugged in?

I used UNetbootin to put Ubuntu on a stick.  I didn't install it to the machine's hard drive.  Yes, it is a 64-bit machine.  When Ubuntu hangs after installing the wifi driver and I have to do hard reboot, XP comes up.

---

