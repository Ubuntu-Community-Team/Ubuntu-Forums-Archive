---
title: "Installing Guest Additions causing problems"
date: 2014-09-22
forum: New to Ubuntu
---

### Post by souraklis on 2014-09-22
I am trying to install Guest Additions in virtualbox with windows xp host and Ubuntu 12.04 guest. I followed the above steps:

Devices-> Insert Guest Additions CD Image.
After that I locate the folder /media/VBoxAdditions4.3.4_91027/
and run sudo ./VBoxLinuxAdditions.run

I want to be able to create share folders and adjust the resolution of the screen. I achieved to do the first issue, but I couldt do the second one. I didn't get any message, however it is not possible to change the resolution of the screen and I cannot switch to fullscreen. What am I doing wrong? I found in installation log the following: unknown version of the X Window System

---

### Post by ibjsb4 on 2014-09-22
Got dkms?

I run both linux host and guest, so my setup is a bit different.  But I wonder if you need to install virtualbox-guest-dkms or maybe with a windows host, just dkms in the guest.

---

### Post by anika200 on 2014-09-22
> **souraklis said:**
>  but I couldt do the second one. I didn't get any message, 

So you located the folder? You then open a terminal and run the command ```
sudo ./VBoxLinuxAdditions.run
```? Which one of these steps did not get completed?

---

### Post by souraklis on 2014-09-22
When I run the command it was printed in the end the following warning:

Installing the window system drivers 
warning unknown version of X windows  systme installed. Not installing
X window system drivers .
...done
installing graphic libraries and desktop services
....done

---

### Post by slickymaster on 2014-09-22
Your  virtualbox-additions package and CD are apparently missing some pieces. Please try the following in a terminal:```
sudo apt-get install virtualbox-guest-dkms
```
After that restart.

---

### Post by souraklis on 2014-09-23
When I tried the command I got: Error! Bad return status for module build on kernel 3.13.0-32-generic(i686). I restart the VM and I had the same problem. I tried to run again the command and I got 0 updated. 0 newly installed, 0 to remove and  58 not upgraded

---

### Post by slickymaster on 2014-09-23
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with **/dev/vboxdrv**. Please reinstall the kernel module by executing```
sudo /etc/init.d/vboxdrv setup
```Please note that before rebuilding the module you should install the DKMS package first```
sudo apt-get install dkms
```This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

---

### Post by souraklis on 2014-09-23
The file vboxdrv does not exist in inti.d folder!

---

### Post by slickymaster on 2014-09-23
It seems you're facing this bug: [#1292118]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1292118")

You could try the workaround proposed in [post #10]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1292118/comments/10").

---

### Post by souraklis on 2014-09-23
The solution to install newer version of VB in host OS??

---

### Post by slickymaster on 2014-09-23
> **souraklis said:**
> The solution to install newer version of VB in host OS??

Yes. You could be facing some sort of incompatibility between your guest X server version and your current Guest Additions.

---

### Post by sp40140 on 2014-09-23
Not to change topic. But I have found VMware to be much more stable, faster and reliable option. The new version of VMWare player if free for personal use and can create vms as well (unlike previous versions).
I suggest you try VMWare.

---

### Post by souraklis on 2014-09-24
I ve got 4.3.4 version of virtualbox. The issue here that I ve already tested it that version with the same host and same guest and guest additions were nicely installed. What possible could happen at this time?

---

### Post by slickymaster on 2014-09-24
Let's try it this way, boot your guest OS into a root shell by holding and pressing the left Shift key during boot. Once in the Grub menu, select "Advanced options for Ubuntu" -> select the kernel you wish to boot in "Recovery mode" (it should be the second available option). That will lead you to the advanced options. Selecting "Enable networking" to gain access to the internet. After the network has loaded, and the fielsystem mounted, you will be presented again with the menu, from where you choose "Drop to a root shell prompt".

In the root shell run the following commands, one at a time:```
apt-get install virtualbox-guest-dkms
mount /dev/cdrom /mnt
cd /mnt
./VBoxLinuxAdditions.run
reboot
```

---

