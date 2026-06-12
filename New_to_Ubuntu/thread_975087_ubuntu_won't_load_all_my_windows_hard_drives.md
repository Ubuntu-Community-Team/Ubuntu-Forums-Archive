---
title: "ubuntu won't load all my windows hard drives"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-08
Hi. for some reason ubuntu won't load all my windows hard drives including an internal one.
M

---

### Post by louieb on 2008-11-08
Did you look in the places menu?

---

### Post by ronnielsen1 on 2008-11-08
> Hi. for some reason ubuntu won't load all my windows hard drives including an internal one.
Does BIOS recognize them? Post the output of [COLOR=Red]fdisk -l[/COLOR] from a terminal

---

### Post by irish66 on 2008-11-08
Hi.
Well the only one it doesn't recognise now is the one In installed ubuntu on. That is. I chose the share with windows option. So i guess that's why I can't see the windows files.
now I would have liked to partion a drive. but i don;t  have any ones that haven't got a lot of stuff on. Basically i don't feel like moving tons og gigs of stuff to format another drive.
Hmm, actually i do have a drive with a total capacity of 5.4 gigs. Would that be enough for ubuntu. Then of course I'd be installing other stuff too, and I suppose getting rid of stuff I didn't need.
M

---

### Post by bumanie on 2008-11-08
Post the output of 
> sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
the / filesystem of ubuntu will take about 3-3.5gb, before you install anything else. A 5gb drive is cutting things fine.

---

### Post by irish66 on 2008-11-08
i think this is it all.
M
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6CD462E3D462AED0 loop=/ubuntu/disks/root.disk ro access=v1 ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6CD462E3D462AED0 loop=/ubuntu/disks/root.disk ro access=v1 ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

irish@ubuntu:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
irish@ubuntu:~$ ### END DEBIAN AUTOMAGIC KERNELS LISTirish@ubuntu:~$ 
irish@ubuntu:~$ # This is a divider, added to separate the menu items below from the Debian
irish@ubuntu:~$ # ones.
irish@ubuntu:~$ titleOther operating systems:
bash: titleOther: command not found
irish@ubuntu:~$ root
The program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
bash: root: command not found
irish@ubuntu:~$ 
irish@ubuntu:~$ 
irish@ubuntu:~$ # This entry automatically added by the Debian installer for a non-linux OS
irish@ubuntu:~$ # on /dev/sda1
irish@ubuntu:~$ titleMicrosoft Windows XP Home Edition
bash: titleMicrosoft: command not found
irish@ubuntu:~$ rootflags (hd0,0)
bash: syntax error near unexpected token `hd0,0'
irish@ubuntu:~$ savedefault
bash: savedefault: command not found
irish@ubuntu:~$ chainloader+1
bash: chainloader+1: command not found
irish@ubuntu:~$ 
irish@ubuntu:~$ rish@ubuntu:~$ i
bash: rish@ubuntu:~$: command not found
irish@ubuntu:~$ irish@ubuntu:~$ 
bash: irish@ubuntu:~$: command not found
irish@ubuntu:~$ irish@ubuntu:~$ # This entry automatically added by the Debian installer for a non-linux OS
bash: irish@ubuntu:~$: command not found
irish@ubuntu:~$ irish@ubuntu:~$ # on /dev/sda1
bash: irish@ubuntu:~$: command not found
irish@ubuntu:~$ irish@ubuntu:~$ titleMicrosoft Windows XP Home Edition
bash: irish@ubuntu:~$: command not found
irish@ubuntu:~$ bash: titleMicrosoft: command not found
bash: bash:: command not found
irish@ubuntu:~$ irish@ubuntu:~$ rootflags (hd0,0)
bash: syntax error near unexpected token `('
irish@ubuntu:~$ bash: syntax error near unexpected token `hd0,0'
> irish@ubuntu:~$ savedefault
> bash: savedefault: command not found
> irish@ubuntu:~$ chainloader+1
> bash: chainloader+1: command not found
> irish@ubuntu:~$ 
> irish@ubuntu:~$ i
> 
>

---

### Post by irish66 on 2008-11-15
okay, it's all about knowing where to look. The windows drive that ubuntu is sharing is in the host folder.Some programs such as krusader
will show all drives in a list, wheras other such as movie player
require you to go into "file system" and then "host"
M

---

