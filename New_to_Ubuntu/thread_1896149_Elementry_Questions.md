---
title: "Elementry Questions"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by mgm2010 on 2011-12-16
I am planning to install some variation of linux/fedora/ubuntu, in a separate partition, along with windows and in this connections I have some very elementary doubts.
1. Can I access my data/videos etc downloaded via windows from linux/fedora/ubuntu and vice versa ??
2. Is there any software in linux/fedora/ubuntu which can create compressed images of partitions which I can burn on dvd,s. And these images can then be used to restore windows/linux etc if any of these are corrupted ??
3. Which variation of linux/fedora/ubuntu would you recommend ??

---

### Post by taseedorf on 2011-12-16
Yes, you can access your data in Windows as long as you install ntfs-3g and mount the Windows partition in Linux.

You need to use Google to find the software, but yes there is.

As far as best version, I'd say install multiple and explore in a virtual machine.  I prefer Linux Mint. :)  Ubuntu is good for a beginner, though.

---

### Post by Mark Phelps on 2011-12-16
> **mgm2010 said:**
> I am planning to install some variation of linux/fedora/ubuntu, in a separate partition, along with windows and in this connections I have some very elementary doubts.
1. Can I access my data/videos etc downloaded via windows from linux/fedora/ubuntu and vice versa ??
Not really.  Linux distros can access Windows format partitions, but it's generally a BAD idea to make changes to those partitions from inside Ubuntu.  If you really want to share data amongst different OSs, a better solution is to use a common NTFS-formatted data partition.  And, Windows in general, can not read Linux filesystems -- without some tweaking.
> 2. Is there any software in linux/fedora/ubuntu which can create compressed images of partitions which I can burn on dvd,s. And these images can then be used to restore windows/linux etc if any of these are corrupted ??
The best imaging/restore software for Windows filesystems is Macrium Reflect -- and the free version has what you need to do that.  For Linux filesystems, consider using Clonezilla.
> 3. Which variation of linux/fedora/ubuntu would you recommend ??
Depends on what you want -- just try them all and see what works best for you.

---

### Post by anewguy on 2011-12-16
For Windows, +1 on Macrium Reflect.  It works very well, very easily, and the data is easily accessed.  Just be sure to create the boot disk via Macrium Reflect first.

Dave ;)

---

