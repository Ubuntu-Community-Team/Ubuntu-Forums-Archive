---
title: "Just installed ubuntu, 100% new to linux having a few problems."
date: 2016-07-01
forum: New to Ubuntu
---

### Post by jon932 on 2016-07-01
Hey I'm a total noob to linux. I just installed it today and I'm having a few problems. First of all resizing screens is really slow. like painfully slow. For some windows it can take over 30 seconds. I took pictures:

[[IMG]https://s32.postimg.org/s7g42htn5/20160701_174658.jpg[/IMG]]("https://postimg.org/image/s7g42htn5/") [[IMG]https://s32.postimg.org/de3pqoqwx/20160701_174707.jpg[/IMG]]("https://postimg.org/image/de3pqoqwx/") [[IMG]https://s31.postimg.org/529pciayv/20160701_174722.jpg[/IMG]]("https://postimg.org/image/529pciayv/") [[IMG]https://s31.postimg.org/xuflgra3b/20160701_174733.jpg[/IMG]]("https://postimg.org/image/xuflgra3b/")

The clock on the left shows the timer in seconds. Now this window was an extreme example but usually there is like a .5 to .8 second delay when resizing a window. I tried googling it and most of the other topics I saw were unsolved but people always asked how the resizing was done, I resized my windows with the mouse. 
*Edit: just noticed how small the pictures are. If you don't want to click to enlarge them basically this window took about 40 sec to resize.

Another problem I'm having is every time I turn on the computer it takes me to a menu called gnu grub. Most of the options there lead to computer just staying at a pink screen. Here are some pictures:

[[IMG]https://s31.postimg.org/niwaxyyon/20160701_165440.jpg[/IMG]]("https://postimg.org/image/niwaxyyon/") [[IMG]https://s32.postimg.org/th1ujn0td/20160701_165503.jpg[/IMG]]("https://postimg.org/image/th1ujn0td/")

In the first screen if I select ubuntu it leads to a perma pink screen. If I select advanced options it takes me to the second picture. Here every option except the recovery mode leads to a permanent pink screen. After that it leads to the recovery menu. Here I have to press "resume normal boot" twice for the computer to actually boot. The first time I press it, the computer starts to boot but then stops and returns to the recovery menu. 

While booting a bunch of things flash by the screen and it always says "volume group "ubuntu-vg" not found cannot process volume group ubuntu-vg".

Lastly for some reason the computer will take one of my CPU's to 100% while all the others remain between 0% and 3%. 

I feel like these problems might be the types of problems a dated computer might have, but my pc isn't old. Here are my system specs:

Ram: 16gb 
processor: Intel® Core&#8482; i7-5930K CPU @ 3.50GHz × 12
Graphics: GeForce GTX TITAN X/PCIe/SSE2
OS Type: 64-bit
Disk: 967.6 GB

Ok while copying the system specs from system details I noticed its not picking up my intel ssd. 

I doubt all of these things are intended on ubuntus end. I know its a lot of things so you guys don't have to help me with all of them, but if I could fix one or two of these issues it'd be great.

Edit: that windows that took 40sec to resize is what popped up when I tried to install netbeans / java jdk. It's taken more than an hour to install is that normal?

---

### Post by tabakisp on 2016-07-01
I would suggest to run a live cd, run gparted, partition and format your ssd and then re-install. Your installation is not done correctly. When you choose the drive for installation, (or partitioning), be sure it's the right one.

---

### Post by jon932 on 2016-07-01
I did choose the right one. I don't want to install it into the sdd. Were you suggesting I reinstall because you thought I'd want to boot from the ssd, or are there just too many problems that the easiest fix would be a reinstall? Also I'd only have linux on this pc. I don't intend on keeping windows.

---

### Post by grahammechanical on 2016-07-01
There are a couple of things that are unusual about your installation.

1) When Ubuntu is the only OS on the machine we do not usually get a boot menu (Grub). The boot loader is installed but it is hidden.
2) At the bottom of the menu this is written: The highlighted entry will be executed automatically in 24s. The default is usually 10 seconds and it counts down to zero. Unless we press a key such as the space bar.

Are you unable to load into Ubuntu? The Details page will tell us the size of the partition Ubuntu is installed in. No more than that. As for the slowness of screen redraws it could be down to a video driver conflict. 

Go to System Settings>Software & Updates>Additional Drivers tab and change video drivers. You need to be connected to the internet and to allow the utility time to do its job.

Regards.

---

### Post by jon932 on 2016-07-01
yea the drivers should all be up to date. I went into that tab earlier and enabled the drivers for my wifi, graphics card, and cpu. I know they're enabled because I have wifi and the screen resolution got fixed after a restart, and by load into Ubuntu do you mean access my computer like get to the desktop and stuff? I can do that. I also went into ubuntu software -> updates and updated a bunch of things such as the OS. I'm not fully sure what you mean by load into ubuntu, but I can only access my computer through recovery mode.

---

### Post by tabakisp on 2016-07-02
@jon932 I suggested a re-install because I thought you wanted to boot from the SSD. 

Also, did you manually partition /home, /swap etc or did you just used the whole drive? 

At first I thought it's a GPU driver problem. But maybe your /home partition is full. A screenshot with your partitions from gparted and the Details page would be helpful. 

What @grahammechanical meant is that, if you only have 1 OS installed (Ubuntu in your case), the grub menu shouldn't appear. It should boot right to your login screen/desktop.

---

### Post by grahammechanical on 2016-07-02
If you are using recovery mode to get to the desktop then it is highly likely that a fall back open source video driver is being used and that video driver is not very good at doing 3D rendering. It is slow. But at least you are at the desktop which is better than a black screen. I think that the screen resizing issue is a distraction from the real problem of only being able to load Ubuntu by using Advanced options>recovery mode.

This is of concern

> it always says "volume group "ubuntu-vg" not found cannot process volume group ubuntu-vg".

I have no experience of installing & using Ubuntu with Logical Volume Management (LVM). I think you choose that option during the installation process.

You could try going to Advanced options and selecting Ubuntu with Linux 4.4.0-21-generic to see if that solves the problems. If it does then load with that option until such a time as there is another upgrade to the Linux kernel that may or may not fix the problems.

Regards

---

### Post by TheFu on 2016-07-02
I always use LVM on all physical machine installs.  Can't imagine what is happening here, but I suspect grub was installed on a different HDD and that the BIOS/EFI has to search it out to boot.  If the installed disk isn't /dev/sda ... I can see where confusion might happen.

Another issue might be if both whole disk encryption (which forces LVM) AND encrypted HOME was selected during the install.  I've never selected both and after a lots of slowness with HOME directory encryption, I don't use that anymore. It has other issues too, at least for my needs. Automatic system backups weren't possible, for example, but that could have been user error on my part.

I've seen Core i7 machines brought to their knees, but only inside a virtual machine. It was really sad. Can't recall the exact issue, but think it was related to running a 3d accel desktop when that wasn't working in the VM-hypervisor.  The solution for that install was to use any non-Unity/Gnome3 flavor of ubuntu instead.  Today, I'd suggest Ubuntu-Mate -  a fresh OS install isn't necessary to use a different GUI. With Linux, the GUI is **not** the OS.

Hope fully someone can distill this down to something understandable for the OP.  I'm not good for folks new to Linux.

---

