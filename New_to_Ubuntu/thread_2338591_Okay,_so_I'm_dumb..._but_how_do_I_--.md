---
title: "Okay, so I'm dumb... but how do I --"
date: 2016-09-29
forum: New to Ubuntu
---

### Post by billy.boy.bob on 2016-09-29
Okay, so I admit it... I ain't too savvy. A long time Windows user, and that's all I ever do is "use", I've downloaded Ubuntu 16.04.1 LTS Xenial Xerus because Windows 10 is the pits. But where did it go? Rather, how do I open Ubuntu? The how-to with the download is quite clear, but once the download is done... what do I do now? For some reason there is a DVD drive on my C: drive... but 1) for some reason the DVD drive on Windows 10 doesn't respond and 2) none of the files in that DVD does anything. I'll take any help I can get... and while feeling dumb, will be filled with gratitude if the explanation is simple enough for me.
Ahead of time... Thank you......
Bill

---

### Post by yancek on 2016-09-29
You need to burn the downloaded iso of Ubuntu to a DVD 'as an image'.  If you don't have software currently installed on windows, you will need to also get that.  You can also put the iso on a flash drive using pendrivelinux or the windows version of unetbootin.  Just google either and you should find the site.  After doing that, you will need to boot the computer with the DVD or flash drive installed and set to first boot priority in the BIOS.

The official Ubuntu documentation on dual booting Ubuntu with windows 10 is at the link below:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by cariboo on 2016-09-29
I've used [Rufus]("https://rufus.akeo.ie/") on Windows 10 a couple of times, it always works to create a bootable usb drive.

---

### Post by howefield on 2016-09-30
Windows 10 has the ability to mount and burn iso images already built in.

I'm guessing that you have double clicked the file which has mounted it, hence the "DVD" mentioned in your post, which should reveal the files contained within the iso.

Right clicking on the downloaded iso file and selecting "*Burn disc image*" will allow you to burn to a DVD.

If you want a Live USB stick use one of the options that cariboo and yancek already mentioned.

---

### Post by saresu2 on 2016-09-30
Before anything, not necessary to say there's a steep learning curve to get around Ubuntu so if you're an absolute newbie, I strongly urge you to download VMplayer (link below) and use it to install the ISO file you downloaded and put it into a virtual machine. You can operate Ubuntu normally from VMplayer in Windows. That way, you can get to learn how Ubuntu works first, without stress. And btw the program is free.
[https://www.vmware.com/products/player/playerpro-evaluation.html](https://www.vmware.com/products/player/playerpro-evaluation.html)

Maybe you will have to change a setting in your bios called  CSM and disable "Secure Boot".

Also, don't forget to check this therad: [https://ubuntuforums.org/showthread.php?t=2015424](https://ubuntuforums.org/showthread.php?t=2015424)

Have fun

---

### Post by buzzingrobot on 2016-09-30
> **billy.boy.bob said:**
> Okay, so I admit it... I ain't too savvy. A long time Windows user, and that's all I ever do is "use", I've downloaded Ubuntu 16.04.1 LTS Xenial Xerus because Windows 10 is the pits. But where did it go? Rather, how do I open Ubuntu? The how-to with the download is quite clear, but once the download is done... what do I do now? For some reason there is a DVD drive on my C: drive... but 1) for some reason the DVD drive on Windows 10 doesn't respond and 2) none of the files in that DVD does anything. I'll take any help I can get... and while feeling dumb, will be filled with gratitude if the explanation is simple enough for me.
Ahead of time... Thank you......
Bill

The file you downloaded will be in the folder your browser uses as its default download folder.

The file cannot be executed ("run").  It's in the format used in the industry for installation of operating systems, including Windows. It's intended to be transferred to a DVD, and can also be transferred to a USB stick. This transfer is not a simple file copy.  An exact duplicate of the file needs to be placed on the the DVD or USB stick. This transfer is commonly called "burning" the image. 

If you have a DVD drive, you can insert a DVD in it, right click on the file and Windows will offer to burn it to that DVD.

If you don't have a DVD, you'll need to use a USB stick and follow the instructions at ubuntu.com and in this thread. 

Once you have the file burned to a DVD or USB stick, you can restart your system and tell your machine to boot the OS image on the DVD/USB rather than Windows. 

When you boot an Ubuntu image like this, the first thing you see is the option to "Try Ubuntu" or to install Ubuntu.  If you choose the "Try Ubuntu" option, Ubuntu runs entirely in a "Live" mode using the DVD/USB. This gives you a chance to explore Ubuntu and to see if all the hardware in the machine works appropriately. Live mode is reasonably speedy on a USB, and not very speedy on a DVD. (I'd recommend using this approach to sample Ubuntu before attempting to set up a virtual machine installation, especially if that is new territory for you.)

The "Install" option, of course, does just that. Before you install, you need to decide if you want Ubuntu to replace Windows entirely, or if you want to maintain Windows while installing Ubuntu  and maintaining the ability to boot into either OS ("dual booting").  

In all cases, remember that Ubuntu is its own operating system, not a program to be installed and run inside Windows. You must ensure space is available on the drive for its installation. If you want to completely replace Windows, this could be the entire drive. If you want to dual-boot Windows and Ubuntu, you need to ensure at least one partition on the drive is available for Ubuntu. If Windows is currently using the entire drive, there are tools in Windows to decrease that and free up space.

---

