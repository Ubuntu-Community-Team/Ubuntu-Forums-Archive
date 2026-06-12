---
title: "How to make a grub floppy on Ubuntu and use it to install grub to your hard drive if"
date: 2006-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by catlett on 2006-07-27
First insert a blank floppy into the floppy drive but do not mount it.
Use the floppy formatter under Applications<System Tools<Floppy Formatter to format the floppy to Linux Native(ext2).
Open a terminal and enter
```
sudo mkfs /dev/fd0
```
Now mount the floppy```
sudo mount /media/floppy0
```
Enter these commands in the terminal
```
sudo mkdir -p /media/floppy0/boot
```
```
sudo cp -r /boot/grub /media/floppy0/boot
```
Then unmount the floppy
```
sudo umount /media/floppy0
```

If you ever loose grub and need to use your floppy to boot into your system, this is how to put grub back on your hard drive. (this example will put grub on the mbr of the first ide hard drive. if you use sata then use the corresponding label wich I think is /dev/sda {I do not have a sata drive})
Now that you can boot into your normal Ubuntu install, open a terminal and enter this command
```
sudo grub-install /dev/hda
```

Grub will install to the mbr. You will have grub on your hard drive.

**A couple of notes. If you do not find floppy formatter in the menu. Open alacarte menu editor, which is under Applications<Accessories<alacarte menu editor, highlight the system tools and then check off Floppy Formatter when the options appear.
*/dev/hda is used in my example because I have an ide drive. If you do not have an ide drive use the label /etc/fstab uses for your drive. You can see your fstab by using this command ```
cat /etc/fstab
```Use the label but do not use any numbers i.e. /  /dev/sde1 defaults....use /dev/sde do not use the number after the letter.
*if you are using another distro, sudo would represent a root terminal, so open a root terminal and enter the commands that follow sudo.Also check to see where your distro mounts the floppy, it may not be /media/floppy0
*for some reason this is the only way I can get grub to install to a floppy. sudo grub-install doesn't work, also using mk2fs from the command line didn't work either. The only combination that worked was using the formatter to make an ext2 and then using the command line to mkfs.
*this list of instructions is basically a reprint of these instructions [http://ubuntuforums.org/showthread.php?t=6195](http://ubuntuforums.org/showthread.php?t=6195) , except I had to change the mkdir and cp commands a little bit to make it work (for me at least. maybe the original will work for you)

---

### Post by confused57 on 2006-07-27
Nice "HowTo's"...I've bookmarked both of yours, it'll be easy just to refer someone to them.

---

### Post by jediborger on 2006-09-11
You could also add the termainal command for the floppy formatter [FONT="Courier New"]gfloppy[/FONT] That way there will be no confusion over enabling the menu entry for it.:D

---

### Post by catlett on 2006-09-11
> **jediborger said:**
> You could also add the termainal command for the floppy formatter [FONT="Courier New"]gfloppy[/FONT] That way there will be no confusion over enabling the menu entry for it.:D

Thanks for th tip. I always hated using the floppy formatter because it isn't always available on people's menus but I couldn't get the disk to boot without it. It would always come up with an error on boot of "filesystem unknown" and wouldn't boot to anything. So thanks for the information, I'll have to go use it now and then edit or make another thread.

---

### Post by AT-AT on 2006-09-28
Okay, so I made the floppy, but Im not sure what to do next. Do I restart the computer and insert the floppy? If so, the comp said the floppy was not a boot disk. If one is supposed to enter the '
[LEFT]sudo grub-install /dev/hda' immediately after unmounting the floppy the terminal tells me that 'The file /boot/grub/stage1 not read correctly'. Does this mean that my stage 1 file is corrupted?
 
Finally, what if I wanted to create a bootable floppy that uses grub (ie, everytime I start my comp, the bootloader is used from a floppy, not the MBR on the HD), can I do that?[/LEFT]

---

### Post by catlett on 2006-09-28
All you do is insert the floppy and reboot. If it worked correctly, the computer boots into the grub menu.
After you make a selection, and boot into your system, then you do the grub install.
For this to work, you need to have grub working properly already. 
If grub is not working but it was installed before you had some problem, you can get it back by using the live cd [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
If you do not have grub, you can download the image and make a grub floppy by following spoj's fifth reply in this thread [http://www.ubuntuforums.org/showthread.php?t=248103](http://www.ubuntuforums.org/showthread.php?t=248103) 
> OK, time to conclude this thread...

This appears to be the way to "use" or install or setup the grub-disk package:-

   1. Insert a scratch floppy disk (do not mount)
   2. Uncompress the ext2fs package:
      

```
      sudo gunzip /usr/share/grub-disk/grub-0.97-i486-pc.ext2fs.gz
```

   3. Write image to floppy:
      

```
      sudo dd if=/usr/share/grub-disk/grub-0.97-i486-pc.ext2fs of=/dev/fd0 bs=512
```

   4. Mount floppy and cd to grub area on floppy:
      

```
      mount /media/floppy cd /media/floppy/boot/grub
```

   5. Write grub stage1 to boot sector:
      

```
      sudo grub
```  at the grub prompt i.e. grub>```
 root (fd0) 
```grub> ```
 setup (fdo)
```

      This will eventually report a "disk write error", but still seems to do the job, and also reports the stage1.5, stage2 and menu.lst files that are present on the floppy.

---

### Post by pe1800 on 2007-03-10
I did everything you said to create this floppy. The system will not let me see what's on the floppy even though I am the root user.

Next, when I rebooted my floppy was ignored. Even though my BIOS will boot into DOS from a floppy that I have.

GRUB is working. I have a choice of WXP and Ubuntu. I assume GRUB is installed with the Master Boot Record. How can I see the MBR and GRUB?

---

### Post by gooner11 on 2007-11-20
I cant even mount the floppy what am i doing wrong?

I have tried so many guides to do this but none of them work for me. All of the commands that I put dont work.

---

### Post by dhenton9000 on 2008-01-12
I wasn't able to get this to work as such, but I added the following from 
[http://www.linuxjournal.com/article/4622]("http://http://www.linuxjournal.com/article/4622")


[LIST=1]
[*]sudo grub
[*]grub> root (fd0)
[*]grub> setup (fd0)
[*]grub> quit
[/LIST]


I'm not sure anybody covered it here, but the procedure in the first post does not add anything to the boot area of the floppy, it just prepares the filesystem and adds the needed menu files. it doesn't put stage 1 and 2 into the first 512 of the floppy. This is similar to catlett's 2nd post, but does not require the grub image. So follow the first post if you like, then try these commands.

Anyway, I now have a floppy that contains my grub menu and allows me to dual boot into Ubuntu or XP.

---

