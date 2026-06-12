---
title: "Booting Problem with Ubuntu 10.10 on Dell Latitude D500"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by Candid05 on 2012-02-19
[COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Can someone help me urgently? I have been using Ubuntu 10:10 on my Dell Latitude D500 for a while without any booting problem. It does not boot anymore but rather show the following when I put the power on:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]GNU GRUB version 1.98+20100804-5ubuntu3.3[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Where it requests me to choose the installed Ubuntu Linux between 2.6.35-32 and 2.6.35-22, Memory test (memtest86+) or Memorytest (memtest86+, serial console 115200)[/FONT][/COLOR]
 
**[COLOR=black][FONT=Verdana]When I press 'e' to edit the commands before booting, it gave me the following to edit:[/FONT][/COLOR]**
 
[COLOR=black][FONT=Verdana]recordfail[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]insmod part_msdos[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]insmod ext2[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]set root = '(hd0, msdos1)'[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Search --no-floppy --fs-uuid --set ..........................[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]linux /boot/vmlinuz-2.6.35-32-generic root=UUID= .......................... ro quiet splash[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]initrd /boot/initrd.img-2.6.35-32-generic[/FONT][/COLOR]
 
(please note that where my computer's code appear above and below, I replaced it with '...............................' as I don't know if it is safe sharing everything online)
 
**[COLOR=black][FONT=Verdana]When i pressed 'e' for memory test edit, i got:[/FONT][/COLOR]**
 
[COLOR=black][FONT=Verdana]insmod part_msdos[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]insmod ext2[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]set root = '(hd0, msdos1)'[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Search --no-floppy --fs-uuid --set .....................................[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]linux16 /boot/memtest86+.bin console=ttyS0,115200n8[/FONT][/COLOR]
 
**[COLOR=black][FONT=Verdana]When I tried to boot it, i got the following message:[/FONT][/COLOR]**
 
[COLOR=black][FONT=Verdana][ 1.996840] EIP : [<c 03643aa>] _perpcpu_counter _sum+0x2a/0x70 SS: ESP 0068 : dda95d60[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 1.996942] CR2: 0000000000f3f000[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 1.997008] ---[ end trace e50e6df5c98af344 ]--- Killed[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]mount: mounting /dev on /root/dev failed: No such file or directory[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]mount: mounting /sys on /root/sys failed: No such file or directory[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]mount: mounting /proc on /root/proc failed: No such file or directory[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Target filesystem doesn't have requested /sbin/init.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]No init found. Try passing init= bootarg[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Enter 'help' for a list of built-in commands.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana](initramfs)_ [/FONT][/COLOR]
 
 
**[COLOR=black][FONT=Verdana]When i press Ctrl-c for the built-in commands, I got:[/FONT][/COLOR]**
 
[COLOR=black][FONT=Verdana]. : [ alias break cd chdir command continue echo eval exec exit export false getopts hash help let local printf pwd read readonly return set shift source testtimes trap true type ulimit umask unalias unset wait [ [[ ash awk basename cat chmod chroot chvt clear cmp cp cut deallocvt df dnsdomainnames du dumpkmap echo egrep env expr false fbset fdflush fgrep find grep gunzip gzip hostname ifconfig ip kill ln loadfront loadkmap ls mkdir mkf ifo mknod mkswap mktemp more mount mv openvt pidof printf ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort stat static-sh stty sync tail tee test touch tr true tty umount uname uniq wc wget yes zcat[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]NB: please I am providing all these information hoping that someone out there can help me fix the problem. I am a complete novice on things like these.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thank you[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Candid05 [/FONT][/COLOR]

---

### Post by ajgreeny on 2012-02-19
Boot to a live CD or USB and then follow the instructions when you click on the Boot-info-script link in my signature to use the Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

