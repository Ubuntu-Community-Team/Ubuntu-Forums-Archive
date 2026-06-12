---
title: "Is my computer just too old for Ubuntu?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Qwertinsky on 2008-11-08
The last version of Ubuntu that worked "out of the box" on my computer was 6.06.

Every 7.x version left me with a black login screen. 

I installed 8.10 today and it's unable to start the x-server after install (something about no screen present?) and it only offered 640x480 resolution and no sound when running from the 8.10 live-CD

My desktop consists of
Asus motherboard AMD-64 4200+ X2 (socket 939)
2GB RAM
A couple SATA HDD's
SB Audigy soundcard 
2X nVidia 6800GT's SLI bridged
Logitech Bluetooth Mx5000 mouse and keyboard combo
Samsung 960BF LCD monitor

Nothing exotic, but it is all old, too old I guess...:(

---

### Post by Martin Fierro on 2008-11-08
may be i will ask you a very simple question, but.. did you picked up the right architecture for your machine? You have a AMD64 :-)
Best regards.

---

### Post by Yashiro on 2008-11-08
No, it's not too old.

Try installing with one video card in. The rest of your spec is similar to mine and 8.04 runs OK.

---

### Post by DGortze380 on 2008-11-08
> **Qwertinsky said:**
> The last version of Ubuntu that worked "out of the box" on my computer was 6.06.

Every 7.x version left me with a black login screen. 

I installed 8.10 today and it's unable to start the x-server after install (something about no screen present?) and it only offered 640x480 resolution and no sound when running from the 8.10 live-CD

My desktop consists of
Asus motherboard AMD-64 4200+ X2 (socket 939)
2GB RAM
A couple SATA HDD's
SB Audigy soundcard 
2X nVidia 6800GT's SLI bridged
Logitech Bluetooth Mx5000 mouse and keyboard combo
Samsung 960BF LCD monitor

Nothing exotic, but it is all old, too old I guess...:(

Your hardware is not that old (in comparison to some of the machines I'm running ubuntu on). What is your graphics card? Sounds like a 'simple' driver issue.

EDIT: I'm blind. I see you card now. Back after a google search.

SLI issue?    - [http://ubuntuforums.org/archive/index.php/t-425717.html](http://ubuntuforums.org/archive/index.php/t-425717.html)
Driver?       - [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/177.70-0ubuntu1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/177.70-0ubuntu1)
Modify XOrg?  - [http://www.linuxquestions.org/questions/linux-games-33/nvidia-sli-on-linux-499317/](http://www.linuxquestions.org/questions/linux-games-33/nvidia-sli-on-linux-499317/)

---

### Post by mkvnmtr on 2008-11-08
I don't think it is a matter of age. You have plenty of resourses to run Ubuntu. You have more than me and I am running 8.04 on a powerpc Mac. I haven't been able to get 8.10 to boot yet. I am sure it is a matter of you just working through the problems one by one. For me I am just going to wait a while and try again. Give them a chance to do some updates.

---

### Post by hictio on 2008-11-08
*Anything* with 2 GB of RAM is not old :D
My desktop runs on a Pentium II @ 350 MHz with 512 MB of RAM with Hardy; won't upgrade to Intrepid because the video card, a GeForce2 MX/MX 400 won't deliver 3D with this release.

---

### Post by DGortze380 on 2008-11-08
> **Martin Fierro said:**
> may be i will ask you a very simple question, but.. did you picked up the right architecture for your machine? You have a AMD64 :-)
Best regards.

he does not need the AMD64 build. x86 will run fine on his machine.

Now, if you want AMD64, you could run it.

---

### Post by Iowan on 2008-11-08
This machine is a Dell Dimension 4100 - 866Mhz.  I don't remember if I've upped the memory from the 256M it came with.  It runs 7.10 - my only upgrade attempt from 7.04.


Gee, got a phone call, and 5 posts sneaked in...

---

### Post by ben2talk on 2008-11-08
[QUOTE=Qwertinsky;6132587]The last version of Ubuntu that worked "out of the box" on my computer was 6.06.

Every 7.x version left me with a black login screen. 
*******************************************
Firstly, I'd look at the rather non-standard '2X nVidia 6800GT's SLI bridged' configuration. You could remove the video cards and install, perhaps put one in - it's easy enough to try installing without, putting it in and powering up again.


Perhaps also you're rather too hooked on the word 'ubuntu'. There are many flavours you should be trying out! Ubuntu often fails with older hardware in this respect, focussing instead on the notebook market - it's very important to be functional on newer machines, and laptops are apparently taking over the sales market now.

Unfortunately, in doing this, they are losing out with older hardware.

Did you try any alternatives? You could start by trying a variety of Debian based distro's for familiar territory. Have you tried a SuSe disk?

Something I am starting to love and respect is the matter of choice. I have stopped saying I use 'ubuntu' or anything else. I am now a 'linux' user, and try to avoid saying that I use KDE or gnome - because it leads to division, and people often try to be sheep and follow the flock - as they did with Microsoft. This is not a good thing. Everyone seems to be madly in love with Firefox - how many people try to avoid it, or use alternatives in order to maintain some kind of balance?

Try something else - you have many choices! Don't be so keen to choose! It only takes about 20 to 30 minutes to try out an installation disk - so get a few torrents running, and plan to spend up to 5 hours installing from ten different disks.:KS

---

### Post by kansasnoob on 2008-11-08
> **Qwertinsky said:**
> The last version of Ubuntu that worked "out of the box" on my computer was 6.06.

Every 7.x version left me with a black login screen. 

I installed 8.10 today and it's unable to start the x-server after install (something about no screen present?) and it only offered 640x480 resolution and no sound when running from the 8.10 live-CD

My desktop consists of
Asus motherboard AMD-64 4200+ X2 (socket 939)
2GB RAM
A couple SATA HDD's
SB Audigy soundcard 
2X nVidia 6800GT's SLI bridged
Logitech Bluetooth Mx5000 mouse and keyboard combo
Samsung 960BF LCD monitor

Nothing exotic, but it is all old, too old I guess...:(

If you still have 8.10 installed try this to resolve the x-server problem:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by kansasnoob on 2008-11-08
This is a good start also:

[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

---

### Post by kansasnoob on 2008-11-08
Also, since you're using a bluetooth keyboard/mouse setup look here:

> X.Org Input Devices

The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system). 

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by islandstone on 2008-11-08
> **ben2talk said:**
> [QUOTE=Qwertinsky;6132587] Everyone seems to be madly in love with Firefox - how many people try to avoid it, or use alternatives in order to maintain some kind of balance?

Try something else -.:KS

Yeah Opera's always worked for me , it loves Linux , and is a great alternate to IE on Windows nowadays.
 I've had great success with the current SUSE 11.0 distro also , As a sortofnewbie I found SUSE incredibly stable and easy to use , but sadly lacked the intuitiveness of Ubuntu for hardware detection and drivers etc. I never got my Broadcom BCM43XG to work , nor my printer (ip4600) .

Ubuntu 8.10 was a no go , black screen at login whatever I tried , my graphics is onboard Intel 82845G/GL , not a hope of 3D.

My sytem is OLD , P4 2.8ghz ,1GB ram , MicroStar mobo Neon,80gb IDE hardrive ,  but so far Hardy is smooth except for the graphics again , I cannot select Normal or Extra Visual effects.

---

### Post by kansasnoob on 2008-11-08
If we can get your video resolution fixed then we should easily be able to get past the audio problem, probably by installing ld10k1 and adding gnome-alsamixer and possibly applying the pulse audio fixes here:

[http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid](http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid)

---

### Post by Qwertinsky on 2008-11-08
> **Martin Fierro said:**
> may be i will ask you a very simple question, but.. did you picked up the right architecture for your machine? You have a AMD64 :-)
Best regards.

Actually I picked the 32bit version because past experience with 64bit Ubuntu required too many hoops to jump through to get anything to work...

---

### Post by Zimmer on 2008-11-08
xorg.conf works a bit different from 6.06 to 8.*  
Autodetection from components (particularly the monitor) plays a major part in setting metamodes and other weird new stuff that the old xorg tweaks will not touch.

You will need to look at the xorg.log (probably from the live CD boot) to get a clue as to what is going on. The new X server has a nasty habit of ignoring your old style crafted xorg.conf(fortunately the log will tell you if it has!) and then relies on the EDID info from your monitor (which could be wrong/corrupt/missing/mis interpreted etc..) to set your 'valid' resolution(s) ...

I found the nvidia-settings program ok for writing the correct res info to the xorg.conf, once I had a working res and the nvidia drivers loaded.

I now use EnvyNG for the driver loading....

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html)

is where I found the option to force X to ignore the EDID data and use the settings in my old xorg.conf file.

But first, find out what the xorg.log has to say..

---

### Post by Qwertinsky on 2008-11-08
> **Zimmer said:**
> xorg.conf works a bit different from 6.06 to 8.*  
Autodetection from components (particularly the monitor) plays a major part in setting metamodes and other weird new stuff that the old xorg tweaks will not touch.

You will need to look at the xorg.log (probably from the live CD boot) to get a clue as to what is going on. The new X server has a nasty habit of ignoring your old style crafted xorg.conf(fortunately the log will tell you if it has!) and then relies on the EDID info from your monitor (which could be wrong/corrupt/missing/mis interpreted etc..) to set your 'valid' resolution(s) ...

I found the nvidia-settings program ok for writing the correct res info to the xorg.conf, once I had a working res and the nvidia drivers loaded.

I now use EnvyNG for the driver loading....

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html)

is where I found the option to force X to ignore the EDID data and use the settings in my old xorg.conf file.

But first, find out what the xorg.log has to say..

Where do I find the xorg.log? It is not in /etc/X11/

---

### Post by Qwertinsky on 2008-11-08
> **kansasnoob said:**
> This is a good start also:

[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

Oh my, I dont know where to begin here...

The "quick fix" reconfigure command did not help at all.

looking at my xorg.conf the sections are empty except for "configured"?

Section "Device"
Identifier "Configured Video Device"
End Section

Section "Monitor"
Identifier "Configured Monitor"
End Section

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
End Section

Well I don't know what to do since I am stuck t the console it impossible to download and install some of the things they suggested and most of the links in the How To seem dead anyway...

---

### Post by DGortze380 on 2008-11-08
> **Qwertinsky said:**
> Oh my, I dont know where to begin here...

The "quick fix" reconfigure command did not help at all.

looking at my xorg.conf the sections are empty except for "configured"?

Section "Device"
Identifier "Configured Video Device"
End Section

Section "Monitor"
Identifier "Configured Monitor"
End Section

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
End Section

Well I don't know what to do since I am stuck t the console it impossible to download and install some of the things they suggested and most of the links in the How To seem dead anyway...

I really suspect an SLI problem. I would suggest you start by removing one card, troubleshooting that (if you even need to, it may just work), then working on SLI after you get one card going.

---

### Post by the Arbiter on 2008-11-08
hi im th arbiter and i have a ? about xubuntu... does it run good on a computer with 4gb hard, drive 352mb ram, idont know what graphics card is in there ... 
please help

---

### Post by DGortze380 on 2008-11-08
> **the Arbiter said:**
> hi im th arbiter and i have a ? about xubuntu... does it run good on a computer with 4gb hard, drive 352mb ram, idont know what graphics card is in there ... 
please help

Please search, and start a separate thread for each specific question you may have. It is not appropriate to hi-jack other threads.

---

### Post by handydan918 on 2008-11-08
> **hictio said:**
> *Anything* with 2 GB of RAM is not old :D


+1

I wish I had a machine that "old".

---

### Post by Zimmer on 2008-11-09
The log can be viewed from System>Administration>System log  or directly at location  var/log.

---

