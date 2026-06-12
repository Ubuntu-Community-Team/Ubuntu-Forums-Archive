---
title: "Vistas_Ubuntu dual boot locks on GRUB"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Costas100 on 2008-08-30
I am an Ubuntu user for about 2 years, but due to my age (70) consider me a beginner. I have a computer with XP_Ubuntu dual boot and it works fine, no problems. Yesterday I acquired a new computer with Vista Pre-installed and after testing every think and was fine, I used Vista to make a large partition to be used for Ubuntu 8.04
I used the live CD and checked that every thing was working fine, checked most programs and took the courage to install. Again every thing went fine. Ubuntu found the new empty partition and installed it self without any errors. At the end I was asked to restart to enjoy my installation. 
That was it, from that point on when I start I get a dos screen with the word GRUB.. and nothing more, despite waiting for as much as an hour on times.
I then rebooted from the live Ubuntu CD which worked perfect and there I could see (using Computer) the full directory structure, the Ubuntu partition, the Vista partition and in general as far as I can see all was there.
I went to 165 GB Media (Ubuntu directory) and found under boot/grub the menu.lst and copied the booting section as shown below:

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1874e296-58e9-4d4e-a395-763b37649bf4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1874e296-58e9-4d4e-a395-763b37649bf4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

As far as I can see there is nothing wrong here. I tried to find the equivalent Vista boot file but I am totally green in Vista and was unable to find it.

I tried to use the Vista recovery disk but it did not work. So my choices are limited. The computer is:
Lenovo IdeaCenter K210 Intel Desktop PC - Intel Pentium Dual Core E2140 1.6 GHz, 4GB DDR2, 500GB SATA II, DVDRW, Intel GMA3100, Webcam, Veriface, Flash Reader, Vista Home Premium SP1

I can only see two choices:
1. reformat the whole thing and start fresh - this could be a disaster
2. using a separate gparted CD empty the Ubuntu partition(s) and start all over with a new version of Ubuntu (possibly older)

Any other suggestions will be greatly appreciated.
Keep in mind that my only access is the live Ubuntu CD and thus the terminal does not work

Thank you and I really appreciate the help I received in the past. You are all great People.
Costas
PS: I am sending this message using the new computer and the live CD

---

### Post by mrtomservo on 2008-08-30
Hello!  I don't know if this will be of any help, but I came across this post a while ago and sounds similar to what your describing.

[http://ubuntuforums.org/showthread.php?t=2689]("http://ubuntuforums.org/showthread.php?t=2689")

---

### Post by gmxgeek on 2008-08-30
the blink grub prompt can mean that grub was not installed correctly.
reboot to your liveCd, open a terminal, and try
```

sudo grub
find /boot/grub/stage1
root (hdX,X)    #X,X is found from previous step
setup (hd0)
quit

```

restart and it should be working

---

### Post by Costas100 on 2008-08-30
Thank you both, very quick and up to the point. I followed gmxgeek instructions and in two minutes I am looking at my istalled UBUNTU and the Vista was shown in the boot list. I will try Vista in a few minutes.
As all the People of the great Ubuntu community you are **SPECIAL**.
I think this problem is now solved
Costas

---

