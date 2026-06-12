---
title: "[SOLVED] Sharing a HDD and permissions"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Fenris_rising on 2008-05-13
hi all

my 3rd week with 8.04 and alls well. one small thing though. having succesfully got my 2nd HDD to auto mount at boot (i use it for storage)
i find its set as read only. whats the simplest way to make it read and writable? please make it simple and include how to do this as root as im still getting to grips with being told i dont have the permissions to do certain things. I am the only user of the PC in question.

thanks in advance

---

### Post by kesman on 2008-05-13
How did you get it to auto-mount? If you edited fstab, there should be a flag to set a partition read-only(ro). Remove it and it should work fine.

---

### Post by Joeb454 on 2008-05-13
Also is it an NTFS drive or ext3?

---

### Post by Fenris_rising on 2008-05-13
i used the  ubuntu guide to automatically mounting HDD using the
app 'diskmounter'. as it happens id bookmarked it and therein was
also the 'code' to bring up the fstab file so you can edit it. i have deleted the ro from the line and im about to reboot and try it. cheers for
the heads up........it is getting easier to do the terminal stuff, its just remembering what to do and when :lolflag:

well i tried it and nothings changed, heres my fstab you can see i have removed the ro from the /sdc1 line and it is ntfs
mainly incase i ever need to boot up my sdb1 drive which has XP on it (note i have # it out as i dont need it auto mounting). all my music etc is on the sbc1 drive which is a 320GB HDD. if its relavent i cant manually unmount  it either as i dont have the right 'permissions'

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=181b9393-f671-46d7-85fb-6a50d00d425c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ef97bc65-9c4d-410f-95ba-733adfc65afe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#Added by diskmounter utility
#/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdc1 /media/sdc1 ntfs,user,fmask=0111,dmask=0000 0 0


scanning the forum i found this 'chown' and have edited it to suit me i think, is it right? run it in terminal and the drive will be mine?

sudo chown -R My NAME:MY NAME /media/sdc1 
ls -la /media

ok i ran it anyway, its still read only and i am still unable to unmount it at will due to the permissions. im sure its something ridiculously simple to sort it out but i dont know what.

sorted! i wasnt rebooting properly, i was ctrl+alt+ bkspc rather than a 'proper' reboot.

---

