---
title: "I need to delete all of my partitions from the command line."
date: 2008-10-04
forum: New to Ubuntu
---

### Post by EvilDaemon on 2008-10-04
Hey.

I have screwed up grub all weird. I'm trying to install ubuntu server, but it's the same with all the os - It won't overwrite everything. I want it so that it's only ubuntu server on there. I tried sudo cfdisk, and deleted everything I could find, while on an ubuntu 7.10 livecd. Can anyone help me? I was suggested that sudo rm -rf / would do the trick, but I'm not that blind. All my data is backed up, it's just the problem of unclogging it. I've also considered DBAN, is this what I want? Or can I do it from the command line.

Thanks ahead of time.

---

### Post by mojoman on 2008-10-04
> **EvilDaemon said:**
> Hey.

I have screwed up grub all weird. I'm trying to install ubuntu server, but it's the same with all the os - It won't overwrite everything. I want it so that it's only ubuntu server on there. I tried sudo cfdisk, and deleted everything I could find, while on an ubuntu 7.10 livecd. Can anyone help me? I was suggested that sudo rm -rf / would do the trick, but I'm not that blind. All my data is backed up, it's just the problem of unclogging it. I've also considered DBAN, is this what I want? Or can I do it from the command line.

Thanks ahead of time.

Couldn't you just use the Ubuntu server installation disk's own partition manager? I don't know which server edition you're using but the installation process will lead you to set up partitions. Define them up as you want them and write the changes to disk. Make sure to check the "format partition" alternative.

---

### Post by paul_mcl on 2008-10-04
rm -rf /* will delete anything from mounted volumes only. Try one of partition managers: parted, fdisk, cfdisk, sfdisk.

---

### Post by EvilDaemon on 2008-10-04
mojoman: When I did that before, it overwrote everything except 7.10, and nothing seems to delete it.

paul_mci: I used cfdisk, it's still there.

---

### Post by mojoman on 2008-10-04
> **EvilDaemon said:**
> mojoman: When I did that before, it overwrote everything except 7.10, and nothing seems to delete it.

Uhm, use the automatic format option (or whatever it's called), which uses the entire disk as one partition? (unless of course you have other stuff on the disk that you want to keep...)

---

### Post by EvilDaemon on 2008-10-04
So after tinkering around, seems that there's two hard drives. So what I ultimately want to do is 'join' them- start Ubuntu on sda (30.6 GB) and then have it dynamically expand into sdb (12.6 GB) when it needs to. Can someone help me with this? the first part is to get the OS off of sdb. Then I want to overwrite the one on sda, and then make it... expand. Right?

---

### Post by bodhi.zazen on 2008-10-04
I think you might want to look at LVM 

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

As far as deleting , there should be no need. You can boot a live CD and use fdisk or just format over the top or install with LVM.

---

