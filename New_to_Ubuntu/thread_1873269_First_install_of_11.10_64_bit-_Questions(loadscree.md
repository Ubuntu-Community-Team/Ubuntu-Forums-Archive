---
title: "First install of 11.10 64 bit- Questions(loadscreen glitch, root, md5sum)"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by zghawking on 2011-11-01
(I downloaded the 64 bit version of ubuntu if that makes any difference)
Here is what I did to get Ubuntu installed alongside my existing Windows 7:
Used Gpart to create an extended partition of 50GB
Divided this into:
sda5 100mb boot ext2
sda6 4gb swap
sda7 20gb root ext4
sda8 25gb home ext4

Ran the installer.  At the end of the installer I got the message that grub failed to be installed onto any  '/dev/sda5'
I went into Windows and ran EasyBCD.  This only let me load to a grub> prompt via the Windows boot menu

From the USB loader was able to install grub with
```
sudo mount /dev/sda5 /mnt 
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```This seemed to over-ride Windows being the default, now I just got a grub prompt still.
I ran the installer from the USB loader and had the option to 're-install' Ubuntu so I did that and everything seems to have gone smoothly.

Grub boots up to a menu and I can start Ubuntu and Windows ( :D yay! )

First question:
When Ubuntu is loading, at one point there is a garbled black box that spans about a 3rd of the screen. (Sort of like this with a different pattern: [png image]("http://1.bp.blogspot.com/-Z0hwyeE1q_s/TZBO2ybrdMI/AAAAAAAABM4/Y988170TQEk/virtual-pc-ubuntu-garbled-dmesg.png") except the rest of my background is the purple color, only under the glitch is black background).  Is this something I should be worried about?  It would be nice if it was some kind of console messages that I could read.

2nd question:
When I go into Disk Utility (huh I just noticed I no longer have access to Gparted?) It looks like my partitions were changed by the re-install.  What was sda7 (root) is now sda 20gb free space!  boot and home are not mounted.  it looks like root is mounted to a new partition sda8 (109gb) and another swap space has been added at the end (4gb) (Is it best to have swap space at the end of the drive like that or right after /boot?)  I'm wondering if I should re-install...

3rd question:
As a beginner I've started using ubuntu so I could follow this tutorial:   [http://c.learncodethehardway.org](http://c.learncodethehardway.org)   (I've programmed c/c++ in Windows for a few years but this is my first  foray into Linux based systems.)
The tutorial introduces the md5sum command with this example:
```
wget http://valgrind.org/downloads/valgrind-3.6.1.tar.bz2 
md5sum valgrind-3.6.1.tar.bz2
```and says "# use md5sum to make sure it matches the one on the site".
Well I get this result ```
$ md5sum valgrind-3.6.1.tar.bz2
2c3aa122498baecc9d69194057ca88f5  valgrind-3.6.1.tar.bz2
```Does this tell me something?  I feel like I have to do the same thing for "the one on the site".

Unfortunately I'm kind of stuck with the C tutorial because Valgrind says it's only valid for kernals 2.4 and 2.6:
```
checking for the kernel version... unsupported (3.0.0-12-generic)
configure: error: Valgrind works on kernels 2.4, 2.6
```Thanks for looking!

---

### Post by abohsin on 2011-11-01
Great work, but why not just use Wubi to install inside window, much easier.

---

### Post by zghawking on 2011-11-01
Am I going to learn Ubuntu with the same depth if I use Wubi though?

Edit:
So according to EasyBCD it may be a bug that grub won't install into it's own boot partition, ie it must left in root /boot
I re-formatted and did a fresh Ubuntu install with only swap, root, and home defined, installing grub into root (sda6).
This installed without error but still gave me a "error: unkown filesystem" grub rescue> prompt.

From a live session I was able to re-install grub as follows:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```restarted and it works now :)

Edit 2:
I'm not sure all that was really necessary but like I said I have no experience with Ubuntu or Linux

---

