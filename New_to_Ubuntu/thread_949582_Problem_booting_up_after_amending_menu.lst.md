---
title: "Problem booting up after amending menu.lst"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by ibnbatuta on 2008-10-16
I am a novice user and in attempting to shorten the start-up list, I deleted the last two entries in the start up list. Since then the system simply starts up and shows a Dos type screen with GRUB> and a blinking cursor. I had installed edubuntu on a DELL 8300 running Windows XP and chose the dual boot option with both Windows and Edubuntu on a single hard disk but in different partitions.

Could somebody please help me get out of this situation and help me get my computer running again. I am unable to run a Live-CD either since the setup screen displays the message that the CD-drive cannot be found.

Thanks.

---

### Post by Keen101 on 2008-10-16
I can understand why you edited it, but i have no idea why it does not load, unless you deleted something else by accident. Is Edubuntu the only operating system in the computer, or is it dual boot?

are you able to get into the recovery mode? 

your BIOS will not let you boot a live-cd?

In the future when editing grub it is advisable to comment lines out instead of deleting them. the **#** symbol effectively comments out all lines.

---

### Post by iponeverything on 2008-10-16
at the grub prompt just type:

boot

and see what happens.

---

### Post by caljohnsmith on 2008-10-16
How about posting your menu.lst so we can check it? Boot your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Post all the above, and hopefully we can help you get Grub working again.

---

### Post by ibnbatuta on 2008-10-16
To answer - It is dual boot, Edubuntu installed on a single hdd on which Windows XP was already installed.

I am unable to get the system run a live CD. On startup it goes through its processes and then gives the following display.

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]

grub>


When I type in boot at the prompt I get


Starting up ....

Error 8: Kernel must be loaded before booting

grub>


Thanks.

Anup

---

### Post by philinux on 2008-10-16
I would use this to sort it out.

On the right is are choices to download. It works a treat.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by ibnbatuta on 2008-10-16
Thank you for the tip.

I have got the SGD for USB downloaded and have run it on my computer. It now does not show the 

grub> 

screen.

Instead it now gives an error message saying

Error loading operating system.

I shall now try to run the same from the Windows reinstallation disk and will get back in case of more problems.

Thanks once again for all your tips.

Regards.

---

### Post by Keen101 on 2008-10-17
Error loading operating system usually means a BIOS error, or hard drive failure.


assuming you can get to a terminal or bash shell this command might help fix your problem:

> sudo update-grub

---

### Post by iponeverything on 2008-10-17
It quite easy to overcome:

ref: [http://www.linuxquestions.org/questions/linux-software-2/discussion-new-grub-trouble-shooter-278748/](http://www.linuxquestions.org/questions/linux-software-2/discussion-new-grub-trouble-shooter-278748/)
ref: [http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

Let us know how it turns out!

---

