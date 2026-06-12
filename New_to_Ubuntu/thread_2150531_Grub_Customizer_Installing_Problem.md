---
title: "Grub Customizer Installing Problem"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by whitelotuss on 2013-06-01
I installed the Xubuntu to my notebook. After the bios screen, i'm choosing the which system will boot (Xubuntu or Win7). But i want to install Grub Customizer and change the some settings. So, installed the Grub Customizer with terminal:

```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update
sudo apt-get install grub-customizer

```

But i cant see Grub Customizer anywhere. I searched everywhere but i cant find and open this program. I tried to reinstall the app but i get these codes:

```
beyazlotus@beyazlotus-M7X0SU:~$ sudo apt-get install grub-customizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-customizer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'danielrichter2007-grub-customizer-raring.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'danielrichter2007-grub-customizer-raring.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension


```

Can anybody help me to install this program please?

---

### Post by Mark Phelps on 2013-06-01
The error messages indicate the grub-customizer has already been installed -- it won't install it again.

Sorry, but don't use Xubuntu, so am unfamiliar with the desktop.

---

### Post by whitelotuss on 2013-06-01
Ohhhh....After a lot of searching, i found the program in the Advandec Settings Menu - System section. The problem solved. The thread can be tag as Solved and can be locked by admin. Thank you.

[IMG]http://i39.tinypic.com/hte843.jpg[/IMG]

---

