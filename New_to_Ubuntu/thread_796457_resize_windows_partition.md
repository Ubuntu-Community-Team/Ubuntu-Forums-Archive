---
title: "resize windows partition"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by subfactors on 2008-05-16
My hard drive currently has the following partition:

/dev/sda1      ntfs        44.12GB    boot
/dev/sda2      extended    30.40GB
   /dev/sda5   ext3        29.11GB
   /dev/sda6   swap         1.29GB

I'd like to make the ubuntu partition larger, like 15GB more, by shrinking the xp partition, so it would look like the following,

/dev/sda1      ntfs        29.12GB    boot
/dev/sda2      extended    45.40GB
   /dev/sda5   ext3        44.11GB
   /dev/sda6   swap         1.29GB

I've tried to use GParted in ubuntu, but it wouldn't let me resize any partition. Can anyone help me please?

---

### Post by shifty_powers on 2008-05-16
you can get a gparted livecd, (google it), that will do that, BUT it is a risky thing to do so back up your data!

---

### Post by Canis familiaris on 2008-05-16
Well if one of your drives are mounted Gparted would not allow it be resized or deleted. I suggest you use [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") to resize your partitions.
Also backup your critical files before this operation as it is a risky process.

---

### Post by wolfen69 on 2008-05-16
> **subfactors said:**
> My hard drive currently has the following partition:

/dev/sda1      ntfs        44.12GB    boot
/dev/sda2      extended    30.40GB
   /dev/sda5   ext3        29.11GB
   /dev/sda6   swap         1.29GB

I'd like to make the ubuntu partition larger, like 15GB more, by shrinking the xp partition, so it would look like the following,

/dev/sda1      ntfs        29.12GB    boot
/dev/sda2      extended    45.40GB
   /dev/sda5   ext3        44.11GB
   /dev/sda6   swap         1.29GB

I've tried to use GParted in ubuntu, but it wouldn't let me resize any partition. Can anyone help me please?

in terminal:
```
gksudo gparted
```
then unmount the partition(s) you want to resize first. then you should have no problems.

---

### Post by subfactors on 2008-05-16
Thanks for everyone's replies.

The only concern I have about using the GParted Live CD is it may damage GRUB, then I couldn't boot into ubunut or xp anymore. Should I be concerning about that at all?

---

### Post by subfactors on 2008-05-16
> **wolfen69 said:**
> in terminal:
```
gksudo gparted
```
then unmount the partition(s) you want to resize first. then you should have no problems.

I tried that, the only thing I was able to do was deleting my xp partition, it didn't give me the option of resizing.

---

### Post by housam on 2008-05-16
The newer version of Gparted live CD will do the job without harming grub because it allow the resizing from both ends of the partition. but be careful when resizing the windows partition : backup your data first then defrag the partition 2-3 times and notice the position of the green mark - it is windows file system. you can not resize behind that green mark or you'll damage windows.

---

### Post by subfactors on 2008-05-16
Thank you so much!
I used the gparted live cd and partition the drive exactly the way I wanted without any problem.

---

