---
title: "How do I upgrade to kernel 2.6.17.x using update manager"
date: 2006-07-04
forum: Repositories &amp; Backports
---

### Post by leo_m on 2006-07-04
I am stuck with the kernel 2.6.15-25-686 - an effort at update says that everything is up-to-date.

My TV tuner card is supported only in 2.6.17.x (perhaps), certainly not in 2.6.15; so I wish to upgrade the saa7134 driver.  That is the reason behind trying to update the kernel in a clean manner.

Kindly guide.  I have removed Windows entirely and want to watch the crucial world cup matches using the existing LifeView DVB-T mini-PCI hybrid tv card on my computer.

---

### Post by Dr. Nick on 2006-07-04
Once you are on a "final release" version you really dont get kernel updates, You can try these instructions for the 2.6.16 and modify them
[http://ubuntuforums.org/showthread.php?t=157560&highlight=2.6.17]("http://ubuntuforums.org/showthread.php?t=157560&highlight=2.6.17")

Other than that you would have to enable the edgy repos which is the next release of ubuntu still in developement to get the 2.6.17 kernels.

EDIT
[http://ubuntuforums.org/showthread.php?t=200470&page=4&highlight=2.6.17](http://ubuntuforums.org/showthread.php?t=200470&page=4&highlight=2.6.17)

They are trying to get it done, no releases yet

---

### Post by FenrisAbraxas on 2006-07-04
You should download the latest kernel image from [www.kernel.org](www.kernel.org) then copy it to /usr/src/ then decropress it with:

```
sudo tar --bzip2 -xvf linux-blahblah.bz2

```

Now install the packages to compile from source:
```
sudo apt-get update
sudo apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev bin86
```
Then make the symbolic link with:

> sudo ln -s linux-2.16.17.bleh/ linux

After that, change into the new directory:

> cd /usr/src/linux

And finally type:

> make xconfig

Select all the options you want (look for kernel guides if u don't know how to compile your kernel).

And to actually have your new kernel up and running do this:

```
sudo make-kpkg clean

sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
```

You can change to -custom to anything you want.

This will make you a .deb package that as you are guessing yes! it can install with:

```
 dpkg -i kernel-image-blah blah.deb 
```

Reboot and voila!

\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ 

More info in this thread:
[http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

Just another thing:

Select your processor type and if you don't know what you need and what you don't just add the new driver and leave everything like it is.

---

### Post by leo_m on 2006-07-04
Is there an alternative method whereby I can just upgrade the saa7134 driver without going through the hassle of confguring and building the kernel from scratch?

---

### Post by leo_m on 2006-07-04
Okay, I compiled and installed the kernel as per the instructions given.

Now I am going to reboot and then see if my TV-card is supported now.

The instructions provided were good - I used the earlier configuration of my kernel (the last one installed by Kubuntu auto-updater).

Thanks.

---

### Post by leo_m on 2006-07-04
No, the TV-Card (LifeView DVB-T mini-PCI Hybrid) is not supported yet...the PCI subsystem is 5168:3307; card no. 94 supports 5168:3306 although that's a cardbus card, not a mini-PCI card...close, but not quite there?

---

### Post by leo_m on 2006-07-04
However, though the kernel 2.6.17 was significantly faster in booting up, I wonder if I should use this because vmware server stopped working and I had to recompile that after booting up in the previous version of the kernel (2.6.15-25).  Also, the wireless connection was not brought up.  I had used the same old (2.6.15-25) configuration for the new kernel as well and if wireless was working there, wireless should have worked in this version as well. I guess I shall just uninstall this version (2.6.17) sometime later because it did not fulfil the primary purpose, viz., supporting my tv-tuner card.

---

### Post by Dr. Nick on 2006-07-04
yeah you may aswell rever unless you feel like fixing all the other things.

If you were using ndiswrapper for your wireless then you would have had to recompile ndiswrapper against your new kernel, even though you saved the previous config. If it was a built in kernel module it should have worked though, not sure why it wouldnt.

Compiling kernels is sorta cool, but it can get tedious and annoying at times. I ususally just wait for them to show up in repos before updating, but if I was in your case of trying to get a piece of hardware supported then compiling it is worth a shot.

---

### Post by leo_m on 2006-07-06
I tried the instructions at [http://ubuntuforums.org/showthread.p...ghlight=2.6.17]("http://ubuntuforums.org/showthread.php?t=157560&highlight=2.6.17").  The instructions seem to be fine.  But there seems to be something wrong with the default configuration from /boot for the earlier version of the kernel that I copy to quickly create a new configuration.  After I boot up with the newly compiled kernel 2.6.17.3, I do not see any splash image, nor does my wireless work.  I do not know what else might be broken.  The dmesg tells that it does try to load the driver for my wireless card but cannot find the firmware...and I thought the firmware location is common across kernel versions (for hotplug firmware).  I am not using any ndiswrapper nor do I have an idea of what it is and I do not think an ndiswrapper is required in my case (an Intel ipw2200 based card). Kindly guide.

I am again recompiling the kernel to try to get the splash image at boot up - I had only kept the 224 color image option earlier, I have enabled 16 color image option now.

Also, since a few things are not being properly done after I have 2.6.17.3, as mentioned above, is it possible in the interim (till I find how to fix these when I use 2.6.17.3), to just load the new module for TV card - saa7134, when I load the old kernel, viz., saa7134-kernel 2.6.17.3 version when I load kernel 2.6.15-25 (I have made a few changes *locally* to the saa7134 files in a bid to get my TV card to function in Ubuntu)?

[update]
I do not get splash image even now, output when I try to setup kernel-image:

```

root@leo:/usr/src# sudo dpkg -i kernel-image-2.6.17.3_x86.TVonly_i386.deb
Selecting previously deselected package kernel-image-2.6.17.3.
(Reading database ... 116895 files and directories currently installed.)
Unpacking kernel-image-2.6.17.3 (from kernel-image-2.6.17.3_x86.TVonly_i386.deb) ...
Setting up kernel-image-2.6.17.3 (x86.TVonly) ...
/initrd.img does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
/vmlinuz does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17.3
Found kernel: /boot/vmlinuz-2.6.15-25-686
Found kernel: /boot/vmlinuz-2.6.15-25-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

---

