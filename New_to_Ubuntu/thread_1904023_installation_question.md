---
title: "installation question"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by jwagman on 2012-01-03
I downloaded the image of 10.10 32-bit, installed it side-by-side with Windows 7. It would then only boot to Ubuntu. Luckily my Windows Rescue disk allowed me to nuke the Ubuntu installation. Any ideas why this would happen? I would like to try again but not until I know a workaround. TIA.

---

### Post by cortman on 2012-01-03
It's very simple to dual boot. I'm surprised you couldn't boot to Windows before.
Go ahead and install it side-by-side again. Even if (for some inexplicable reason) you can't boot to it at first updating the bootloader to allow you to is very simple.

---

### Post by jwagman on 2012-01-03
> **cortman said:**
> It's very simple to dual boot. I'm surprised you couldn't boot to Windows before.
Go ahead and install it side-by-side again. Even if (for some inexplicable reason) you can't boot to it at first updating the bootloader to allow you to is very simple.

Just to make me feel better, where can I get simple explanation of the workings of the bootloader and to switch to dual-boot? Thanks.

---

### Post by cortman on 2012-01-03
Sure! It's good not to go on blind faith with things like bootloaders, etc.

I found [this decent tutorial]("http://www.dedoimedo.com/computers/grub.html"). FTR, if you can boot to Ubuntu but not Windows it's just a matter of installing GRUB to the MBR. Which can be accomplished with a single command.

---

### Post by GregA on 2012-01-04
Here's just a short recap of the standard way I've installed dual boots on my last 3 systems:

>   First, clean the cruft and excess from your windows install.   Would recommend a backup to external device such as large capacity Flash stick or HD SD card.,
>   Next, run the windows defrag program.,
>   Next, use the windows provided application to resize (shrink the partition).  This is especially recommended for Windows 7.
>   Next, obtain and use a good partition manager application (I like Parted Magic Live Linux CD (see distrowatch.com for download).  Another good live CD is Knoppix.   The actual program on these CD's is called "gparted").,
>   Next, using gparted, partition your hard drive into 2 or 3 partitions, and add a small partion of 2-4 gb's for swap.  Note - - if you haven't used a partion manager before, just google for YouTube tutorial videos).,
>   Next, install your linux distro (I recommend "Kubuntu" for new Linux users).  The install CD will allow you to choose the partition to install it to.  Don't use the "install beside existing OS" option, instead, use the custom install option.
>   Finally, during the install process, a couple things to remember, if possible - be internet connected (wired or wireless), and when prompted, be sure to install the bootloader (grub2) to the Master Boot Record (MBR).  The proper place to locate (mount) Grub will be on the first sector of the first primary partion (typically sda1).

Now, when you reboot your system, it will load grub, and offer you a list to choose what OS to load (it will also show a couple other options, but you'll get the gist of it).

One last point, right after you clean up and reduce the windows partion, be sure to reboot and test that windows will load.   On this first reboot, windows may prompt to boot in safe mode, or take slightly longer to load-up, but that is just a one time thing.  Once windows is running, just log off as normal, and subsequent restarts will be normal.

Hope this helps.

---

### Post by anewguy on 2012-01-04
This link contains a small but very important discussion on installing Ubuntu for dual-bot with Windows 7 (*must* follow this if your Windows is Windows 7):

[http://ubuntuforums.org/showthread.php?t=1894174]("http://ubuntuforums.org/showthread.php?t=1894174")

---

