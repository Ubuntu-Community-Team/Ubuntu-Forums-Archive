---
title: "ubuntu stops working in my PC"
date: 2016-03-30
forum: New to Ubuntu
---

### Post by shivank1969 on 2016-03-30
[COLOR=#000000]I was using windows 8.1 and then afterwards, I install [/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]Ubuntu 14.04[/FONT][/COLOR][/COLOR][COLOR=#000000] next to windows 8.1. Both of them windows and ubuntu works perfectly for approx 4 months. Then after that one day, I was working on windows and then suddenly a blue screen pops with a message "Your PC ran into a problem and need to restart" and then restart fails and also it was asking for recovery media. But I press the power button to shutdown the laptop and then when I restart it there was no selection screen. It automatically opens the windows. There is no way to go to ubuntu. How to resolve the problem? [/COLOR]
[COLOR=#000000]Thanks in advance.[/COLOR]

---

### Post by lynx6 on 2016-03-30
Hello,
The first step is you have at your disposal a live  DVD or pen drive Ubuntu.
Give boot normally, as if you were to format the computer with Ubuntu, however, start the system in live mode, just as you do when you want to test the system before installing.
The first command is for you to identify which partition you have Ubuntu installed.
> **sudo fdisk -l **

Note the partition table it states that the [COLOR=#ff0000]*/dev/sdaX*[/COLOR] partition contains Linux, that is, that partition the system is installed, this step is important because it can vary (probably will) from computer to computer.

The second step is to mount the partition that you identified in the previous step, in this way, run this command modifying the partition as your computer.
> **sudo mount -t [COLOR=blue]ext4[/COLOR] [COLOR=red]/dev/sdaX[/COLOR] /mnt**


Where the red text is part you should place according to the partition where Ubuntu is installed on your computer, in my case it was [COLOR=#ff0000]*/dev/sda1*[/COLOR] but could be [COLOR=#ff0000]*/dev/sda2*[/COLOR] (sda3, sda4 ..., etc. )
In blue we have the file system, which is usually the Ext4, if you installed Ubuntu with another file system modify this session, otherwise it will not work. If you "only" installed Ubuntu, the system will be ext4.

Now comes the comado to reinstall GRUB itself:
> **sudo grub-install --root-directory=/mnt /dev/sda**

With that your GRUB will be back, restart the computer and do the tests.

---

### Post by mastablasta on 2016-03-31
the first action should actually be to start a live OS and run bootinfo summary ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) then provide the results here using code tags or attach the file.

---

### Post by Bucky Ball on 2016-03-31
> **mastablasta said:**
> the first action should actually be to start a live OS and run bootinfo summary ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) then provide the results here using code tags or attach the file.

+1. Please do this. Just post back the link Boot Repair gives you after it has run the bootinfo script. No need to post the whole thing here or attach the file. ;)

---

### Post by shivank1969 on 2016-04-20
My main problem has been resolved by the Boot Repair. But due to this, now on selection screen there are 4 to 5 pannel showing to operate windows and only 1 pannel for ubuntu. Previously there was only 2 pannel for windows.
Will this cause any problem ?

---

