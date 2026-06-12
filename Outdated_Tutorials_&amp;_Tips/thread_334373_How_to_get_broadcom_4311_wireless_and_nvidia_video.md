---
title: "How to get broadcom 4311 wireless and nvidia video card to work"
date: 2007-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by twade on 2007-01-08
Please forgive any errors in this post, I still consider myself a relative noobie, but rapidly becoming less green.  I also don't have a lot of time to check up on my posts, but I'll do my best.

I'm working on a compaq presario v3010ca (NVIDIA motherboard and GeForce Go 6150 graphics card with a broadcom bcm4311 wireless card and running 32-bit Kubuntu edgy)  

This is a how to on how to get edgy to work with NVIDIA and BCM4311 working at the same time.  These two components appeared to play nice in Dapper with ndiswrapper, but in Edgy they don't.  An additional benefit is that this procedure appears to have enabled the headphone jack, though you will still have to manually select it through kmix.

the problem is discussed in these threads:
[http://www.nvnews.net/vbulletin/showthread.php?t=48327&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=48327&page=2)
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57355](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57355)

These report that the conflict is fixed with the following combination:
Kernel 2.6.20-rc3
ndiswrapper 1.34rc2
NVIDIA-Linux-x86-1.0-9631
[B]
Step 1[/B]: Fresh and clean Edgy install

Ensure that no proprietary drivers are being used to drive the video card.
i.e.
make sure that /etc/X11/xorg.conf has a section that looks like:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          **"vesa"**
        BusID           "PCI:0:5:0"
EndSection
```
and not like:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         **"nvidia"**
EndSection
```


**Step 2**: Get 2.6.20-rc3 (or rc4) kernel from [www.kernel.org](www.kernel.org)
note: this is a bleading edge kernel, proceed at your own risk!

**Step 3**: Compile and install new kernel

There are various how-to's available:
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
[http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

I'll summarize what worked for me.
[B]
3.1[/B]
get neccessary packages (Not sure which are necessary or optional)
```
sudo apt-get update
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
```

change a symbolic link (again, I'm not sure how necessary this is)
```
rm -f /bin/sh
ln -s /bin/bash /bin/sh
```

**3.2**
Download the kernel from [http://www.kernel.org/pub/linux/kernel/v2.6/testing/](http://www.kernel.org/pub/linux/kernel/v2.6/testing/)
I used linux-2.6.20-rc4.tar.bz2 though rc3 is also reported to work.

**3.3**
unzip the archive
```
tar xjf linux-2.6.20-rc4.tar.bz2
```

**3.4**
move the archive to /usr/src
```
sudo mv linux-2.6.20-rc4 /usr/src/
```

**3.5**
create symbolic link
```
cd /usr/src
sudo ln -s linux-2.6.20-rc4 linux
cd /usr/src/linux

```
**3.6**
use the current kernel configuration as a starting point
```
sudo cp /boot/config-2.6.17-10-generic .config

```
**3.7**
configure the kernel. There are at least two ways to do this.
```
sudo make xconfig
```
or
```
sudo make menuconfig
```

Load the .config file as a starting point (you'll have to browse through some menus to find out how).  I found that the only change I had to make to make the new kernel work was to select Device Drivers -> Serial ATA (prod)... -> ATA device support -> NVIDIA SATA support

Save and exit

**3.8**
compile the kernel (took about an hour for me)
sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-ident kernel_image kernel_headers
where ident can be any identifier you want for your kernel
[B]
3.9[/B]
Compiling will create 2 packages which now need to be installed
```
cd /usr/src
sudo dpkg -i linux-image-2.6.20-rc4-twade2_2.6.20-rc4-ident-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.20-rc4-twade2_2.6.20-rc4-ident-10.00.Custom_i386.deb

```
The installation should update grub so that the new kernel shows up
```
more /boot/grub/menu.lst

```
**3.10**
Shutdown and restart and select your new kernel to test
Check which kernel you are using with
```
uname -r/-a
```
If it doesn't work restart (ctrl-alt-delete), and select your old kernel using Grub
The non-working kernel can be removed by using
```
sudo dpkg -r linux-image-2.6.20-rc4-ident
sudo dpkg -r linux-headers-2.6.20-rc4-ident
```

**Step 4** Install ndiswrapper

[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
The first link contains working firmware drivers.  Not all windows drivers will work with ndiswrapper.

**4.1**
Get ndiswrapper from [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
The current stable working release is 1.34

**4.2** (optional)
To remove old attemps:
```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

```
**4.3**
to install ndiswrapper:
```
sudo apt-get install build-essential linux-headers-386 linux-headers-686
tar xvzf ndiswrapper-1.34.tar.gz
cd ndiswrapper-1.34
make
sudo make install

```
**4.4**
install windows drivers
```
cd path-to-driver
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```

```
sudo modprobe ndiswrapper
dmesg
```

**4.5**
to blacklist bcm43xx and enable ndiswrapper on boot:
just edit the
/etc/modprobe.d/blacklist
file and add 
blacklist bcm43xx 
to the end of the file
enable ndiswrapper on boot:
sudo kate /etc/modules
add
ndiswrapper
to the end of the file.

**Step 5** Install Binary NVIDIA driver

[http://wizah.blogspot.com/2006/11/debian-how-to-nvidia-drivers.html](http://wizah.blogspot.com/2006/11/debian-how-to-nvidia-drivers.html)
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

**5.1**
Download the Linux IA32 driver.
I used version 1.0-9631, though there is a more recent one that is also reported to work.

**5.2**
You shouldn't need to install any new packages.  Everything should be already there from the previous proceedures

**5.3**
Shut down the graphical interface
I found that
```
sudo /etc/init.d/gdm stop
```
didn't work.
you can get to text terminals using ctrl-alt-f1 through to f6
I managed to shut down the graphical interface by logging out and selecting login at text terminal (or something like that) at the graphical login window)

**5.4**
Login to one of the text terminals
Install the drivers
```
sudo sh NVIDIA-Linux-x86-1.0.9631-pkg1.run
```
follow the on screen instructions and make sure to allow it to modify /etc/X11/xorg.conf.

**5.5**
Load the NVIDIA module
```
sudo modprobe nvidia

```
**5.6**
restart the graphical display
```
sudo /etc/init.d/gdm start
```
note.  I found this didn't work and I just restarted the computer
```
sudo shutdown -r now
```

**5.7**
add the appropriate resulution to the /etc/X11/xorg.conf (make sure you back it up first)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorf.conf.bak070108
kdesu kate /etc/X11/xorg.conf
```
you can check that the nvidia driver is being loaded.  there should be a section that looks like

```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```

add the appropriate resolution there should be a number of sections that look like:
```
SubSection     "Display"
    Depth       1
    Modes      "1024x768" "800x600" "640x480"
EndSubSection

```
In my case I changed them all to look like:
```
SubSection     "Display"
    Depth       1
    Modes      "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
```

Restart the graphical interface with ctr-alt-backspace.

The display settings can be changed with
```
nvidia-settings
```

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

### Post by SnowPunk98 on 2007-03-01
I am currently having problems with the wireless on my Dell E1705 not working, and causing even more problems with Beryl (locking up/no wireless). I am currently using the following

ndiswrapper 1.37
kernel 2.6.17-11
nvidia drivers 1.0-9746

I am going to try and kernel upgrade tonight to 2.6.20.1 since that is the newest stable one and the stable release of the release candidate you were listing. I will report back tonight on the wireless and Beryl issues, I really hope this works.

---

### Post by stoopid1 on 2007-03-26
this seemd to have doe the trick...thank you.  

P.S. If you find a solution to the headphone jack thing, please post it.

---

### Post by twade on 2007-04-02
Glad to be of help :) I haven't looked into the headphone thing much more since it doesn't bother me much to go into Kmix and I'd rather spend my very small amount of free time on other things (such as getting UFRaw to process my Pentax files with the correct exposure).

---

