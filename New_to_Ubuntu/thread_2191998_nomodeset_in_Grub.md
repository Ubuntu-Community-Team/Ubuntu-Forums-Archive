---
title: "nomodeset in Grub"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by jj.wauters on 2013-12-05
[SIZE=4][FONT=arial]When I remove nomodeset from Grub the GUI in Ubuntu 12.04 is not visible.
I seem to have doubles in the video drivers.

This is reported by dkms status ;
nvidia-319, 319.32, 3.8.0-33-generic, x86_64: installed
nvidia-319, 319.32, 3.8.0-34-generic, x86_64: installed
nvidia-319-updates, 319.32, 3.8.0-33-generic, x86_64: installed
nvidia-319-updates, 319.32, 3.8.0-34-generic, x86_64: installed
nvidia, 331.20, 3.8.0-33-generic, x86_64: installed
nvidia, 331.20, 3.8.0-34-generic, x86_64: installed[/FONT][/SIZE]

[SIZE=4][FONT=arial]How can I clean this up ???[/FONT][/SIZE]

---

### Post by bashiergui on 2013-12-05
You'll notice that those are not *really* duplicates if you look closely. 
....3.8.0-[COLOR=#ff0000]33[/COLOR]-generic.....
....3.8.0-[COLOR=#ff0000]34[/COLOR]-generic.....

those numbers indicate kernel versions. Every time the kernel is updated your system automatically keeps the previous versions in case the update breaks everything and you want to roll back. 

I would recommend keeping at least 1 previous version. When you have numerous versions then the easiest way to get rid of them is to use Synaptic Package Manager. Search for "generic" and then you can uninstall the oldest ones. After that update grub and the old ones will be gone.

---

### Post by fantab on 2013-12-06
You must install proprietory driver your Graphics card or install opensource drivers.
'Nomodeset' is a temporary solution/workaround to boot Ubuntu in a 'failsafe' graphics mode. Once booted you'll have install the appropriate graphic drivers.
You can do this from 'Additional Drivers' in 'Software Center' ->Edit->software sources ->additional drivers.

---

### Post by Bucky Ball on 2013-12-06
If you want nomodset permanently, set it in /etc/grub/default like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
```

... and change it to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet nomodset"
```

You don't need to install third-party drivers if you don't need them.

---

### Post by jj.wauters on 2013-12-06
Hello Fantab,

I understand Bashiersgui's comment that the kernel is keeping track of the different drivers/updates installed, and I suppose the kernel is loading the last one on startup.
I also understand your comment that using nomodeset is just a workaround.
But unfortunately nomodeset is the only working solution for me until now.
After installing Ubuntu 12.04 nvidia driver 319 was automatically installed but I was stucked with a black screen. Same after updating this driver. Same after getting the last driver 331.20 from the manufacturer.
Just before sending this reply I started Additional Drivers and installed the non activated nvidia binary Xorg driver (screenshot). Same result.
(ps: I don't see an Edit button in Additional Drivers)

Can you help me further?

---

### Post by Bucky Ball on 2013-12-06
Read the post above yours, #4.

PS: Try enabling the Xorg driver, not the updates one.

---

### Post by fantab on 2013-12-06
I don't have Nvidia card so I don't know much about the issue... 
You can take your query to:[ http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")
Also go through that thread it might be of some assistance to you.

Lets hope some one with more experience with Nvidia offers a better solution.

Good Luck...

---

### Post by oldfred on 2013-12-06
I have only installed the nVidia drivers offered by Ubuntu in the repositories. But my nVidia card is older now.
But only the very newest nVidia card may need the very newest driver directly from nVidia, as Ubuntu seems to add the newer nVidia drivers pretty quickly now.

When you install from Ubuntu dpkg automatically integrates it into the kernel on updates. If from nVidia directly you may have to manually do the reinstall every time a kernel is updated.

Also the nVidia direct download and Ubuntu repository versions may conflict. If installing a newer version best to un-install all old nVidia drivers and start clean with one new one.

Versions I show I installed are now old, as I have updated also. Install from repository the version you prefer from its list.

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

   # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

   # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 
nvidia-settings-experimental-310

---

### Post by efflandt on 2013-12-06
How did you end up with 3 different versions of drivers nvidia-310, nvidia-319-updates, and 331.20? One time I messed up a system trying to switch nvidia drivers using apt-get, ended up with multiple versions, could not purge them properly, and ended up reinstalling Ubuntu. What video card/chip do you have that you feel you need a backported (?) kernel and 331 nvidia drivers?

I am using nvidia-expermental-310 which in 12.04 all shows same nvidia version for each mainstream kernel version for: dkms status```
nvidia-319-updates, 319.32, 3.2.0-54-generic, x86_64: installed
nvidia-319-updates, 319.32, 3.2.0-55-generic, x86_64: installed
nvidia-319-updates, 319.32, 3.2.0-56-generic, x86_64: installed
nvidia-319-updates, 319.32, 3.2.0-57-generic, x86_64: installed
```I might have had to use nomodeset while installing 12.04, but not since it was installed (not in GRUB_CMDLINE_LINUX_DEFAULT line).

---

### Post by jj.wauters on 2013-12-07
How did I ? : see #5
From the beginning "System Details" reported  "Graphics unknown"
There are 2 graphic devices in this laptop :
Intel HD Graphics 4600
Nvidia Geforce GT740M
I decided to install the latest Nvidia driver 331.20 hoping the system should recognize the device and in order to take advantage of his Optimus technology.

---

### Post by fantab on 2013-12-07
If you have two graphic cards then its called "**Hybrid Graphics**".
Normally BIOS/UEFI uses one card to boot the OS, the second card is used after the OS has booted and if performance is needed.
In your BIOS/UEFI check what is the default card it uses... Intel supports its cards quite well with open source drivers.

More Info:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[https://wiki.archlinux.org/index.php/Hybrid_graphics](https://wiki.archlinux.org/index.php/Hybrid_graphics)

---

### Post by Bucky Ball on 2013-12-07
This is what you want I believe:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by oldfred on 2013-12-07
The newest nVidia driver only uses the dual video capabilities with new kernel & other supporting software that just is in 13.10 or later. It is not in 12.04.3. 

       Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by jj.wauters on 2013-12-08
Being a newby in Ubuntu it's all very confusing for me. It seems I'm being trapped having a very recent graphic card that's not (yet) supported.
So I plan doing next steps :
1° follow your purge steps until sudo reboot
2° 
OPTION 1°
-follow the Installation/Basic Steps like explained in The Bumblebee project [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
-update the 319 driver (see Bumblebee)
OR
OPTION 2°
- follow the Installation/12.04.3/Nvidia systems steps like explained in [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

In my opinion I should follow Option 1 as in that case the power management is enabled. For the moment my laptop is firmly heated by the card.
Can you give me your opinion on this?

I also have some questions about the purge procedure.
[TABLE="class: outer_border, width: 750"]
[TR]
[TD]# dpkg -l | grep nvidia*
rc  nvidia-319                                  319.32-0ubuntu0.0.1                     NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-319-updates                          319.32-0ubuntu0.0.1                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-331                                  331.20-0ubuntu1~xedgers~precise1        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                               1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-persistenced                         331.20-0ubuntu1~xedgers~precise1        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                0.4.2~hybrid0.0.1                       Tools to enable NVIDIA's Prime
ii  nvidia-settings-319                         331.20-0ubuntu1~xedgers~precise1        Transitional package for nvidia-settings-319
ii  nvidia-settings-319-updates                 319.32-0ubuntu0.0.1                     Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-331                         331.20-0ubuntu1~xedgers~precise1        Tool for configuring the NVIDIA graphics driver
# apt-cache search nvidia-sett*
nvidia-settings - Transitional package for nvidia-settings
nvidia-settings-304 - Tool for configuring the NVIDIA graphics driver
nvidia-settings-304-updates - Tool for configuring the NVIDIA graphics driver
nvidia-settings-319-updates - Tool for configuring the NVIDIA graphics driver
nvidia-settings-experimental-304 - Transitional package for nvidia-settings-experimental-304
nvidia-settings-experimental-310 - Transitional package for nvidia-settings-experimental-310
nvidia-settings-updates - Transitional package for nvidia-settings-updates
nvidia-settings-310 - Transitional package for nvidia-settings-310
nvidia-settings-313 - Transitional package for nvidia-settings-313-
nvidia-settings-319 - Transitional package for nvidia-settings-319
nvidia-settings-331 - Tool for configuring the NVIDIA graphics driver
[/TD]
[/TR]
[/TABLE]

- Does this means that in my case I just have 2 housecleaning commands :
sudo apt-get remove --purge <319.32-0ubuntu0.0.1>
sudo apt-get remove --purge <331.20-0ubuntu1~xedgers~precise1>
??? use brackets or not ?

- By the way : mv /etc/X11/xorg.conf will not work as I have no such a file.
There is a xorg.conf.failsafe file and 2 xorg.conf.backup files. 
Those backup files seems to be created while installing the 331.20 driver as they have the same date.

Thanks in advance for your kind help

---

### Post by oldfred on 2013-12-08
No brackets.
But it looks like you also have the settings files from 304 & experimental-304, 310, 319 etc.
That may be why it is confused?

---

### Post by jj.wauters on 2013-12-10
I followed your purge and install instructions.
After reboot the 304, 310 and 331 drivers were still visible in dpkg.
And my screen was in low resolution (800x600).
Then I tried to activate the Nvidia xorg driver with the same low resolution result.
Hoping on a better result I continued installing Bumblebee.
Now on startup Unity is not opening and I am stucked on a purple Ubuntu screen.


Any suggestions other than wipe Ubuntu and replace by the 310 version???

---

### Post by oldfred on 2013-12-10
Maybe a correction. I think dpkg shows all the versions you can download, not what you have.

But you are showing xedgers? Did you had a ppa to add nVidia drivers? That may keep updating? I have never used the ppa for video drivers but have seen posts with users suggesting it as  another way to download them.


I have not used bumbebee, but I think you have to have nVidia working correctly first.

---

### Post by jj.wauters on 2013-12-22
I tried at least a dozen of re-installations and had always to remove them for one or another reason.
This frustrating job didn't took me several hours, but several days !!!
For the moment I have 2 up and running versions (without using nomodeset in grub) in another partition on my laptop.
During the last install I had to do next :

Install 12.04.3 from live USB
1    reboot
2     no Grub : Windows 8.1 is starting up.
3    reboot
4     boot-repair from USB
5    reboot
6     black screen after Grub
7    reboot
8     sudo apt-get purge nvidia
      sudo apt-get install nvidia-current (version 304 is installed)
9    reboot
10    black screen after grub
11    reboot
12    sudo apt-get purge nvidia* (a lot of nvidia drivers are now purged)
13    reboot
13    grub menu is showing/and can load 12.04 and windows 8

Install 13.1 from live USB in a different partition
1    reboot
2    grub appears but without Windows 8 in the menu
3    reboot
4    boot-repair from USB
5    reboot
6    grub 2 is overwritten by grub 1.9
7    reboot
8    boot-repair from the same USB
9    reboot
10    grub menu is showing/and can load 12.04, 13.10 and windows 8

In each Ubuntu version there is still something wrong with the drivers, but I am already happy to see Unity.
Version 13.10 tells me my graphics = "Intel Haswell Mobile"
Version 12.04 tells me my graphics = "unknown"
Additional drivers in 13.10 mention : "not available"
Additional drivers in 12.04 is proposing to install 2 identical drivers "NVIDIA binary Xorg Driver kernel module"

Because I fear having to re-install everything once again, I am not tending to
- install the latest driver from Nvidia and/or add Bumblebee in 13.10
- install the proposed Nvidia driver in 12.04

In both versions I have a problem with the screen brightness.
At each startup had to push the F3 button to brighten my screen.
I fixed this by inserting "acpi_osi=Linux acpi_backlight=vendor" in grub.
But now the brightness was at 100% and after each startup I had to push the F2 button in order to reduce.
Then I fixed by inserting "echo 25 > /sys/class/backlight/acpi_video0/brightness" in rc.local
(in my case 25 stands for 25% brightness)
This patch was well working untill I installed TLP. 
Now my keyboard is set to QUERTY while set to AZERTY in Systems.
Do you see another solution how to fix the brightness problem?

---

### Post by oldfred on 2013-12-22
So do you have the dual video. Then you may need Intel boot paramters to boot but still install the nVidia driver. 

I have an old nVidia 9600GT and have to use nomodeset to boot until I install the offered nVidia driver from Ubuntu system settings. 
Only a few with very very new nVidia cards may need drivers direct from nVidia. And then you have to manually reinstall on every kernel update. And if you attempt to install from nVidia and from Ubuntu respository or another ppa they will conflict and create even greater issues.

To see video:
       sudo lshw | grep -A 11 display

      
 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

   # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*

      
 apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 
nvidia-settings-experimental-310

But if dual video which I do not have nor know much about:
      
 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by jj.wauters on 2013-12-23
As for the moment I have at least a GUI, I dare not even make more changes to the drivers. 
I will wait for the next 14.04 LTS release in april and hope that this version can handle the problems with double graphic cards during installation.

Apparently my problem with changing language after reboot was not due to an interaction with TLP.
I solved following directions in : [http://askubuntu.com/questions/362973/keyboard-layout-switches-to-english-each-time-i-reboot](http://askubuntu.com/questions/362973/keyboard-layout-switches-to-english-each-time-i-reboot)

And I fixed again the screen brightness by inserting "echo 25 > /sys/class/backlight/acpi_video0/brightness" in rc.local

Thanks for your help, and in the meantime I wish you a Merry Christmas and an Happy New Year

---

