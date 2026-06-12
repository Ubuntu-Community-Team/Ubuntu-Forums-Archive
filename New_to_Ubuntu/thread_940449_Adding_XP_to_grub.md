---
title: "Adding XP to grub"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by cozmokramer8 on 2008-10-07
I posted a little while ago about grub not showing windows xp. I still have my windows xp i realize now i just have to add it to the grub menu. I looked online how to do this but now i get a error message. Just to be clear this is what i did.

Windows XP Home
root (hd0,2) #right here i am not sure if my windows is installed on partition 2, how do i tell?
makeactive
chainloader +1


I am not sure i am choosing the right partition as i indicated above? That is my first question. I tried to do this, and it gives me an error message when i boot to windows xp home. Is this even in the ballpark of what i am suppose to do. Any help would be appreciated. Thanks.

---

### Post by tangibleorange on 2008-10-07
could you please post the output of:

```
sudo fdisk -l
```

this will tell us what partitions are where.

---

### Post by cozmokramer8 on 2008-10-07
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        7655    61440592+  83  Linux
/dev/sda3            7656       30393   182642985    f  W95 Ext'd (LBA)
/dev/sda5            7656       30393   182642953+   7  HPFS/NTFS
kramer@Crypto:~$

---

### Post by kansasnoob on 2008-10-07
> **tangibleorange said:**
> could you please post the output of:

```
sudo fdisk -l
```

this will tell us what partitions are where.

+1 -- I might add that's a lower case L at the end rather than a one!

It would also help to see a copy of your menu list. Just go to terminal (as you did to run the previous command) and copy-n-paste this command:

```
cat /boot/grub/menu.lst
```

Then copy-n-paste the result here.

---

### Post by cozmokramer8 on 2008-10-07
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=59b05ddf-3ec6-4528-9e0b-d92d1aa4643d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=59b05ddf-3ec6-4528-9e0b-d92d1aa4643d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title Windows XP Home
root (hd0,2)
makeactive
chainloader +1

---

### Post by tariquepark on 2008-10-07
hi
if you change the
root (hd0,2)

to 

root (hd0,4)

that should solve your problem
the reason it is 4 and not 5 is because grub counts starting with zero not 1
cheers

---

### Post by cozmokramer8 on 2008-10-07
Tried switching it to partition 4 as you suggested and it gave me the error message 

ERROR 12 Invalid device requested
Press any key.....blah

I heard about something with windows being weird with being the "master" or something I don't know I am very new to this but they change the command a little in the other post they had something like
root (hd0, 4)
root (4 , hd0)
I can't remember it said something about mapping. Sorry I have been reading tons of post trying to fix this.

---

### Post by tariquepark on 2008-10-07
i think what you are referring to is that windows likes to be on the first partition of the drive and be and be a primary partition, whereas your xp is in an extended partition
have you tried reinstalling grub and see if it will find the xp install and add it to your menu.lst?
also has windows always been there on that partition or have you reinstalled it there?

---

### Post by pastalavista on 2008-10-07
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by cozmokramer8 on 2008-10-07
Yes windows has always been on that partition, and that is exactly what I was thinking. No I have not re-installed the GRUB. I am very new to ubuntu and linux and if it wouldn't be too much to ask do you think you could run me through it? I really don't want to mess it up and not even be able to boot to ubuntu.

---

### Post by kansasnoob on 2008-10-07
You know it just doesn't work having two threads going on the same problem!

I posted a reply on the other one!

You can try what I posted there, but your partitioning is a mess!

---

### Post by der_hede on 2008-10-07
Do you have deleted some old fat or ntfs partitions before installing ubuntu (sda1/sda2)?

Try mounting the windows Partition (/dev/sda5) and search for boot.ini and ntldr in the root directory. If there are no such files, it's for 100% shure Windows previously booted of from some other partition.

Try to chainload hd(0,0) and hd(0,1), maybe it's worth a try, but it's very unlikely.

If nothing helps, make some grub boot floppy (or usb boot stick / boot cd) and make shure it works. (pastalavista said how to obtain a simple grub bootdisk. Test if you can boot from it! Do only try to fix any mbr if you know you don't need it ;-) )

Then I would suggest to boot of a windows CD, fix your mbr for windows (search the internet for "windows fix mbr"). If this fails... ugh... you have deleted some needed partition. Windows can boot from one partition, for example a small dos one, even if %windir% resides on another one.

If this works and you can boot windows, everything would be fine. You can boot your linux with the grub bootdisk now, save the windows mbr to a file, reinstall grub to mbr and boot of windows from grub using the windows mbr file. You can even let the windows bootloader reside in mbr and boot grub of windows' boot.ini. For the later one you have to save your grub mbr in beforehand. (dd if=/dev/sda of=/towindowsmount/grub.mbr count=1)

---

### Post by tariquepark on 2008-10-07
do you have a live/desktop install cd or one of the alternate cds?
you need to boot the computer from the live disk, open a terminal and do this:

sudo grub
then 
find /boot/grub/stage1

this will give you something like (hd0,0)
 use the returned value and type
root(hd0,1) (or whatever the value is)
then 
setup (hd0)
then type
quit 
to exit the grub program
what this does is write the mbr (master boot record)
to the first sector of the hard drive
you can also install grub to any given partition (instead of the first sector)if needs be but i think this is the better way

---

### Post by der_hede on 2008-10-07
Did you ever tried to boot the "Dell Utility" entry? Maybe Windows is booting off this Partition!?

---

### Post by tariquepark on 2008-10-07
i wouldnt use the dell utility because that will erase everything and put only xp back on
unless this is what you want to do?

---

### Post by Bucky Ball on 2008-10-07
As suggested earlier, Super grub disk.

Download from:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

burn, boot from and see if that can get things going for you.

---

### Post by der_hede on 2008-10-07
> **tariquepark said:**
> i wouldnt use the dell utility because that will erase everything and put only xp back on
unless this is what you want to do?
Are you shure it will erase everything without asking first? Then I would definitely not try to boot it.

But before installing Ubuntu there must be a partition where the old Windows gets booted from and where the old Dell menu resides from where you can decide if you want to boot Windows or recover it. Isn't it? I do not know how this works with dell.

Nevertheless he can try to open this Dell partition. I think it's possible it is a ntfs or fat partition and there is some ntldr on it. Try searching for it and if there is a boot.ini. Open this boot.ini and look what kind of entries are in it.

And yes, the first thing to do is to make some working boot media. The Super Grub Disk is fine (if a floppy is present, a simple "grub-install '(fd0)'" would do the same, but maybe SGD is easier and there's a good howto at their wiki)

---

### Post by tariquepark on 2008-10-07
i have only used the dell utility twice and both times there were no options just a 10 min wait then xp came up no prompts at all, which is why i worry about using it, ever! i just dont like not having control over these things especially when data is at stake
in regards to sgd, i really dont see the need for it because everything you need is on the live disk, its just a case of knowing how to use it, which is the main issue new users have when something like this happens. i dont mean to sound condescending but i dont think telling new linux users to go and use another different program is the best way to help. teaching them how to use what is already there, indeed an integral part of the OS is a much better option IMHO
if reinstalling grub does not fix the problem then i think its probably not a grub issue at all but more likely an error in XP's ntldr
the other thing that might be worth a try is to boot from an xp disk go to recovery mode and type fixmbr at the command prompt and see if xp will boot?
if it does then reboot with the ubuntu live disk again and reinstall grub again and see what happens

---

