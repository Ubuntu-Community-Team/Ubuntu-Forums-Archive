---
title: "Install 12.04 over 11.10"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by greenelf on 2012-04-26
How can I do a fresh install over my broken 11.10 installation?

---

### Post by c2tarun on 2012-04-26
You can always format and then install :) boot from CD or Pen drive and then install.
 
***Hoping that you have separate home partition, that may save your imp data*** :)

---

### Post by Frogs Hair on 2012-04-26
You can choose the same or use the entire disk depending weather you have a dual boot or not.

---

### Post by grahammechanical on 2012-04-26
A screen shot of your hard disk partitions would be helpful in getting specific advice for your set up.

Basically you create a live CD of 12.04 and select the Install Ubuntu option and then select Something Else.

When you see a representation of your hard disk partitions you select the partition that holds 11.10. You then click Change and at the dialogue you set the partition to be used as Ext4, tick the format box and set the mount point as /

Now at this point you are set to install 12.04 over 11.10. Will you loose all your data? Do you have a separate /home partition?

Regards.

---

### Post by greenelf on 2012-04-26
> **Frogs Hair said:**
> You can choose the same or use the entire disk depending weather you have a dual boot or not.

I am dual booting. So I can just select the same partition that I created and overwrite all the files? Will the installer automatically wipe all the files on that partition? Will GRUB work normally after I install?

---

### Post by c2tarun on 2012-04-27
> **greenelf said:**
> I am dual booting. So I can just select the same partition that I created and overwrite all the files? Will the installer automatically wipe all the files on that partition? Will GRUB work normally after I install?
 
 
If only you'll ask the installed to do so. You can choose to format a particular partition and then install on it, or use it as it is. (I personally dont recommend second one, as better than this would be upgrading--this opinion may differ person to person).

---

