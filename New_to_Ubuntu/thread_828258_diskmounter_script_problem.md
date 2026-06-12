---
title: "diskmounter script problem"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by misho21 on 2008-06-13
I have tried to mount my fat32 partitions using diskmounter script .. it made the task but my Arabic folder names now is "?????" just question marks! 
please help to restore the files and folder names and dont tell me to rename them one by one!
here is my fstab file contents: 

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0d97c1fc-9ef0-405f-8c29-c83e3f0f36cd /               ext3    relatime,erro$
# /dev/sda9
UUID=c35e82f6-62de-48df-aa4b-553596493a8f none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda6 /media/sda6 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda7 /media/sda7 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda8 /media/sda8 vfat rw,user,fmask=0111,dmask=0000 0 0[/PHP]
I wonder is it hopless?!

---

### Post by Hospadar on 2008-06-13
Howdy, I believe you need to add the "iocharset" option to the disks with arabic file names.  Not knowing what encoding exactly they are in, it might take a little guessing around (maybe try utf8 ).

Then end result will look something like ```
[COLOR=#000000][COLOR=#007700]/[/COLOR][COLOR=#0000bb]dev[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]sda1 [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]media[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]sda1 vfat rw[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]user[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]fmask[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0111,iocharset=utf8[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]dmask[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0000 0 0[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#0000bb]

[/COLOR][/COLOR]There are many different types of encoding which might possibly be the one you need (or I might be wrong altogether about this being the right option) so do some more googling on the topic and see what you can find out.  Hopefully this can at least get you pointed on the right track.

Here's a page i turned up with a little more info: [http://www.linuxfromscratch.org/lfs/view/development/chapter08/fstab.html](http://www.linuxfromscratch.org/lfs/view/development/chapter08/fstab.html) some of the instructions here might not be relevant as it's not ubuntu-specific, but it should help

---

### Post by misho21 on 2008-06-13
yes it wokrs great!
thank u so much!

---

