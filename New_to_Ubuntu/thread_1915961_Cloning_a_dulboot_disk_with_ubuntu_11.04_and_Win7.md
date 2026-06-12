---
title: "Cloning a dulboot disk with ubuntu 11.04 and Win7"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by AliSajidImami on 2012-01-27
Hi everyone.
I hae a problem. I just bought a new pc with a larger drive. (1TB). I have an older 320 GB drive with dual booted Ubuntu 11.04 and win 7. Now i wanted to clone it to my new hard disk instead of losing all my data and settings and all that.

I saw a post 6 years old that suggested dd, but i am looking into using 'clonezilla'. Any opinion whether clonezilla can handle dual boot? Any problems to anticipate?

EDIT: I should mention that I used GParted to copy each drive to the newer hard disk. But it seems to have messed up, as i no loner et the grub screen, and win7 doesn't boot, but throws an error.

---

### Post by haqking on 2012-01-27
> **AliSajidImami said:**
> Hi everyone.
I hae a problem. I just bought a new pc with a larger drive. (1TB). I have an older 320 GB drive with dual booted Ubuntu 11.04 and win 7. Now i wanted to clone it to my new hard disk instead of losing all my data and settings and all that.

I saw a post 6 years old that suggested dd, but i am looking into using 'clonezilla'. Any opinion whether clonezilla can handle dual boot? Any problems to anticipate?

clonezilla will do everything you want.

Dualboot is irrelevant.

It just clones a bit by bit stream of the HDD

You may want to choose expert mode and choose the option which pertains to grub which i cant remember what it says now but if you have a problem booting after the clone then go back do it again and choose the grub option in the expert mode.

Cheers

---

### Post by AliSajidImami on 2012-01-27
[http://www.clonezilla.org/clonezilla-live/doc/03_Disk_to_disk_clone/advanced/05-advanced-param.php](http://www.clonezilla.org/clonezilla-live/doc/03_Disk_to_disk_clone/advanced/05-advanced-param.php)

Did you mean the '-g auto' option given above?

Thanks for the reply.

---

### Post by haqking on 2012-01-27
> **AliSajidImami said:**
> [http://www.clonezilla.org/clonezilla-live/doc/03_Disk_to_disk_clone/advanced/05-advanced-param.php](http://www.clonezilla.org/clonezilla-live/doc/03_Disk_to_disk_clone/advanced/05-advanced-param.php)

Did you mean the '-g auto' option given above?

Thanks for the reply.

yeah you may find that with that enabled you might have a grub issue when booting.

If you do then remove it and the original grub will remain in place.

Peace

---

### Post by Mark Phelps on 2012-01-27
You can also try the FREE version of Macrium Reflect.  It's a Windows product, but it will clone the drive.

---

### Post by AliSajidImami on 2012-01-27
I just finished. Worked like a charm. Thanks. :)

---

### Post by haqking on 2012-01-27
> **AliSajidImami said:**
> I just finished. Worked like a charm. Thanks. :)

no worries, you are welcome.

remember to use the thread tools menu to mark as solved to help others when searching for solutions.

Cheers

---

