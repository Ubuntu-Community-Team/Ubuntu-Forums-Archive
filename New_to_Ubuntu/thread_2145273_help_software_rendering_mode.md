---
title: "help software rendering mode"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by Mizz Shadow Kat on 2013-05-14
[COLOR=#000000][FONT=century gothic][SIZE=4]Hi, although I’ve been running Linux for over 2 years now I’m still not overly confidant with the command line and a few other aspects, (so please can you keep it simple for me =) ) I’m also not entirely sure what I’m talking about I just know I've got an issue and its probably to do with my drivers. OK I've just got a new monitor that works in HD although I'm not currently using an HDMI cable, I'm still using my old VGA. my OS is Ubuntu 12.10 (but I'm using a cinnamon desktop over the top of it) and my graphics card is NVIDIA GT430. my graphics card is HD compatible, AVI i think. (but again i don’t know enough to be sure on that) since I've plugged my new monitor in i keep getting this message 'Running in software rendering mode, the system is currently running with out video hardware acceleration and as a result you may observe much higher CPU usage' witch is true ive checked my CPU usage in comparison to what it was before and its a lot higher some heavy graphics games i cant run because it freezes the screen. ive found what i think are solutions but i don’t understand the answers. like i said im not good on the command line and i don’t know a lot about this subject. i relay hope some one can help me, =) .[/SIZE][/FONT][/COLOR]

---

### Post by DuckHook on 2013-05-14
Hi Mizz Shadow Kat,

Welcome to the forums.

I'm afraid that we can't avoid the command line when troubleshooting, but I'll try to keep it minimal. Please post output of:```
lspci -vk | grep -iA13 vga | grep -i Kernel
``````
dpkg -l | grep -E '^ii' | grep nvidia
```In Linux, case matters, so, to avoid typos, just copy and paste these commands into a terminal. The last command may return nothing. If so, just report this.

Please also tell us make and model of your monitor, and make and model of your computer.

---

### Post by Mizz Shadow Kat on 2013-05-15
=) ty, this is my output of the above; 
   
 Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

ii  nvidia-current                            304.88-0ubuntu0.1                         i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.88-0ubuntu0.2                         i386         Tool for configuring the NVIDIA graphics driver

the monitor make is a celcus 22inch full HD 
and my pc is made up of customesed random stuff, (more or less home built)
if u want info on specific hard wear i can find out 

hope thats the info u needed?
=)

---

### Post by DuckHook on 2013-05-15
You actually do have NVIDIA drivers installed already. I had thought that your current problems arose from only having the open-source drivers, but this is not so. Are you running 32-bit or 64-bit Ubuntu?

---

### Post by DuckHook on 2013-05-15
It's getting late here and I'm about to close down for the night, but I wanted to give you [this]("http://www.geforce.com/drivers/results/61453") link, which links to the NVIDIA driver site. It is the latest 319.17 driver which reports as supporting your video card. The site I've linked to is for the 64-bit driver. If you are running 32-bit Ubuntu, you will have to search the NVidia site for the correct 32-bit driver. If you agree to NVIDIA's terms and download it, you can install it and replace your current driver. Hopefully, this will solve your display issue. For instructions on installing a driver, see [this]("https://help.ubuntu.com/community/NvidiaManual").

As you can see, it is very important that you have full backups of your important data before changing any driver. Video drivers are the second leading cause of extreme distress among users (after partitioning), and if you decide to change drivers without proper backups of your critical data... well... you may not be able to recover this data if the new driver borks your system.

---

### Post by Mizz Shadow Kat on 2013-05-15
thank u so much for ur help i think im running 32 bit, lol yeah partitions have done nothing but cause mgreaf, so i totaly get that, and yeah always a go idea to back up regualy, im sorfell asleep lastnight i'll try this out now =) let u know if it works

---

### Post by r m h on 2013-06-09
First and foremost, if this suddenly appeared when the latest cinnamon (1.8.x) installed through the update manager, check that you are not logging in under cinnamon 2D.  Cinnamon 2D is now defaulting to software rendering mode.  Log out and log back in using cinnamon 3D and see if that fixes your problem.

Previous versions of cinnamon were dodgy on my workstation so I was using 2D mode.  Now with 1.8.x, 3D mode appears to work like I expect on my workstation.

Further, as part of my debugging of this issue on my workstation, I uncovered another gem - I could remove the fglrx AMD proprietary drivers on my workstation and keep multi-monitor support AND eliminate the screenshot issue that was capturing the desktop background and not the window contents I wanted.

Note: at this point I had used the fglrx drivers to set up a desktop across 2 24" LCD monitors (3840x1200 resolution)

Here's what I did after getting annoyed at the "cinnamon running in software rendering mode" issue:
> 
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK.20130609
$ sudo apt-get remove --purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
<reboot>
<login using cinnamon 3D mode>


Hope that helps

edit: I'm running Ubuntu 12.04 LTS 64-bit

---

