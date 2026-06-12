---
title: "Easy way to clone an Ubuntu PC"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by dtree46 on 2014-01-04
What is the easiest way to clone an Ubuntu PC?
As simple as one click... maybe?

Don

---

### Post by Mark Phelps on 2014-01-04
I take it what you mean is to clone an Ubuntu PC "installation", right?  That means copying all the partitions on the hard drive to another drive.  In this case, the other drive must be as large, or larger (in terms of capacity) as the original drive.

Is that what you want to do?

---

### Post by mastablasta on 2014-01-04
not one click but have a look at RedoBackup and or also Clonezilla.

---

### Post by dtree46 on 2014-01-04
Yes, I want to copy -backup- all software, data and system onto another hard drive.
However, my hd is 1tb. What I now backup on is 250mb.
Obviously I can not copy 1tb to 250mb.
So, can I do it to DVD's?

---

### Post by dtree46 on 2014-01-04
Downloaded and ran RedoBackup.
Thanks for the tip.

dlw

---

### Post by Mark Phelps on 2014-01-04
If you were able to do a "backup" of your 1TB installation to a 250GB drive, then what really happened is that RedoBackup created a compressed image file on the new drive -- not a "copy" of what you have on the 1TB drive.  That means you can't actually run using the 250GB drive as it is a compressed image backup.

Clonezilla will actually "clone" one drive to another -- but since it is making an exact copy, the second drive must be at least as large as the first drive.

---

### Post by dtree46 on 2014-01-04
It used the 1tb to backup.
Therefore there is a compressed image on the 1tb... right?
Since only 80Gb are used on the 1tb, is there a way to do an exact copy of the 80Gb?

---

### Post by monkeybrain20122 on 2014-01-04
> **Mark Phelps said:**
> 

Clonezilla will actually "clone" one drive to another -- but since it is making an exact copy, the second drive must be at least as large as the first drive.

That's why I use fsarchiver instead of Clonezilla. For fsarchiver the partition to restore to just has to be big enough to hold all the data. With Clonezilla the target to restore to has to be >= the original even though the original partition may be mostly empty. Fsarchiver is in the repo.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by monkeybrain20122 on 2014-01-04
> **dtree46 said:**
> It used the 1tb to backup.
Therefore there is a compressed image on the 1tb... right?
Since only 80Gb are used on the 1tb, is there a way to do an exact copy of the 80Gb?

Yes, use fsarchiver. You can clone your Ubuntu partition even when Ubuntu is running, just don't install software or otherwise alter the system when you are cloning (use -a  and -A options with savefs)

---

### Post by sammiev on 2014-01-04
I tested RedoBackup and it backup worked very well. Then I restored the backup which went very well. I tried to backup that fresh copy to my backup drive and RedoBackup would not find my HD that was restored by RedoBackup . For this reason I will not use RedoBackup. Clonezilla is my first choice.

---

