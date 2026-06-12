---
title: "Installed Windows 7 on Ubuntu"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by Geebsie on 2012-01-01
Right, so I needed some software for work that just wasn't available on Ubuntu so I had to install Windows 7. Now, I installed Windows 7 on a separate partition from Ubuntu, but now when I start my computer it automatically starts up Windows without even letting me choose to boot up in Ubuntu. Also, the old partition that Ubuntu was installed on doesn't show up on My Computer, only the new one does, but with the original size (i.e. a 300 GB HD, partitioned into 2x150 GB; the Windows partition is still 150 GB with all the other files on it intact).

I luckily had all my files on the Windows partition, but I find it a bit odd that the old partition would've just disappeared like that... thoughts?

---

### Post by wildmanne39 on 2012-01-01
Hi, widows always assumes it is the only operating system on the computer, you will need to reinstall grub, here is a link with a program that may be able to do it for you.
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)
Thanks

---

### Post by fleamour on 2012-01-01
Or use EasyBCD.

---

### Post by lolpenguin on 2012-01-01
Or use a LiveCD to reinstall GRUB manually.
It should be```
sudo grub-install /dev/sda/
```but I'm not sure. Don't try until you confirm.

---

### Post by Sunfist on 2012-01-02
I second the suggestion to try EasyBCD. I was having trouble with my dual-boot system from time to time until I got that and it greatly simplifies the whole process and if it does get messed up again, you can run it again and it fixes the problems. You can do it all manually, but BCD makes it a lot easier.

---

### Post by benpack101 on 2012-01-02
And to answer your other question, your Ubuntu partition is ext3 or something similar and that is not recognized in windows. It is still there, don't worry.

You will be able to see all of the drives in Ubuntu.

---

### Post by audiomick on 2012-01-02
> **benpack101 said:**
>  your Ubuntu partition is ext3 or something similar 
For an Ubuntu fresh installed newer than about 9.04, it will be Ext4.

---

