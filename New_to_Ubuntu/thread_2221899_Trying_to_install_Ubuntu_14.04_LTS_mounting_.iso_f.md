---
title: "Trying to install Ubuntu 14.04 LTS mounting .iso file"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by FarvezFree-D on 2014-05-04
Greeting fellow Ubuntu beginners and respected experts.

In the past, I've used Ubuntu 12.04 as my main OS and was forced to drop and switch back to Windows due to pressure from family, just cuz they ain't wanna get used to it.

Now years later, I just wanna switch back to Ubuntu on my better laptop. Now my problem is I don't have a new DVD or a fresh disc to burn and boot live. All I have is the .iso file and Daemon tools. And the installation is just not happening.

I tried the virtual box method, but it seems it only supports 32 bit. I've got 64. Need some help.

Thanks in advance and peace ya'll.

---

### Post by Impavidus on 2014-05-04
Can't you boot from usb? Most people have some that they could use for booting. You can even reuse it later for other purposes, just make sure you park any files you want to keep on a different drive.

---

### Post by slooksterpsv on 2014-05-04
A long time ago I did it via using free space on my HDD by making another partition. You have to go through a few hoops to make sure the boot sector doesn't get jumbled up. IIRC (I don't recommend doing this unless you're data is backed up and you'd be ok with reinstalling EVERYTHING if something messes up) I had to downsize a partition to create 2GB of FREE SPACE, formatted that to a Fat32 partition, use unetbootin to rip to that partition, then install plop inside windows to be able to target that partition to boot to the installation.

I can't remember exactly - I think I was able to install or maybe I had an issue where I couldn't see all my partitions on /dev/sda - it was a while ago so I can't remember. I don't recommend doing that and just hopping over to a store and purchasing a cheap 4GB pen drive for like $5.

---

