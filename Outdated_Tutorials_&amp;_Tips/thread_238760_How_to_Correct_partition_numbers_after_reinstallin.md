---
title: "How to Correct partition numbers after reinstalling Grub in Dapper"
date: 2006-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by true_friend on 2006-08-18
It is a bug in Dapper when we reinstall Grub it changes the partiton nubmers. Due to it i was thinking to format my linux system.
MetalMusicAddict helped me a lot in this regard. Acting on his tip i recovered my system. So writing this small howto to prevent other users from such bad situation.
First of all boot from live/install cd (ofcource you have lost ur MBR).
Go to System>Administration>Disks
Here see ur hard disk and then its partitions by seleting it.
in partitions see every partition by clicking on the partition u can see the file system and its nubmer e.g. /dev/hdax
where x=1,2,3...
confirm it from grub.
open terminal and ender
[COLOR="Blue"]sudo su[/COLOR]
then [COLOR="Blue"]grub[/COLOR]
here u will enter [COLOR="Blue"]find /boot/grub/stage1[/COLOR]
the out put would be like this (hd0,5) now u can confirm ur linux partition nubmer if it is (hd0,5) in grub then its nubmer should be /dev/hda6 in Disk Manager.
(Grub starts counting from 0....)
Now u confirm it. here comes the stage to edit /boot/grub/menue.list
open up terminal and enter [COLOR="Blue"]sudo mkdir /A[/COLOR]
this is the folder to mount the linux partiton's volume.
then enter [COLOR="Blue"]sudo mount /dev/hdax /A[/COLOR]
where x is the nubmer of partiton u confirmed from Disk Manager.
now we shall edit the file which is key to boot.
enter in terminal [COLOR="Blue"]gksudo gedit /A/boot/grub/menue.list[/COLOR]
it will open up gedit now find the lines:::
> title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

now change all (hd0,x) to the out put of grub command which we gave in begining i.e. [COLOR="Blue"]find /boot/grub/stage1[/COLOR]
And change all /dev/hdax with the apprpriate number we got from Disk Manager. or add +1 in grub's x number and put it here.
save the file and close the gedit.
now we are again in terminal.
enter [COLOR="Blue"]sudo su[/COLOR]
then [COLOR="Blue"]grub[/COLOR]
then [COLOR="Blue"]find /boot/grub/stage1[/COLOR]  >>>> it will result like (hd0,x) this out put is input for next command.
then [COLOR="Blue"]root (hd0,x)[/COLOR]   >>>>> (hd0,x) is out put of previous command
then enter [COLOR="Blue"]setup (hd0)[/COLOR] >>> hd0 means grub will write MBR again i tried to write boot list on some other partition but could not do so anyhows it is best on MBR i think.
last command [COLOR="Blue"]quit[/COLOR]
and close the terminal
restart system and boot from linux.
wow it is ok now (you will have to say this with joy)...
Enjoy Ubuntu.

---

