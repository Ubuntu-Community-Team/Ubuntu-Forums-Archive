---
title: "Filesystem"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by openation1 on 2012-04-16
hello everyone. I know ubuntu is running on filesystem ext4, I want to use filesystem ext2, what do I have to do?

---

### Post by dniMretsaM on 2012-04-16
During the installation process, you have to manually set up your partitions (the option might be called "Something Else"). You can then choose to use an EXT2 filesystem.

---

### Post by PhantomTurtle on 2012-04-16
You'll have to reinstall then and do manually partition(which is not hard). Make sure to pick ext2 for your / partition.

---

### Post by oldfred on 2012-04-16
Why would you want ext2? Or is this an SSD or small /boot partition? 

You can used non-journaled filesystems if the partition is smaller, but for anything else it is not recommended.

If an SSD, you can use ext4, but turn the journal off. Supposedly that is better than ext2.

sudo tune2fs -O ^has_journal /dev/sda1

---

### Post by d4m1r on 2012-04-16
Is EXT2 even supported by new Ubuntu installs (including 11.10)? I would highly recommend sticking to EXT4 for all newer Ubuntu installs to ensure compatibility.

EXT2 is several years old now and EXT4 does everything it does, plus more, and faster too ;)

---

### Post by openation1 on 2012-04-16
well extension 2 is the original for linux used in slackware I heard is faster and more stable than ext4.......

---

### Post by oldfred on 2012-04-16
It definitely is not faster on startup file checks, and when ext4 first came out it was not as reliable as ext3. 

But a journalized system will always be more reliable than a non-journalized system. Some settings on when writes occur can change reliability also, both better or worse.

The only place to consider a non-journalized format is a small partition where a filecheck can be run quickly. As soon as file system is large then journal becomes more important.

---

