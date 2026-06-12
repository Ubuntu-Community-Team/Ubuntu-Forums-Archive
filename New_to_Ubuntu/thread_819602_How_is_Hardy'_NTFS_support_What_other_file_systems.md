---
title: "How is Hardy' NTFS support? What other file systems work in both XP and Ubuntu?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by BigWoop on 2008-06-05
I'm not a linux expert, but as far as I know from reading a couple years ago, in linux ntfs is not that good, especially writing to ntfs volumes.

Is it any better these days and why is it not so good in the first place?

I'm interested because I want to set up a dual boot system with XP and Ubuntu, and have some volumes shared between the two OSes, so if not NTFS I have to use FAT32, unless there is another good file system someone can recommend that will work well in both.

Thanks.

---

### Post by shifty_powers on 2008-06-05
used it lots, and never had a problem. It is true that the ntfs support was a bit flaky at first, but now, the ntfs3g drivers are top notch.

---

### Post by michaelaly on 2008-06-05
I've had great results running a 500gb external on NTFS under Gutsy and Hardy. FAT32 works very well as a go-between file system as well. I haven't had any corrupted files, and there's a lot of reading/writing going on with very large files. 
There are ways to get windows to read ext3 file systems I believe, but I'm not sure how well it works. Maybe someone else can post more information.

---

### Post by F4l3 on 2008-06-05
> **BigWoop said:**
> I'm not a linux expert, but as far as I know from reading a couple years ago, in linux ntfs is not that good, especially writing to ntfs volumes.

Is it any better these days and why is it not so good in the first place?

I'm interested because I want to set up a dual boot system with XP and Ubuntu, and have some volumes shared between the two OSes, so if not NTFS I have to use FAT32, unless there is another good file system someone can recommend that will work well in both.

Thanks.
the best supported is FAT32. But NTFS works pretty well :)

---

### Post by starcannon on 2008-06-05
NTFS mounts, reads, and writes fine here.

---

### Post by BigWoop on 2008-06-05
OK it's good to see that it seems to work OK, as I might have to go with it, given FAT32 file and volume size limitations.

---

### Post by shifty_powers on 2008-06-05
there are also ext2 drrivers available for windows, but you might as well use ntfs...

---

### Post by kamitsukai on 2008-06-05
im using the ext2 filesystem and xp can read/write to it perfectly once the ext2 drivers are installed (takes 5 seconds)

---

### Post by darth_indy on 2008-06-05
I had to do some config to make NTFS work in Feisty, but in both Gutsy an dHardy there were no problems, and it all worked out of the box.

---

### Post by wootah on 2008-06-05
> **kamitsukai said:**
> im using the ext2 filesystem and xp can read/write to it perfectly once the ext2 drivers are installed (takes 5 seconds)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I use this driver with Windows XP Pro. Works great; never had any problems. The only problem with this driver is that is does not maintain the permissions :/

---

### Post by BigWoop on 2008-06-05
> **shifty_powers said:**
> used it lots, and never had a problem. It is true that the ntfs support was a bit flaky at first, but now, the ntfs3g drivers are top notch.

Is ntfs3g included with Hardy by defualt?

---

### Post by starcannon on 2008-06-05
Yes its included in the default install.

---

### Post by pasisti on 2008-06-05
So writing on an external NTFS hard drive with an clean Ubuntu 8.04 install won't be risky? If there was a risk of something happening, what would it be?

---

### Post by starcannon on 2008-06-05
I will make no warranties expressed or implied, I can give you my testimonial experience in that I have personally had no data corruption reading, and writing to ntfs since feisty.

---

### Post by Kevbert on 2008-06-05
NTFS and FAT32 seem to work fine here in Gutsy and Hardy Ubuntu and Kubuntu.

---

