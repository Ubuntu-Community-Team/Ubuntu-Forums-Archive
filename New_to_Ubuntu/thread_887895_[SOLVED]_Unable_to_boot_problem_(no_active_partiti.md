---
title: "[SOLVED] Unable to boot problem (no active partition)"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-08-12
Hi,

I think I've done something rather stupid! 

I had some free space on my laptop so I thought I try another linux distro as well just to see how I liked it compared to Ununtu (SUSE 11.0) Well something was weird about the grub boot loader in that it first went to a SUSE grub and then when I clicked on the Ubuntu option I then got my original grub installed by ubuntu and had to click again. So I just deleted that partition.

Now when boot up I get a error message saying "no active partion" and it does nothing more. I cant do anything! I know I deleted the correct partition and not my Ubuntu one or the Windows one. What should I do next to correct this? Can I do it from the live CD disk?

---

### Post by Crafty Kisses on 2008-08-12
Check if your HD is your primary boot device in your BIOS, that's one solution, or put your LiveCD in and post the output of:
```
sudo fdisk -l
```

---

### Post by mariane_08 on 2008-08-12
> **Codename said:**
> Check if your HD is your primary boot device in your BIOS, that's one solution, or put your LiveCD in and post the output of:
```
sudo fdisk -l
```

HD is primary and result is the same! With live CD the result is:

ubuntu@ubuntu: ~$ sudo fdisk -l
Disk /dev/hda: 40:0 GB 40007761920 bytes

Device Boot     Start    End      Blocks        ID     System
/dev/hda1       1        2550     20482848+     7      HPFS/NTFS   
/dev/hda2       3826     4864      8345767+     5      extended
/dev/hda5       3826     4813      7936078+     83     linux
/dev/hda6       4814     4864       409626      82     linux swap/solaris

---

### Post by mariane_08 on 2008-08-12
I should add that I can't boot into windows either...nothing!

After "Error No active Partition" there's some giberish about Realtek fast etherenet controller and then "PXE-E61 media test failure, check cable" Does this help or is this just incidental?

---

### Post by caljohnsmith on 2008-08-12
I think I know exactly what you are experiencing based on my own experience when installing other distros; when you installed SUSE, it took over your MBR, but it gave you an option to boot Ubuntu. Well now that you deleted SUSE, the Grub in the MBR is still looking in the SUSE partition for all its config files, which of course don't exist anymore.

Anyway the solution is really simple, just boot a Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return a partition in the form (hdX,Y), which should be your Ubuntu partition][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR, but it will point to the Ubuntu partition for all its config files (including menu.lst of course).

---

### Post by mariane_08 on 2008-08-12
> **caljohnsmith said:**
> I think I know exactly what you are experiencing based on my own experience when installing other distros; when you installed SUSE, it took over your MBR, but it gave you an option to boot Ubuntu. Well now that you deleted SUSE, the Grub in the MBR is still looking in the SUSE partition for all its config files, which of course don't exist anymore.

Anyway the solution is really simple, just boot a Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return a partition in the form (hdX,Y), which should be your Ubuntu partition][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR, but it will point to the Ubuntu partition for all its config files (including menu.lst of course).

Thank you so much!! Yes that fixed it. I should have known that CA would come up with the answer (my home away from home!) as I thought about it I figured it had to be something along those lines since all I had done was delete the SUSE partition and touched nothing else. Maybe next time I should try uninstall.

Anyway thanks a lot!

---

### Post by caljohnsmith on 2008-08-12
> **mariane_08 said:**
> Thank you so much!! Yes that fixed it. I should have known that CA would come up with the answer (my home away from home!) as I thought about it I figured it had to be something along those lines since all I had done was delete the SUSE partition and touched nothing else. Maybe next time I should try uninstall.

Anyway thanks a lot!
Glad you've got your computer booting OK again. :) Just as a last note, I wanted to mention that a really easy way to manage multiple linux distros is first to decide which distro you want to manage the boot process (Ubuntu in your case), and then when you install other distros, have them install their Grub *to the boot sector of their own partition*, and not the master boot record (MBR). Then to load them, all you have to do is put in your Ubuntu menu.lst an entry like:
```

title		OpenSUSE
root		(hd0,4)
chainloader	+1
```
That way you don't have to worry about adding an entry that specifies the kernel, initrd, and all the correct boot options with the kernel. Let each distro figure that out for you, and then just "chainload" it to boot it from your main grub menu. And also, you can then delete any of your distros (other than the one controlling the MBR), and not have to worry about boot problems. :)

---

### Post by mariane_08 on 2008-08-13
> **caljohnsmith said:**
> Glad you've got your computer booting OK again. :) Just as a last note, I wanted to mention that a really easy way to manage multiple linux distros is first to decide which distro you want to manage the boot process (Ubuntu in your case), and then when you install other distros, have them install their Grub *to the boot sector of their own partition*, and not the master boot record (MBR). Then to load them, all you have to do is put in your Ubuntu menu.lst an entry like:
```

title		OpenSUSE
root		(hd0,4)
chainloader	+1
```
That way you don't have to worry about adding an entry that specifies the kernel, initrd, and all the correct boot options with the kernel. Let each distro figure that out for you, and then just "chainload" it to boot it from your main grub menu. And also, you can then delete any of your distros (other than the one controlling the MBR), and not have to worry about boot problems. :)

Thanks! Thats useful to know as I would like to at least try open SUSE even though I'll probably stick with Ubuntu :)

---

### Post by Pinho on 2008-11-28
> **caljohnsmith said:**
> I think I know exactly what you are experiencing based on my own experience when installing other distros; when you installed SUSE, it took over your MBR, but it gave you an option to boot Ubuntu. Well now that you deleted SUSE, the Grub in the MBR is still looking in the SUSE partition for all its config files, which of course don't exist anymore.

Anyway the solution is really simple, just boot a Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return a partition in the form (hdX,Y), which should be your Ubuntu partition][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR, but it will point to the Ubuntu partition for all its config files (including menu.lst of course).

This solution worked out fine for me too. Thank you very much!

---

### Post by klausner on 2010-03-28
> **caljohnsmith said:**
> Anyway the solution is really simple, just boot a Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return a partition in the form (hdX,Y), which should be your Ubuntu partition][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR, but it will point to the Ubuntu partition for all its config files (including menu.lst of course).

Unfortunately, that doesn't seem to work for me. My partion table looks like this:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             72332660  50076362  22256298  70% /Windoze
/dev/sda5              6720248   5080768   1298104  80% /
/dev/sda6               980308     63624    866888   7% /boot
/dev/sda7             46141380  34105028   9692472  78% /home
/dev/sda8             46141380  30444900  13352600  70% /usr/local

With /dev/sd6 being the intended boot partition. But when I follow your instructions, I get this:
> grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,6) 
root (hd0,6)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub> find /boot/grub/stage1  [COLOR="DarkOrchid"](Just to check)[/COLOR]
find /boot/grub/stage1
 (hd0,5)
grub> 

FWIW, "/boot/grub/stage1" *does* exist. Booting from a supergrub stick finds it with no problem, but I still get a blank grub prompt when I try to boot from the HD.
:(

---

### Post by oldfred on 2010-03-29
this is an old solved thread. You probalby should have started a new thread of your own.

run this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by klausner on 2010-03-30
[QUOTE=oldfred;9043330]this is an old solved thread. You probalby should have started a new thread of your own.

run this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt./QUOTE]


This seems to be a great diagnostic tool. Unfortunately, I can't see anything wrong in it, but I'm no grub expert.

The output was nearly 400 lines, so I thought that was a bit much to put in quotes. The output file is attached instead.

Thanks for the suggestion and for future help.

---

### Post by klausner on 2010-03-30
Per oldfred's suggestion, follow-ups should go to [this, newer thread]("http://ubuntuforums.org/showthread.php?p=9043646"), rather than duplicating postings.

Thanks.

---

