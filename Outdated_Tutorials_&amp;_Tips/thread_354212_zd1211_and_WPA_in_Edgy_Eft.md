---
title: "zd1211 and WPA in Edgy Eft"
date: 2007-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by DanlG on 2007-02-05
There are several different methods of getting a zd1211 based wireless device working in Edgy Eft.  Unfortunately, none are simple, because the zd1211 driver included in the Edgy Eft kernel (2.6.17-10) is buggy.

The easiest solution, and one that I previously was using is based on the Community supported driver that can be downloaded from [http://zd1211.ath.cx/](http://zd1211.ath.cx/).

If you choose to go this route, you might want to look at this post: 

[http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211](http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211)

It looks pretty much like what I've done, and I'm relatively certain that it will work, alt,hough I used r83, while he used r77 of the module.

My experience with this driver is that it would work for a while, then my system would hang.  i'd have to do a hard reboot to recover.  if you look at the zd1211 development site, it's clear that the path of new development is the zd1211rw module.  The rw suffix stands for "rewrite".  The rewrite is designed to clean up all the problems in the old module, and has been included in the kernel since 2.6.17.  Unfortunately, as I mentioned earlier, the one included in the Edgy Eft kernel does not work correctly. 

My solution was to upgrade to a new kernel.  if that sounds too scary, you can use the other driver, which is marginally stable, or wait until Feisty Fawn is released.   If you're up to it, here we go:

**Kernel upgrade**

Download the latest kernel from [www.kernel.org](www.kernel.org) (or preferably, one of it's mirrors).  The kernel I used was the 2.6.20 kernel.  Unpack the kernel in your /usr/src directory.  (tip:  most of the stuff we'll be doing requires root permission, so i open a window and execute "sudo xterm" to get a root window.

tar xvfj linux-2.6.20-tar.bz2

Although probably not necessary for ubuntu, standard practice calls for creating a link named linux to the unpacked source directory.

cd /usr/src
ln -s linux-2.6.20 linux

Next, copy the configuration file from the original kernel distribution to your new kernel source:

cp /usr/src/linux-headers-2.6.17-10-generic/.config /usr/src/linux

Since the new kernel has lots more options, you have to reconfigure the new options in the kernel.  You do this by:
cd /usr/src/linux
make clean
make mrproper
make oldconfig

Most of the answers you can just hit return and take the default. However, at about the 4th or 5th question, you have an opportunity to increase performance by tuning the kernel for your specific architecture.  Warning: if you choose the wrong option, your new kernel will not work - or you can just use the generic default.  For example, I know my processor is a Celeron - but is it
option 7, 8, or 11?  (Mine is a celeron coppermine)

Processor family
  1. 386 (M386)
  2. 486 (M486)
> 3. 586/K5/5x86/6x86/6x86MX (M586)
  4. Pentium-Classic (M586TSC)
  5. Pentium-MMX (M586MMX)
  6. Pentium-Pro (M686)
  7. Pentium-II/Celeron(pre-Coppermine) (MPENTIUMII)
  8. Pentium-III/Celeron(Coppermine)/Pentium-III Xeon (MPENTIUMIII)
  9. Pentium M (MPENTIUMM)
  10. Core 2/newer Xeon (MCORE2) (NEW)
  11. Pentium-4/Celeron(P4-based)/Pentium-4 M/older Xeon (MPENTIUM4)
  12. K6/K6-II/K6-III (MK6)
  13. Athlon/Duron/K7 (MK7)
  14. Opteron/Athlon64/Hammer/K8 (MK8)
  15. Crusoe (MCRUSOE)
  16. Efficeon (MEFFICEON)
  17. Winchip-C6 (MWINCHIPC6)
  18. Winchip-2 (MWINCHIP2)
  19. Winchip-2A/Winchip-3 (MWINCHIP3D)
  20. GeodeGX1 (MGEODEGX1)
  21. Geode GX/LX (MGEODE_LX)
  22. CyrixIII/VIA-C3 (MCYRIXIII)
  23. VIA C3-2 (Nehemiah) (MVIAC3_2)
choice[1-23]:


After you've gone thru this list, your new config file should be up to date.  You can build the new kernel -- but be warned that it may take several hours (especially on a slow box like mine!)

cd /usr/src/linux
make

When the kernel is finished building, make and install the modules.  This can take a while, but not as long as building a new kernel:

make modules_install

Now that the kernel is built, we can change our boot:

**Modifying GRUB to boot the new kernel**

Copy the kernel to the boot partition:

cd /usr/src/linux/arch/i386/boot
cp bzImage /boot/vmlinuz-2_6_20

Make an initrd.  This intermediate boot step is required unless you were familiar enough with your system to build in all the needed drivers:

mkinitrd -o /boot/initrd-2_6_20 2.6.20

Modify /boot/grub/menu.lst to add your new kernel.  Note that the first one on the list boots by default, so if your new kernel does not boot correctly, you have an opportunity in the boot sequence to hit escape and select the old kernel to boot from.  Here is my new menu.lst:

...
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20
root            (hd0,1)
kernel          /vmlinuz-2_6_20 root=/dev/hda4 ro 
initrd          /initrd-2.6.20
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
initrd          /initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
...

Now you should be able to boot into the 2.6.20 kernel - which has the good zd1211rw driver in it.


**Configuration to use WPA**
You may have to add wpa_supplicant to your system.  I've been working on this thing so long, I no longer remember if I loaded it or not :confused: 

Next you need to tell the system that WPA will be used.  Edit /etc/default/wpasupplicant and add the following content:

ENABLED=1
OPTIONS "-w -ieth1 -Dwext -c/etc/wpa_supplicant.conf"

The -w option means that wpa_supplicant should wait for the interface to come on rather than immediately quitting. The -i option tells us that the interface is on eth1, -D indicates that the wext module will be used (which, in turn calls the zd1211rw module), and that the configuration file (-c) is at wpa_supplicant.conf.

Second, edit /etc/network/interfaces and add the following entry, or something like it:

auto eth1
iface eth1 inet static
post-up /sbin/iwconfig eth1 rate 54M fixed
address 192.168.5.5
netmask 255.255.255.0
gateway 192.168.5.1
network 192.168.5.0
broadcast 192.168.5.255
dns-nameservers  68.87.69.146
wpa-conf /etc/wpa_supplicant.conf

I use static DNS, but you will probably want dynamic DNS.  You can look around and find a configuration that supports that.  Two lines in this configuration deserve special attention:
The 'post-up' line is added to force the zd1211 chip to run at 54M.  The current driver does not dynamically adjust the speed, so if you don't have this line, it will run at 11M.   The last line 'wpa-conf' points to the wpa_supplicant configuration line.

Third, is the configuration file at /etc/wpa_supplicant.conf.  Here is a copy of mine:

#
#wpa_supplicant.conf
#
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
  ssid="myHouse"
  scan_ssid=1
  psk="mySecretPassphrase"
  key_mgmt=WPA-PSK
  proto=RSN
  pairwise=CCMP
  group=CCMP
}


And finally, a step I almost forgot, you have to download the firmware for the zd1211 module from [http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083).   Unpack the files, and put them in /lib/firmware/2.6.20/zd1211.

ls /lib/firmware/2.6.20/zd1211
README      zd1211b_uph   zd1211b_uphr  zd1211_ub   zd1211_uphm  zd1211_ur
zd1211b_ub  zd1211b_uphm  zd1211b_ur    zd1211_uph  zd1211_uphr


Good Luck!! ):P

---

### Post by trippinnik on 2007-02-07
Nice job with the post.  I've got it working now on the new kernel too.  I've been trying it on and off since the 2.6.18.1 kernel came out.  This driver is definetly the way to go.  I've got NetworkManager working and WPA working with no extra config.

---

### Post by DanlG on 2007-02-07
Thanks!

As you can see, I have not posted before.  However, I've been pulling my hair out over this driver for quite some time.  Before giving up, I wanted to give it one last try with the zd1211rw driver in the new kernel. 

After getting it working, I figured I'd pay back the community for all the good support I've gotten in the past and hopefully save someone a few fistsfull of hair.

After re-reading the post, it occurred to me that it might be easier to just install the new module without the kernel.  If anyone wants to do that, you can get the most recent driver snapshot at [http://www.deine-taler.de/zd1211/snapshots](http://www.deine-taler.de/zd1211/snapshots).  If anyone does, let us know how it works!

I also wanted to optomize the kernel, so while rebuilding it, why not get the most recent? I've been using it for a few days, and have not had any problems.

---

### Post by trippinnik on 2007-02-07
I have had one unfortunate side effect of the new kernel my computer doesn't stay in sleep mode.  It goes down to sleep but then comes back out immediately.  I don't think I compiled wrong (ie chose wrong optimization cause I've done it before .. but it's possible).  

Maybe I'll try out the module on one of my other kernels (that has sleep and let you know how it goes).

---

### Post by DanlG on 2007-02-07
BUG CORRECTION:

I said to copy the config file using the command

cp /usr/src/linux-headers-2.6.17-10-generic /usr/src/linux
  
It should read:

cp /usr/src/linux-headers-2.6.17-10-generic/.config /usr/src/linux

---

### Post by trippinnik on 2007-02-08
Your link for the module is broken.  I tried moving a level up but wasn't sure what I should download to get the module driver.

---

### Post by DanlG on 2007-02-08
My bad! sorry!   try:

[http://www.deine-taler.de/zd1211/snapshots/](http://www.deine-taler.de/zd1211/snapshots/)

I found this link by digging around on the [http://zd1211.ath.cx](http://zd1211.ath.cx) site.

---

### Post by trippinnik on 2007-02-09
i couldn't get any of them to build... i mean i didn't try all of them but i went back at least 4 days.

---

### Post by DanlG on 2007-02-10
Bummer!  Thanks for trying though.  Perhaps I'll give it a shot

---

