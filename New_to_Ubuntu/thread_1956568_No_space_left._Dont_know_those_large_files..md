---
title: "No space left. Dont know those large files."
date: 2012-04-11
forum: New to Ubuntu
---

### Post by VicenteAtl on 2012-04-11
Hello,
I am having the message of no space left. If I do df -h I get:

/dev/sda1     ext4     14G   13G  4.0K 100% /
udev      devtmpfs    2.9G  4.0K  2.9G   1% /dev
tmpfs        tmpfs    1.2G 1016K  1.2G   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    2.9G  756K  2.9G   1% /run/shm
/dev/sda8     ext4    412G   37G  355G  10% /media/sda8
/dev/sda6     vfat     67G   65G  2.2G  97% /media/sda6
/dev/sda2  fuseblk     81G   61G   21G  76% /media/OS


So it is really full. I search for the heavy files with sudo find / -name '*' -size +1G and find:

/media/OS/hiberfil.sys
/media/OS/pagefile.sys
/media/OS/System Volume Information/{7fb7c153-587b-11e1-81c6-8e766726f236}{3808876b-c176-4e48-b7ae-04046e6cc752}
/media/OS/System Volume Information/{93e65852-5562-11e1-b115-f1cce1a3c492}{3808876b-c176-4e48-b7ae-04046e6cc752}
/media/OS/System Volume Information/{9c4be56a-61f9-11e1-8ca4-e353f2b76e48}{3808876b-c176-4e48-b7ae-04046e6cc752}
/media/OS/System Volume Information/{a76d96af-572c-11e1-adc2-95e14c993b48}{3808876b-c176-4e48-b7ae-04046e6cc752}
/proc/kcore
find: `/proc/2942/task/2942/ns/net': No such file or directory
find: `/proc/2942/task/2942/ns/uts': No such file or directory
find: `/proc/2942/task/2942/ns/ipc': No such file or directory
find: `/proc/2942/ns/net': No such file or directory
find: `/proc/2942/ns/uts': No such file or directory
find: `/proc/2942/ns/ipc': No such file or directory
find: `/proc/3235/task/3235/fd/5': No such file or directory
find: `/proc/3235/task/3235/fdinfo/5': No such file or directory
find: `/proc/3235/fd/5': No such file or directory
find: `/proc/3235/fdinfo/5': No such file or directory
find: `/home/vicente/.gvfs': Permission denied


The thing is that I really dont know what are these files and what should I do with them, and if they are the ones causing the problems. What sould I do ?

Thanks in advance

Vicente

---

### Post by sanderj on 2012-04-11
/media/OS/hiberfil.sys
/media/OS/pagefile.sys

... isn't that Windows stuff? Is there Windows intalled on the harddisk, and do you want to keep it? If so, don't touch the /media/OS/ stuff.

About kcore: "the kcore file is only a virtual file. It contains the RAM the kernel can allocate. Therefore this should not be touched or read."

So no files bigger than 1GB that you can remove.

---

### Post by audiomick on 2012-04-11
I think you should consider using a partitioning tool to take some space from sda8 and give it to sda1.

Sda1 is the partition that is full. None of the stuff that is mentioned in your output seems to be there, so I don't think any of it is relevant to your problem.

Sda8 is nearly empty, and on the same drive as the full sda1 partition, so I think a little partition re-sizing would solve your problem.

Edit: Do you have a separate /home partition? I see that your sda1 is listed as the system partition / . Is you home in there, or is it separate?
The reason for asking is that if it is separate, you might find you can't slim down your system partition all that easily. If, however, you /home is in there as well, you might be able to move some stuff out of your /home folder to make some room.

---

### Post by philinux on 2012-04-11
> **VicenteAtl said:**
> Hello,
I am having the message of no space left. If I do df -h I get:

/dev/sda1     ext4     14G   13G  4.0K 100% /
udev      devtmpfs    2.9G  4.0K  2.9G   1% /dev
tmpfs        tmpfs    1.2G 1016K  1.2G   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    2.9G  756K  2.9G   1% /run/shm
/dev/sda8     ext4    412G   37G  355G  10% /media/sda8
/dev/sda6     vfat     67G   65G  2.2G  97% /media/sda6
/dev/sda2  fuseblk     81G   61G   21G  76% /media/OS


So it is really full. I search for the heavy files with sudo find / -name '*' -size +1G and find:

/media/OS/hiberfil.sys
/media/OS/pagefile.sys
/media/OS/System Volume Information/{7fb7c153-587b-11e1-81c6-8e766726f236}{3808876b-c176-4e48-b7ae-04046e6cc752}
/media/OS/System Volume Information/{93e65852-5562-11e1-b115-f1cce1a3c492}{3808876b-c176-4e48-b7ae-04046e6cc752}
/media/OS/System Volume Information/{9c4be56a-61f9-11e1-8ca4-e353f2b76e48}{3808876b-c176-4e48-b7ae-04046e6cc752}
/media/OS/System Volume Information/{a76d96af-572c-11e1-adc2-95e14c993b48}{3808876b-c176-4e48-b7ae-04046e6cc752}
/proc/kcore
find: `/proc/2942/task/2942/ns/net': No such file or directory
find: `/proc/2942/task/2942/ns/uts': No such file or directory
find: `/proc/2942/task/2942/ns/ipc': No such file or directory
find: `/proc/2942/ns/net': No such file or directory
find: `/proc/2942/ns/uts': No such file or directory
find: `/proc/2942/ns/ipc': No such file or directory
find: `/proc/3235/task/3235/fd/5': No such file or directory
find: `/proc/3235/task/3235/fdinfo/5': No such file or directory
find: `/proc/3235/fd/5': No such file or directory
find: `/proc/3235/fdinfo/5': No such file or directory
find: `/home/vicente/.gvfs': Permission denied


The thing is that I really dont know what are these files and what should I do with them, and if they are the ones causing the problems. What sould I do ?

Thanks in advance

Vicente

Try this guide to help you. 14gig is more than enough usually for root unless you use it for media files in home.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by drs305 on 2012-04-11
One of the important thing that the guide linked to by *philinux* is to unmount everything you can while investigating things. 

This will reveal whether certain files are mounted but actually on another partition or if the files have been written directly onto your system partition. 

For instance, a really large ISO may be on a CDROM but showing in /media, which would not be a problem. However, if the CDROM device is unmounted and it still displays in /media, it means the file has been written directly to your system's /media folder and is taking up space it probably shouldn't be.

---

