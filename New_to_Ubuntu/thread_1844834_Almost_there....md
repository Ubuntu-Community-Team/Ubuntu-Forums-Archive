---
title: "Almost there..."
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Lucky2BeHere on 2011-09-15
I created a USB boot drive with the latest Ubuntu ISO. It starts to boot, then gives this error and stops:

(initramfs) mount: mouning /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I have an IBM T30 running XP, if that helps.

Thanks,
John

---

### Post by searchfgold6789 on 2011-09-15
How did you create your USB stick?
I highly recommend[ **Unetbootin**]("http://unetbootin.sourceforge.net"). It's surefire.
 - search

---

### Post by Lucky2BeHere on 2011-09-15
I used the boot method suggested, Universal USB Installer 1.8.6.3. Best to use the other one, then?

---

### Post by searchfgold6789 on 2011-09-15
Since the tool you used didn't work, I am now suggesting another one.
I would say that UNetbootin is your best option since the other one wasn't working for you. Good luck!

---

### Post by sarwiz on 2011-09-15
Fixed the [Unetbootin]("http://unetbootin.sourceforge.net/") link:

---

### Post by skompier on 2011-09-16
Do you have an external USB HDD attached? If you do...unplug it and try booting again.

---

### Post by Lucky2BeHere on 2011-09-16
Tried UNetbootin. Got pretty far, then...same thing. Here's the error message:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I had selected Try Ubuntu without installing. Going a bit out of my comfort zone, here, but should I just install the damn thing? I don't want to lose it entirely in case it goes wrong.

Options?

---

### Post by dfarrell07 on 2011-09-16
Not all motherboards can boot from USB, but this says you can with a T30:

[http://bit.ly/oTqBR1](http://bit.ly/oTqBR1)

There is some good advice about adjusting BIOS settings in ThinkPads in order to boot from USB in this thread: 

[http://bit.ly/nc1mXb](http://bit.ly/nc1mXb)

Have you checked your boot order, in order to put the USB key at the top, and make sure that is the volume you are going to boot from?

---

### Post by Lucky2BeHere on 2011-09-16
Yep, it boots from the USB. The error message seems to say it goes through the install, partially, then stops.

---

### Post by Elfy on 2011-09-16
Quick question - did you check that the iso you downloaded is good before you tried booting from it?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you didn't, I suggest you do then at least you can remove one possible failure cause.

If it fails you'll need to download it again - if you get it from a torrent it should be ok.

---

### Post by Lucky2BeHere on 2011-09-16
Failed, and I got it directly from the official site :-(. Downloading now from a torrent.

---

### Post by Lucky2BeHere on 2011-09-16
Got much further this time. Installed on the USB to a point - found hardware, etc. - then stopped at a blank purple screen. Suggestions?

---

### Post by Blasphemist on 2011-09-16
A few questions.
1. What gpu do you have? Make and model please. ATI, Nvidia, Intel and model specifics. If you don't know this, what is the system make and model?
2. Do describe what you are prompted for prior to this happening. We might be able to tell what it's trying to do when this happens.
3. If you make the USB with Unetbootin, you should get a prompt for validate the media and try or install. I don't remember which for sure. Are you getting that and have you tried a validate media option from the USB grub menu?

---

### Post by Lucky2BeHere on 2011-09-16
Thanks. Here are answers to your questions, but see what comes after:

1. Don't know about the GPU, but have an IBM T30 notebook.
2. I expected something of an error message, but after it went through the hardware check, it stopped on a purple screen with no prompt or message.
3. Did that part fine. Got past that.

After an hour passed (on the phone, etc.), it gave me another message saying it was looking for network adapters. It took that long. I responded, and now am in a disk partition screen. I had chosen to run the OS instance off the USB drive, not install on the hard drive - not yet. I still might install on the HD, but is there a way to undo that? And, what is LVM when referring to the partitioning? It says: Guided - use entire disk and set up LVM

---

### Post by Lucky2BeHere on 2011-09-16
Important piece of info.

I got back to the Ubuntu installer main menu. I am not sure what some of the options really mean. All I want to do at this point is have the OS on the USB drive and boot from there. I would like to assess, then install it for good on the HD after.

Which option from that menu is what I want? (New at this...)

---

### Post by Blasphemist on 2011-09-16
Ah Ha! You mentioned the LVM question and it made me think that doesn't normally come up but I saw it last night in installing the 11.10 Oneiric Ocelot beta. I just booted that usb and there is no option for what you want to do. You need a "live cd" and should download the Natty Narwal 11.04 live cd and burn it to the usb.

Then, when you boot the live cd/usb, choose try ubuntu and you will be using a live installation only on the usb. If you use unetbootin to burn it, there is an option for setting persistence. Set say 1024MB persistence and you will have the ability to save files to the usb without loosing them after a reboot.

---

### Post by Lucky2BeHere on 2011-09-17
So. The prospect of spending that time pushed me to just do a full install. I used the tools from the Ubuntu site and it all went pretty smoothly. I now have 11.04 on the T30. Here are some issues:

1. The option to install from the desktop did not work. Upon the next reboot, I chose from the initial menu to install on the HD and selected a clean install. Worked.
2. This antiquated piece of hardware didn't have the cojones to run the new menuing system, so it's classic - and just fine. It can do everything it needs to: video, music, Office, etc. Turned a doorstop into a worthwhile machine that will have a few more years to go before it becomes a doorstop again.
3. Updating seems to be a problem, but don't know why, yet. A list of things to download is available, but won't fire off. Just sits there (or, maybe I am too impatient to wait more than 30 minutes for something to happen).

So far, so good!

Thanks very much for the help.

---

### Post by Blasphemist on 2011-09-17
Could be about the impatience thing :D

There could be literally hundreds of updates and it doesn't usually take so long but it is old hardware and could be slow. There is a details item on the update screen and it should show that something is happening, or not.

---

### Post by searchfgold6789 on 2011-09-17
> **Lucky2BeHere said:**
> 
3. Updating seems to be a problem, but don't know why, yet. A list of things to download is available, but won't fire off. 
Don't forget to update the package information first. In a terminal:```
sudo apt-get update
```
Forgive me if you already knew that.
Also forgive me for sounding as if I might have expected you to know that! :popcorn:
 - search

---

