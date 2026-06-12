---
title: "Newbie Question install"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by santelmo on 2016-11-23
Hi I have an asus e200h and have been trying to install ubuntu as dual boot alongside windows 10 to try it out. The problem I seem to have is that the e200h only has a 32Gb hard drive and there  is only 4.5Gb of space available which I think is not enough. From what I can gather my only option is to install ubuntu onto an external hd. My questions are 
Am I right that that this is my best option for this machine?
What size and type of hd should I use ie would 16Gb memory stick do

---

### Post by mastablasta on 2016-11-23
16  Gb memorry stick will do. i would install GRUB to the stick (which should keep Windows bootable when stick is out of USB port). 
reduce swapiness after install. swapping can wear down the stick fast. know that you might need to replace the stick after relatively short time and depending on usage of the OS. they just don't have the hard disk stamina. but for testing and such it Will be ok.

---

### Post by pugstah on 2016-11-23
> **mastablasta said:**
> Reduce swappiness after install. swapping can wear down the stick fast. know that you might need to replace the stick after relatively short time and depending on usage of the OS. they just don't have the hard disk stamina. but for testing and such it Will be ok.

Regarding Mastablasta's advice, after installing, if you do not know how to reduce the swapiness, heres what you need to do:

[LIST=1]
[*]Make sure that you have the necessary applications, which are gksu and leafpad.
```
sudo apt-get install gksu leafpad
``` 
You will then be prompted to enter your root password. 
[*]Check your swappiness.
```
cat /proc/sys/vm/swappiness
```
Usually, it would be 60, which is the default swappiness setting for most computers. 
[*]Then, in order to be able to change the setting, use the leafpad editor that you installed earlier.
```
gksudo leafpad /etc/sysctl.conf
``` 
[*]Put this in the text file, I'd suggest in the bottom.
```
# Decrease swap usage to a more reasonable level
vm.swappiness=10
``` 
[*]Reboot your system and after rebooting, check your swappiness again. It should be 10.
```
cat /proc/sys/vm/swappiness
``` 
[/LIST]

For more information regarding the swap use of Linux, check [this]("https://sites.google.com/site/easylinuxtipsproject/first-lubuntu") out, scroll down and find the "**Decrease the swap use (important!)**".

---

### Post by oldos2er on 2016-11-23
There's no need to install anything to change swappiness; the text editor *nano* is included in all flavors of *buntu.

Also no need to reboot, just run ```
sudo sysctl --system /etc/sysctl.conf
``` to load the new settings in /etc/sysctl.conf

---

