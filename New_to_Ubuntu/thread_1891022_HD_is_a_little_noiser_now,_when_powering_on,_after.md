---
title: "HD is a little noiser now, when powering on, after 4 years. Should I worry?"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by mikodo on 2011-12-04
My Hard-drive is a little noisy when powering on now, after 4 years of turning it on and off multiple time per day.  Is the Disk Utility a good indicator of the status of the drive? The only thing that seems different in all the sections of it, is that the "Spinup Time" is Normalized at "150" and the Worst is showing at "147". With every other section, Normalized and Worst are the same. Should I be worried about the status of my disk?

Below is a screenshot of Disk Utility.

EDIT: I hit Lubuntu by mistake; I still use Ubuntu 10.04; Next will be Xubuntu 12.04. :>)

Thanks.

---

### Post by jtokarchuk on 2011-12-04
Sometimes heads breaking down can sneak right past SMART and you won't see it coming.

I would say at this point the drive is still OK, but to keep diligent on your backups, as if the sound continues, something may fail in the future, and usually when heads fail and platters get scraped, data is rarely recoverable.

Also, Disk Utility is a good diagnostic for the drive, but sometimes you have to rely on intuition, as the mechanics can fail without warning.

As collisionystm has said, it would be wise to replace the drive, as while prices are large, the last drive I sent in for data recovery (that was recoverable) was about a $2000 touch.

---

### Post by collisionystm on 2011-12-04
> **mikodo said:**
> My Hard-drive is a little noisy when powering on now, after 4 years of turning it on and off multiple time per day.  Is the Disk Utility a good indicator of the status of the drive? The only thing that seems different in all the sections of it, is that the "Spinup Time" is Normalized at "150" and the Worst is showing at "147". With every other section, Normalized and Worst are the same. Should I be worried about the status of my disk?

Below is a screenshot of Disk Utility.

EDIT: I hit Lubuntu by mistake; I still use Ubuntu 10.04; Next will be Xubuntu 12.04. :>)

Thanks.


i would replace it. 

4 years is a pretty good life for a drive.

buy a new one. cheap insurance considering the price of them these days

---

### Post by mikodo on 2011-12-04
Thanks, I use Back in Time to back up my ~/. So, if I need to replace the drive; can I just reinstall with the same partitioning to the new drive and use Back in Time to bring /home data back?

Oops, I was responding to jtokarchuck.

---

### Post by collisionystm on 2011-12-04
> **mikodo said:**
> Thanks, I use Back in Time to back up my ~/. So, if I need to replace the drive; can I just reinstall with the same partitioning to the new drive and use Back in Time to bring /home data back?

yeah you should be able to!

it does not matter how you partition the drive. The home directory is all the same to that backup program so dont worry about remembering how you did it.

Personally i never do separate partitions because I never saw the point in it. It just makes your life more complicated when you have to worry about resizing stuff

---

### Post by mikodo on 2011-12-04
The other thing I was thinking of doing was using [this ]("http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/")newbie friendly guide and imaging the drive. It looks good, for a replacing a drive.

---

### Post by jtokarchuk on 2011-12-04
Cloning does work quite well, I do it everyday at my job as a Technician. I use a Paid Acronis, but CloneZilla is the same idea.

After your drive is cloned, you can then just extend your partitions (if the new drive is larger)

---

### Post by mikodo on 2011-12-04
> **jtokarchuk said:**
> Cloning does work quite well, I do it everyday at my job as a Technician. I use a Paid Acronis, but CloneZilla is the same idea.

After your drive is cloned, you can then just extend your partitions (if the new drive is larger)
Thanks. My external drive I backup to is is 500 GB. I will install a new 500 GB Internal HD. 

That should work right, or should I go with a bigger one, like 750 GB or 1TB? All imaging guides say to have at least the same size or bigger on the receiving drive.

---

### Post by jtokarchuk on 2011-12-04
Same size or bigger, makes no difference. if you are happy with 500GB, great, if you want a bigger size, great!

---

### Post by mikodo on 2011-12-04
> **jtokarchuk said:**
> Same size or bigger, makes no difference. if you are happy with 500GB, great, if you want a bigger size, great!
OK; Thanks, jtokarchuk and collisionystm!

:D

---

