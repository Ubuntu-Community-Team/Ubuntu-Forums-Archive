---
title: "how to separate linux boot and windows boot"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by polppol on 2008-04-30
how to separate linux boot and windows boot

i mean now my computer is boot via GRUB bootloader
then it will let me select what i want to boot

now i have 2 partion
one is Ubuntu partion
two is windows partion

it seem GRUB is installed in to my windows NTFS partion

can i move `GRUB boot loader to Ubunto partion and restore my windows Vista
boot ?

than i want to put down other boot loader and set it boot directly to GRUB or windows or another partion

sorry for my bad english

---

### Post by muteXe on 2008-04-30
You might want to look at the super grub disk:

[http://www.supergrubdisk.org/wiki](http://www.supergrubdisk.org/wiki)

Sounds like it could be the thing to help you.

mute

---

### Post by adrian15 on 2008-04-30
> **polppol said:**
> 
can i move `GRUB boot loader to Ubunto partion and restore my windows Vista
boot ?

than i want to put down other boot loader and set it boot directly to GRUB or windows or another partion


What you need to do is:
[LIST=1][*][Fix Boot of Windows](http://www.supergrubdisk.org/wiki/UninstallGRUB)
[*][Prepare Linux for being chainloaded from Windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows)
[*]and finally add the Linux boot entry to Windows Vista boot menu thanks to [EasyBCD](http://neosmart.net/wiki/display/EBCD/Linux) (Check the: Back in Windows Vista section).
[/LIST]

You need, of couse, a [Super Grub Disk](http://www.supergrubdisk.org) and the EasyBCD software.

Finally you could write for me the steps you have done for adding Linux boot to Vista menu thanks to EasyBCD so that I add them to the [How to Boot Grub from Windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows) page.

adrian15

---

### Post by polppol on 2008-04-30
thank every one

i'll try it soon

and post the result

---

### Post by polppol on 2008-04-30
ok, i got it

i did to the following steps


(1)-remove GRUB first---
1. Put Super GRUB Disk( SGD ) in your cd-rom drive and boot it
2.Choose Language & HELP or wo/ Help
3.Choose English Super Grub Disk 
4.Choose Windows 
5.Choose Windows (Advanced) 
6.Choose Fix Boot of Windows 
7.Choose Your HDD and Your Windows Partion
8.Restart

(2)-do Windows chainloads Grub---
1. Put Super GRUB Disk( SGD ) in your cd-rom drive and boot it
2.Choose Language & HELP or wo/ Help
3.Choose English Super Grub Disk 
4.Choose Windows 
5.Choose Windows (Advanced) 
6.Windows chainloads Grub! 
7.Choose Your HDD and Your UBUNTU Partion
8.Restart

(3)-Edit vista boot menu with EasyBCD 1.7.2---
1.Download and run EasyBCD 1.7.2(or any version i think)
2.If program ask for boot drive just select your windows partion
3.Choose Add/remove Entries
4.at "Add an Entry" select "Linux"
5.Change Type to "Linux"
6.Enter Name box with any name u want
7.At Drive Select Your Ubuntu Partion
8.Click "Add Entry"
9.Click "Save"
10. Restart, you have done ^ ^

Pol-P-Pol
1/5/08

---

### Post by adrian15 on 2008-04-30
> **polppol said:**
> 

(3)-Edit vista boot menu with EasyBCD 1.7.2---
1.Download and run EasyBCD 1.7.2(or any version i think)
2.If program ask for boot drive just select your windows partion
3.Choose Add/remove Entries
4.at "Add an Entry" select "Linux"
5.Change Type to "Linux"
6.Enter Name box with any name u want
7.At Drive Select Your Ubuntu Partion
8.Click "Add Entry"
9.Click "Save"
10. Restart, you have done ^ ^

Pol-P-Pol
1/5/08
It seems that you have followed method 2 of the easy bcd link I gave you. You do not need this step: **(2)-do Windows chainloads Grub---** then.


adrian15

---

