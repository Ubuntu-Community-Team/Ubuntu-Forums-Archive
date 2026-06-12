---
title: "Changed the boot order using grub now windows 8.1 wont start"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by Rana_Muhammad_Waqas_ on 2014-05-25
[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
              [TD="class: postcell"]                I wanted windows 8.1 first in boot order so I installed the Grub using This [Method]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order")  and used Grub to change the order now windows 8.1 wont start it just  blink and comes to the selection of OS screen again, Now I can only run  Ubuntu. How I can solve this problem ?  
  
the /boot/grub/grub.cfg file output [http://textuploader.com/9jhw](http://textuploader.com/9jhw) 
sudo update-grub output is 
  Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
done
  Using Ubuntu 14.04 LTS
 I tried to revert it to the previous setting but it does the same thing [IMG]http://ubuntuforums.org/images/icons/icon5.png[/IMG]



[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-05-26
I know grub customize likes to edit grub files and create its own versions.

But it is not that difficult just to manually copy the Windows boot stanza.
Boot files in grub scripts are processed in numeric order.

       sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom

 gedit /boot/grub/grub.cfg
and copy entire Windows boot stanza into grub_default  here:

gksudo gedit /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom
Then do:
sudo update-grub
    
If you just want it to be the default.

 find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

