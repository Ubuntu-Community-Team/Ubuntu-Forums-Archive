---
title: "Do not have option for Hibernation"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by wilsonB on 2012-03-05
I now have the option to Hibernate from menu, but it doesn't go into Hibernation. It just sits there, no writting to the HD.
 Standby works.

Not sure if this is helpful.

Ubuntu 11.10
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   209717247   104857600    7  HPFS/NTFS/exFAT
/dev/sda2       209717248   241174527    15728640   1b  Hidden W95 FAT32
/dev/sda3       241174528   488355839   123590656    7  HPFS/NTFS/exFAT
/dev/sda4       488355840   488397167       20664   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 7969 MB, 7969177600 bytes
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192    15564799     7778304    b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500074283008 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976707583   488352768    7  HPFS/NTFS/exFAT

FSTAB file
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by mikewhatever on 2012-03-05
You seem to have a wubi installation, and 'Hibernation is not supported', according to the FAQ. [http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

---

### Post by wilsonB on 2012-03-06
Heya thanks for the reply.

Ya, thought I would try that Wubi windows installation. I guess I didn't pay attention to anything saying Hibernation wont work.
:-(
Thats a big game changer.
I would rather beusing GRUB instead anyway. What I want to do is be able to Hibernate windows / Ubuntu and dual boot instead of shutting down everytime to go into the other.





Anyway around it?

---

### Post by wilsonB on 2012-03-06
[http://geekztips.blogspot.com/2011/01/after-ubuntu-released-wubi-for-people.html](http://geekztips.blogspot.com/2011/01/after-ubuntu-released-wubi-for-people.html)

I found this, but am a little scared after spending countless hours configuring Ubuntu with this Wubi install.

I will wait for my SSD to come in the mail and reimage that with current before proceeding.

Any thoughts?

---

### Post by Frogs Hair on 2012-03-06
Since 12.04 will be released in late April I would wait because it will have support for five years. At that point you can consider weather you would like to stick with Wubi or install a traditional dual boot.

Unless you need hibernation now I would wait. If for some reason you have to use wubi due lack of a USB or DVD, You could try the procedure once 12.04 is installed before any backed up files from the previous installation have been added.

If you choose to wait make sure any procedure is applicable to 12.04 .

---

### Post by wilsonB on 2012-03-06
Thanks for the feedback.

Ya, I was thinking that myself. Wait and reinstall new release in April.
I heard that imaging a HD to SSD can be a problem with Linux.

So....

Now I need to start studying backing up/restoring in Ubuntu...

Thanks

---

### Post by Mark Phelps on 2012-03-07
Once you do install again and get hibernation working, do not make the mistake of writing to the Windows OS filesystem while it is hibernated.  Folks do that all the time without realizing that any changes they make will be lost when Windows awakens again.

---

### Post by wilsonB on 2012-03-07
> **Mark Phelps said:**
> Once you do install again and get hibernation working, do not make the mistake of writing to the Windows OS filesystem while it is hibernated.  Folks do that all the time without realizing that any changes they make will be lost when Windows awakens again.


Thanks for responding.. 

This is concerning. The only reason I would want Hibernation on Win 7 or Ubuntu is so I Hibernate one , while working in the other. 
Your saying that I should not write to the Win7 partition, when Win 7 is Hibernated.. Right?

---

### Post by Mark Phelps on 2012-03-07
> **wilsonB said:**
> Your saying that I should not write to the Win7 partition, when Win 7 is Hibernated.. Right?

EXACTLY.  This is a really BAD idea, because even though you CAN tamper with the Windows filesystem while the OS is hibernating, you should not.

Windows caches the filesystem info when it goes into hibernation, and restores that when it wakes up.  Thus, any changes made during hibernation are gone when it wakes up.

Problems arise when folks add or change files.  The new files are still there, but the filesystem catalog entries are NOT.  The changes are worse because the files have been modified but the filesystem catalog changes have been removed -- resulting in corrupted files.

---

### Post by wilsonB on 2012-03-07
> **Mark Phelps said:**
> EXACTLY.  This is a really BAD idea, because even though you CAN tamper with the Windows filesystem while the OS is hibernating, you should not.

Windows caches the filesystem info when it goes into hibernation, and restores that when it wakes up.  Thus, any changes made during hibernation are gone when it wakes up.

Problems arise when folks add or change files.  The new files are still there, but the filesystem catalog entries are NOT.  The changes are worse because the files have been modified but the filesystem catalog changes have been removed -- resulting in corrupted files.


I will keep the NTFS boot partition invisible in the future when hibernating. Thanks 

Wow, this was one of the best / detailed and HELPFUL responses I have ever gotten. Well explained and makes perfect sense. 
Do you by chance write any How-To documents ;-)

---

### Post by bcbc on 2012-03-07
You'd have to force mount a hibernated NTFS partition. It won't let you do it with a normal mount.

---

