---
title: "hdd allocation"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by 477145 on 2012-03-28
hi

i got a new computer yesterday running ubuntu. i installed the operating system on an 80GB ssd and after finishing the installation i added another HDD.

now i have a question: what settings do i have to change that all of the files i download / install / etc. are saved on the 2nd HDD? i want to keep the ssd clean save for the operating system...

thanks in advance

ps: this is my first time ever working with linux so i have very limited knowledge about my possibilities here.

---

### Post by MG&amp;TL on 2012-03-28
Putting /home on the second disk and everything else (/)  on the SSD should work.

This guide: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) deals with moving your /home around one disk, but I'm fairly certain it will work for a separate disk too, just make sure you get the device code right.

I'm pretty sure it would we be easier to do with the advanced partitioner on ubiquity though.

^^is fairly advanced, let us know if you need help. There's also [https://help.ubuntu.com/community/Partitioning/Home](https://help.ubuntu.com/community/Partitioning/Home) for extra help.

That scenario would put all of your files on the second disk, however anything you installed would go on the SSD.  I don't think that will be a problem, the operating system takes around 5GB space, after that, you've got 75GB for programs.

---

### Post by 477145 on 2012-03-28
ok

i've read the links you gave me, sounds very promising, unfortunately i got ahead of myself:

after formatting the 2nd drive i wasn't able to boot anymore. i temporarily fixed that by disconnecting the hdd but now i'm unsure about which option i should use in the formatting menu (i.e. master boot record / guid partition / etc.). also i noticed that after formatting the drive it provides "media/PartitionName" as the mount point. won't that conflict with my moving around /home? can i change that mount point?

again, thanks in advance

---

### Post by MG&amp;TL on 2012-03-28
I must admit to not having answers. Hopefully somebody else on the forum does. :(

As for Master Boot Record, that's one option you don't want. MBR is for booting things.

You can (I think) change the mount point, you can use /etc/fstab. [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by 477145 on 2012-03-29
everything's stable now, i followed your first link and used this guide to just switch my complete home folder to the 2nd harddrive; as far as i can tell it did what i wanted.

thanks a lot :)

---

### Post by MG&amp;TL on 2012-03-29
> **477145 said:**
> everything's stable now, i followed your first link and used this guide to just switch my complete home folder to the 2nd harddrive; as far as i can tell it did what i wanted.

thanks a lot :)

No problem, I hope it goes well for you. :)

---

