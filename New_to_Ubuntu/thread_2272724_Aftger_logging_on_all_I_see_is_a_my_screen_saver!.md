---
title: "Aftger logging on all I see is a my screen saver?!"
date: 2015-04-08
forum: New to Ubuntu
---

### Post by csp-liam on 2015-04-08
Hi guys I am new to Ubuntu and have recently installed it on my PC (I used to run Kubuntu).

My PC has been running very slow since I installed it and now after I have logged on all I see is my screen saver.

I suspect issues are related to drivers and I also saw a message earlier today during boot up when it was still working saying something like the disc drive for swap files is not ready for use.

Can anyone help me get back up and running again?

---

### Post by dino99 on 2015-04-08
please give us some usefull info (blahblah does not help): wich ubuntu release ?, which graphic card ? which driver installed ?

from a terminal, run and post the output of:
  sudo blkid    
  cat /etc/fstab

---

### Post by csp-liam on 2015-04-08
> **9d9 said:**
> please give us some usefull info (blahblah does not help): wich ubuntu release ?, which graphic card ? which driver installed ?

from a terminal, run and post the output of:
  sudo blkid    
  cat /etc/fstab

Sorry I am a bit vague but I have very little knowledge of Linux despite using kubuntu for a number of years because it has always just worked for me.

I am running 32 bit Ubuntu 14.x I do not know what graphics card is in this PC

Thank your for your offer of help.

Can you tell me how do I get into a terminal session when all I can see is my screen saver after logging in?

---

### Post by csp-liam on 2015-04-08
OK got into terminal by using ctrl + alt +_F1

sudo blkid

/dev/sda1: VVID="1056448f-dd22-4292-82aa-eb171bbc88b0" Type="ext2"
/dev/sda5: VVID='5yJnw-3Joq-KyHa-1UK1-suYU-wjsa-n8GYH2" Type="LVM2_member"
/dev/sdb1: LABEL="/" VVID="ec7b7cf4-432b-4ef4-ae5e-72be4od2c85c" SEC_TYPE="ext2" Typ="ext3"
/dev/sdb5: TYPE="swap"
/dev/mapper/Ubuntu--vg-root: VVID="617069da-40a6-4140-8dbe-c45f51fe9ac5" Type="ext4"

---

### Post by csp-liam on 2015-04-08
When I type cat/etc/fstab I get the response command not found?

---

### Post by michi1983 on 2015-04-08
> **csp-liam said:**
> When I type cat/etc/fstab I get the response command not found?

you forgot a space between cat and the rest of the command. its ```
cat /etc/fstab
```

---

### Post by csp-liam on 2015-04-08
> **michi1983 said:**
> you forgot a space between cat and the rest of the command. its ```
cat /etc/fstab
```

Thanks.

OK I have to manually type this on another machine as I can't do a screen capture and send it from the faulty machine...

/dev/mapper/Ubuntu--vg-root /    ext4   errors=remount-ro 0     1
# /boot was on  /dev/sda1 during installation
VVID=-1056448f-dd22-4292-82aa-eb171bbc88b0 /boot   ext2   defaults    0    2
/dev/mapper/Ubuntu--vg-swap_1 none     swap   sw    0    0
/dev/sdb5    none    swap   sw     0    0
/dev/fd0     /media/floppy0 auto   rw,user,noauto,exec,utf8  0    0


Thanks very much for the help guys.

---

### Post by csp-liam on 2015-04-08
Ok what's next guys?

My computer still just stops on the home screen once I logon. All I can see is the wall paper and the mouse cursor which I can move but that is all.

BTW I used the lsb_release -a command to discover I am using Ubuntu 14.04.2 LTSD release 14.04 codename trusty.

The problem with my PC stopping at the home screen after I logged on happened after I followed these instructions to speed up my PC

sudo apt-get purge fglrx*
sudo apt-get install fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo aticonfig --initial

I got the error message after typing in the last command aticonfig: No supported adapters detected

and at this point I lost the ability to do anything further than log in to Ubuntu.
...so I fear I am the master of my own problems!

Any help in rectifying this would be appreciated.

---

### Post by csp-liam on 2015-04-08
Bump

---

### Post by grahammechanical on 2015-04-08
Can we clear up a few matters? Thank you.

I do not think that you are seeing a screen saver. Ubuntu does not install a screen saver any more. I think that you are seeing the desktop but without the Unity user interface.

Why are you installing AMD/ATI video drivers? Do you have an AMD/ATI video adapter? I have not seen anything in your posts that tells me that you have AMD video adapters. I see this as a clue

> No supported adapters detected

with next to no information about your hardware, what could the problem be? We can only guess. When you installed did you tick the box, Install Third Party Software? If you did that then an appropriate proprietary video driver was installed. But it would be the latest stable version which may have dropped support for older video adapters. This does happen. It may or may not be happening to you. What can you do?

Try right clicking the desktop wallpaper. Do you see a menu with the option Change Desktop Background? If you do, then select Change Desktop Background and that will open System Settings at the appearance menu. From there you can get to the full System Settings dialog.

At System Settings select Software and Updates and open the Additional Drivers tab. You need to be connected to the internet and you need to allow the utility time to do its work. You will get a list of video drivers. There will be 4 versions of proprietary drivers and one open source video driver. Select and apply the open source video driver. Then re-start. First, get loading to a working desktop and then experiment with proprietary video drivers if you think the open source video driver is not adequate.

If you want to know what video adapter you have and what drivers are available run

```
ubuntu-drivers devices
```

It takes it time but this is what I see

> ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : GT216 [GeForce GT 220]
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00000A20sv00001043sd0000830Fbc03sc00i00
driver   : nvidia-340 - distro non-free recommended
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-304 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304-updates - distro non-free

By the way, my machine works fine on nouveau and nvidia 304 but I hit problems when I try nvidia 340 or newer versions. I suspect that Nvidia has dropped support for my card from its latest drivers.

Regards.

---

### Post by csp-liam on 2015-04-08
grahammechanical thanks for your help.

Yes I think what I am seeing is the Desktop without a unity interface.

No I don't think I have an AMD/ATI adaptor (I accepted the wrong advice on the that one - my fault!)

 Right clicking on the desktop does not open any menu or do  elicit any other response.

 the command Ubuntu-drivers devices causes my machine to go pause for a while and then just return the command prompt.

 I found some other commands that provide information on the video card I think and I got this

 VGA Compatible Controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4m800 CE/VN80-0 Graphics. [S3 Unichrome Pro] (rev 01).

 Would I be correct to assume that my problem is that I don't have the correct video drivers loaded?

 How can I reinstall the correct ones?

---

### Post by Vladlenin5000 on 2015-04-08
You can't run Unity in such old graphics chip, no matter what drivers. Up to 12.04 perhaps you could but not now. 
Instal and use Lubuntu or even lighter...

---

### Post by csp-liam on 2015-04-08
> **Vladlenin5000 said:**
> You can't run Unity in such old graphics chip, no matter what drivers. Up to 12.04 perhaps you could but not now. 
Instal and use Lubuntu or even lighter...


Thanks Vladlenin, It was working before (albeit slowly) with this version of Linux. While it would be nice to speed it up this machine is used for background tasks so it is kindo of OK if it runs slowly. I would rather it ran slow than reload another version of Ubuntu as I do not want to loose the other stuff I have setup on this machine. Vladlenin is there a way to just get it back working like it was before (albeit slowly). 

How do I tell what video driver I had/need for my video card and where do I get it from again?

Can I reload the correct video drivers from Terminal,  that I have inadvertently deleted?

---

