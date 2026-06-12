---
title: "NEW to uBuntu AND LOViNG iT! i have 1 small error"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by JohnDillinger on 2013-01-30
i couldnt install on my desktop because with my motherboard i need to plug in old keyboard to select. anyone know the trick to that?

my problem is i didnt want to plug in a dif keyboard everytime i wanted to boot a dif OS. so i put ubuntu on my wifes laptop lol. i need to change it to boot win7 by default cause she caught me and i have to delete it or make windows load default @@! ubuntu .12.10. gnu grub 2.0
[IMG]http://i480.photobucket.com/albums/rr164/JOHNDILLINGER_7/IMG_2012_zps9853a635.jpg[/IMG]
[IMG]http://i480.photobucket.com/albums/rr164/JOHNDILLINGER_7/Screenshotfrom2013-01-30142213_zpsb0fbfdec.png[/IMG]
[IMG]http://i480.photobucket.com/albums/rr164/JOHNDILLINGER_7/Screenshotfrom2013-01-30142427_zps20fdaf49.png[/IMG]

---

### Post by ACubed10 on 2013-01-30
from the Wubi Wiki

"Ubuntu is not installed as the default boot option, you have to select  it in the Windows boot menu. To change that, in Windows XP go to Control  Panel > System > Advanced Startup and Recovery and edit the  "Default Operating System". In Windows 7, go to Control Panel >  System and Security > System > Advanced system settings (on the  left). Then click Settings under Startup and Recovery. If  you want, you can change the timeout as well. Be aware that changing  the timeout to zero (0) may cause issues booting into Windows. It is  preferable that the value be set at 10 or higher."  

See if this will allow you to choose win 7 again

Cheers!:)

---

### Post by JohnDillinger on 2013-01-30
ubuntu boots automaticly, i changed the default to 4 but it still boots ubuntu by default. because this is not my pc i need windows7 by default

---

### Post by ACubed10 on 2013-01-30
> **JohnDillinger said:**
> ubuntu boots automaticly, i changed the default to 4 but it still boots ubuntu by default. because this is not my pc i need windows7 by default


did you install by using a disk you burnt? or are you using Wubi?

---

### Post by JohnDillinger on 2013-01-30
i tried windows 7 loader but it still booted gnu grub first, so i had to select it in grub loader first then in win7 loader

---

### Post by JohnDillinger on 2013-01-30
> **ACubed10 said:**
> did you install by using a disk you burnt? or are you using Wubi?
disk i burnt

---

### Post by ACubed10 on 2013-01-30
> **JohnDillinger said:**
> disk i burnt
so you manually set up this dual boot from the installation process after booting from the cd?


check the second users' post here [http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa](http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa)
where Marty states "The default entry is determined by the GRUB_DEFAULT= setting in  /etc/default/grub; the first "menuentry" has a value of "0".  It can be  changed to the number of the Windows entry in the menu, probably "3".   Or, it can be changed to the **full, exact name** of the Windows entry, which is useful if you change things very much. To edit this file, you would enter at a command prompt: gksu gedit /etc/default/grub.  Be careful not to change anything you don't understand, as this is an important file."

which looks like Win 7 would be your 5th option according to the picture you posted

---

### Post by JohnDillinger on 2013-01-30
> **ACubed10 said:**
> so you manually set up this dual boot from the installation process after booting from the cd?


check the second users' post here [http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa](http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa)
where Marty states "The default entry is determined by the GRUB_DEFAULT= setting in  /etc/default/grub; the first "menuentry" has a value of "0".  It can be  changed to the number of the Windows entry in the menu, probably "3".   Or, it can be changed to the **full, exact name** of the Windows entry, which is useful if you change things very much. To edit this file, you would enter at a command prompt: gksu gedit /etc/default/grub.  Be careful not to change anything you don't understand, as this is an important file."

which looks like Win 7 would be your 5th option according to the picture you posted
yes it is 5, but from zero it would be 4 correct? thanx alot guys for the help and links and plz correct me if im wrong

---

### Post by JohnDillinger on 2013-01-30
> **ACubed10 said:**
> so you manually set up this dual boot from the installation process after booting from the cd?


check the second users' post here [http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa](http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa)
where Marty states "The default entry is determined by the GRUB_DEFAULT= setting in  /etc/default/grub; the first "menuentry" has a value of "0".  It can be  changed to the number of the Windows entry in the menu, probably "3".   Or, it can be changed to the **full, exact name** of the Windows entry, which is useful if you change things very much. To edit this file, you would enter at a command prompt: gksu gedit /etc/default/grub.  Be careful not to change anything you don't understand, as this is an important file."

which looks like Win 7 would be your 5th option according to the picture you posted
srry i did dual boot from disk upon install

---

### Post by ACubed10 on 2013-01-30
yes from 0 it would be 4.  Unless the memtests don't count?  Never dual booted manually..always used Wubi.  Now I don't use windows at all ):P

---

### Post by deadflowr on 2013-01-30
Two things seem strange about the output from your update-grub terminal photo.

1) Your system seems to have a menu.lst versus a grub.cfg file.
Menu.lst was the file for grub-legacy, grub2 uses grub.cfg.

2) The list generated does not show Windows being found, only linux kernels and memtest.

Please if you could post the output of the menu.lst file.

---

### Post by JohnDillinger on 2013-01-30
> **deadflowr said:**
> Two things seem strange about the output from your update-grub terminal photo.

1) Your system seems to have a menu.lst versus a grub.cfg file.
Menu.lst was the file for grub-legacy, grub2 uses grub.cfg.

2) The list generated does not show Windows being found, only linux kernels and memtest.

Please if you could post the output of the menu.lst file.
yes i was very curious on why i havent seen windows in list

---

### Post by JohnDillinger on 2013-01-30
> **deadflowr said:**
> Two things seem strange about the output from your update-grub terminal photo.

1) Your system seems to have a menu.lst versus a grub.cfg file.
Menu.lst was the file for grub-legacy, grub2 uses grub.cfg.

2) The list generated does not show Windows being found, only linux kernels and memtest.

Please if you could post the output of the menu.lst file.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue


#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2984cc8c-6a30-4ba0-8928-b7fcfa58ee71 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2984cc8c-6a30-4ba0-8928-b7fcfa58ee71

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 12.10, kernel 3.5.0-22-generic
uuid        2984cc8c-6a30-4ba0-8928-b7fcfa58ee71
kernel        /boot/vmlinuz-3.5.0-22-generic root=UUID=2984cc8c-6a30-4ba0-8928-b7fcfa58ee71 ro quiet splash 
initrd        /boot/initrd.img-3.5.0-22-generic

title        Ubuntu 12.10, kernel 3.5.0-22-generic (recovery mode)
uuid        2984cc8c-6a30-4ba0-8928-b7fcfa58ee71
kernel        /boot/vmlinuz-3.5.0-22-generic root=UUID=2984cc8c-6a30-4ba0-8928-b7fcfa58ee71 ro  single
initrd        /boot/initrd.img-3.5.0-22-generic

title        Ubuntu 12.10, kernel 3.5.0-17-generic
uuid        2984cc8c-6a30-4ba0-8928-b7fcfa58ee71
kernel        /boot/vmlinuz-3.5.0-17-generic root=UUID=2984cc8c-6a30-4ba0-8928-b7fcfa58ee71 ro quiet splash 
initrd        /boot/initrd.img-3.5.0-17-generic

title        Ubuntu 12.10, kernel 3.5.0-17-generic (recovery mode)
uuid        2984cc8c-6a30-4ba0-8928-b7fcfa58ee71
kernel        /boot/vmlinuz-3.5.0-17-generic root=UUID=2984cc8c-6a30-4ba0-8928-b7fcfa58ee71 ro  single
initrd        /boot/initrd.img-3.5.0-17-generic

title        Ubuntu 12.10, memtest86+
uuid        2984cc8c-6a30-4ba0-8928-b7fcfa58ee71
kernel        /boot/memtest86+.bin
```

---

### Post by nothingspecial on 2013-01-30
Please use code tags when pasting terminal output to the forums. To do this, highlight the text then Click the # in the formatting options at the top of the posting box.

Thanks.

---

### Post by deadflowr on 2013-01-30
Hmm, could you please run the command

```
grub-install -v
```

and post the ouput.

This will verify what version you have running.

From the looks of the menu.lst( and the fact that you have a menu.lst at all) seems to suggest you're running grub-legacy.

Grub2 uses a program called os-prober which reads the disk connected to your pc and finds OSs and adds them to the boot list (/etc/grub/grub.cfg).

It's been a while so I can't remember if grub-legacy used an os-prober or if I manually entered the menu entries myself.

I sort of remember doing that at some point, though I can't remember if it was needed or my own fiddling desire.

---

### Post by JohnDillinger on 2013-01-30
> **deadflowr said:**
> Hmm, could you please run the command

```
grub-install -v
```and post the ouput.

This will verify what version you have running.

From the looks of the menu.lst( and the fact that you have a menu.lst at all) seems to suggest you're running grub-legacy.

Grub2 uses a program called os-prober which reads the disk connected to your pc and finds OSs and adds them to the boot list (/etc/grub/grub.cfg).

It's been a while so I can't remember if grub-legacy used an os-prober or if I manually entered the menu entries myself.

I sort of remember doing that at some point, though I can't remember if it was needed or my own fiddling desire.
```
grub-install -v
grub-install (GNU GRUB 0.97)
``` when i boot it shows GNU GRUB 2.0 menu

---

### Post by deadflowr on 2013-01-30
Yes, you're using grub-legacy.

Follow this:

[https://help.ubuntu.com/community/Grub2/Upgrading]("https://help.ubuntu.com/community/Grub2/Upgrading")

When all is set, run update-grub and Windows should show up.

From there you can set the default boot in the /etc/default/grub file.

---

### Post by JohnDillinger on 2013-01-30
> **deadflowr said:**
> Yes, you're using grub-legacy.

Follow this:

[https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading)

When all is set, run update-grub and Windows should show up.

From there you can set the default boot in the /etc/default/grub file.
ok sweet so wer getting somewhere this is the menu title
[IMG]http://i480.photobucket.com/albums/rr164/JOHNDILLINGER_7/IMG_2013_zpsab9ef6b4.jpg[/IMG]

---

### Post by JohnDillinger on 2013-01-30
> **deadflowr said:**
> Yes, you're using grub-legacy.

Follow this:

[https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading)

When all is set, run update-grub and Windows should show up.
[IMG]http://i480.photobucket.com/albums/rr164/JOHNDILLINGER_7/Screenshotfrom2013-01-30181738_zps555b58a3.png[/IMG]

From there you can set the default boot in the /etc/default/grub file.
Oh THANK U SOOO MUCH! now i can stop wasting my time with that and learn more about this ubuntu! which so far is GREAT! new to linux, but ive been customizing fw for years and man do i wish i messed with this when i began! agaiN THANX ALOT!

---

### Post by deadflowr on 2013-01-30
Ok, to be sure, restart and see if you can boot into windows.
If all goes good, come back and mark this thread as solved(look in the thread tools at top of page).
Otherwise, if bad things still happen, we can try and resolve them.

---

### Post by JohnDillinger on 2013-01-30
> **deadflowr said:**
> Ok, to be sure, restart and see if you can boot into windows.
If all goes good, come back and mark this thread as solved(look in the thread tools at top of page).
Otherwise, if bad things still happen, we can try and resolve them.
ok thanx, yes its solved. i tested it b4 last post THANK YOU!

---

### Post by deadflowr on 2013-01-30
> **JohnDillinger said:**
> ok thanx, yes its solved. i tested it b4 last post THANK YOU!

Good.

You also posted on wanting to learn more. so here's a great place for learning:

[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")


Also  the place where the link I posted for the grub is the community wiki for Ubuntu, peruse it for good reading.

---

### Post by JohnDillinger on 2013-01-30
> **deadflowr said:**
> Good.

You also posted on wanting to learn more. so here's a great place for learning:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)


Also  the place where the link I posted for the grub is the community wiki for Ubuntu, peruse it for good reading.
ok you must be a mind reader, i was returning to find some pointers. some cool links for first time ubuntu. a list of some useful apps or maybe even abetter ver. of ubuntu (older/newer) im 12.10. i tweak game consoles phones even game and im not sure if i could use the same tools as windows. for example my img burn 2.5.5 came up in seperate files when i installed to  ubuntu? @@ and ive just been trying to get her windows to boot by default or i was going to have to delete it until i found my own laptop;)

---

### Post by stinkeye on 2013-01-31
> i couldnt install on my desktop because with my motherboard i need to plug in old keyboard to select. anyone know the trick to that?
Just a reply to your first post.
In some BIOS  there is a setting to enable USB keyboard.
If set to off, a USB keyboard wont work until your booted into your OS.

---

