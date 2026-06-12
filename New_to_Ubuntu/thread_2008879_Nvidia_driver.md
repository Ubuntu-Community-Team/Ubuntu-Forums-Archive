---
title: "Nvidia driver"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by linux.convert on 2012-06-23
Ok, so I fudged up...I downloaded a Nvidia driver, trying to get Starcraft 1 to work better. I think it somehow rebooted automatically and now I have 640x480 resolution, and when I go to change it, it no longer lists 800 and 1024 and the refresh rate is set at 59 fps. I uninstalled the driver and have absolutely no idea what to do.

Lubuntu 12.04*
Acer Aspire One
Intel Atom Processor
Integrated graphics

---

### Post by Rex Bouwense on 2012-06-23
You obviously know more than I do if you are playing around with Lubuntu 12.10 which is still in its development phase.  That being said, after you uninstalled the driver are you back where you started from or is the video borked because you installed the wrong one and it replaced the correct one?

---

### Post by linux.convert on 2012-06-23
I'm using 12.04, I typed 12.10 originally in error...I think the new one replaced the old one, but its still working right now. The Additional drivers thing only shows a broadcom wireless driver, so that's no help. There doesn't seem to be a settings manager, by default, for graphics drivers where you can designate which driver to use.

*Synaptic shows that I have a bunch of Xserver-xorg video packages installed, so the problem may just be how to enable one...

---

### Post by Redblade20XX on 2012-06-23
> **linux.convert said:**
> I'm using 12.04, I typed 12.10 originally in error...I think the new one replaced the old one, but its still working right now. The Additional drivers thing only shows a broadcom wireless driver, so that's no help. There doesn't seem to be a settings manager, by default, for graphics drivers where you can designate which driver to use.

You tried installing via ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

-Red

---

### Post by linux.convert on 2012-06-23
Ok I added that ppa to my list for synaptic, but I'm not 100% sure which driver to select. This is all pretty new territory for me.

---

### Post by NikTh on 2012-06-23
Hello , 
give the output of commands 
```
lspci -nnk | grep -iA2 vga 
apt-cache policy nvidia-current
```
Thanks.

---

### Post by linux.convert on 2012-06-23
Totally unrelated, how do you show code in a reply?

--------------------------------------------------

USER@USER-AOD###:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Kernel driver in use: i915
USER@USER-AOD###:~$ 

--------------------------------------------------


USER@USER-AOD###:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 302.17-0ubuntu1~precise~xup1
  Version table:
     302.17-0ubuntu1~precise~xup1 0
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main i386 Packages
     295.40-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
        100 /var/lib/dpkg/status
USER@USER-AOD###:~$

---

### Post by Redblade20XX on 2012-06-23
To have text wrapped as code you just use the # sign option when you are in the posting menu. Take a look at the attachment I have.

From your previous post, it looks as if there is no proprietary NVidia driver installed. So first you would want to:

```
sudo apt-get update
```Then

```
sudo apt-get install nvidia-graphics-drivers               
```if that doesn't work, replace nvidia-graphics-drivers with nvidia-current.

This should download the driver and install it in your kernel automatically.

-Red

---

### Post by linux.convert on 2012-06-23
I early before your post, I went ahead and backed up my files and reinstalled. I'm not going to bother with it right now, not at least until I've researched it more.

Thank you guys alot for all the info.

---

### Post by NikTh on 2012-06-24
Hi.
Ok , here is the deal.. 
You have an Acer netbook with Intel integrated graphics. [B]You do not have Nvidia .

[/B]> USER@USER-AOD###:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0590]
    Kernel driver in use: i915So you cannot install Nvidia's driver on a machine that has not Nvidia graphics card.
Intel has not closed source (restricted) driver . Intel's driver its open and its already installed on Ubuntu. You can see "Kernel driver in use:i915" 
So don't spend your time for search or investigate anything about how to install Nvidia's driver at this netbook. You are Ok. 
Thanks

---

### Post by linux.convert on 2012-06-25
That makes a lot more sense now. After reinstalling with the 1024 x 600 screen, I am content to let sleeping dogs lie. Thanks a lot for that explanation.

---

### Post by dynosis on 2012-06-26
hi, i have nvidia graphics.
lspci -nnk | grep -iA2 vga 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV34 [GeForce FX 5200] [10de:0322] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:9980]
    Kernel driver in use: nouveau
i tried sudo... 
but it says, E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
i am at a loss? any help?
thanks

---

