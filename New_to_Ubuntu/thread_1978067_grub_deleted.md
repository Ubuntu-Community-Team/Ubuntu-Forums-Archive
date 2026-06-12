---
title: "grub deleted"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by vibinkrish on 2012-05-11
i had window7 and ubuntu in my laptop. now i deleted the ubuntu partition from windows. the grub also get deleted. i can't able to access my files. please help me to install grub. i doesn't need ubuntu anymore.......


please help......

thanks in advance

---

### Post by jtarin on 2012-05-11
[Several methods for re-installation of Grub2.]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")

---

### Post by wilee-nilee on 2012-05-11
You need to just load the windows bootloader to the mbr. If you have no OS with grub like Ubuntu and most Linux installs you would need some serious tweaks to use grub, and it would not be advised.

We can help you reload the mbr if XP boot a XP disc and navigate to its recovery terminal and run. This is a link on getting to the XP recovery terminal to run this command.

[http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20access%20the%20Recovery%20Console:](http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20access%20the%20Recovery%20Console:)

```
/fixmbr
```If Vista or W7, do the same get to the recovery terminal on a recovery or install disc and run this command. Here are the instructions to the Vista and W7 recovery.

                                  [FONT=Verdana, sans-serif][SIZE=1]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html [/SIZE][/FONT] 
  
```
bootrec.exe /fixmbr
```If you do not have a windows disc get a ubuntu disc and follow these instructions for a bootloader that will boot windows. This is courtesy of a another user on the forums.

                                  [FONT=Verdana, sans-serif][SIZE=1]Restore basic windows boot loader - universe enabled [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]open synaptic-settings-repositories, first tab, tick universe, close those windows and open a terminal, and run these commands [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get update [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo fdisk -l   (confirms hd=sdX, and windows partitions) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get install lilo [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT]

---

### Post by sadaruwan12 on 2012-05-11
You only need to restore your windows MBR and thats it no need to install GRUB.

wilee-nilee has listed a good way to do that just follow the steps you'll get your windows back.

---

