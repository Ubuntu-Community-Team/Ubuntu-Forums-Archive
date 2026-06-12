---
title: "Have question but too long for title."
date: 2008-11-27
forum: New to Ubuntu
---

### Post by JUDOHAWK on 2008-11-27
I have ubuntu on here, loving it so far but I want to dual boot XP.  XP doesn't recognize the harddrive when I go into setup so Im assuming it's the partition, no?  I partitioned the whole harddrive for linux and didn't make two of them.  I was wondering if I'd have to go into ubuntu setup and repartition just to dual boot both of them. Im sure someone knows something lol.

---

### Post by nakama85 on 2008-11-27
> **JUDOHAWK said:**
> I have ubuntu on here, loving it so far but I want to dual boot XP.  XP doesn't recognize the harddrive when I go into setup so Im assuming it's the partition, no?  I partitioned the whole harddrive for linux and didn't make two of them.  I was wondering if I'd have to go into ubuntu setup and repartition just to dual boot both of them. Im sure someone knows something lol.

Yes. If I understand correctly than xp no longer exists on your hard drive

if you want to make a xp (ntfs) partition at this point you will want to go into ubuntu and run terminal.

```
sudo gparted
```

and creat an ntfs partition for xp to be installed on

---

### Post by JUDOHAWK on 2008-11-27
Well I never had xp on my harddrive, but thanks for that. I had a feeling I had to do something like that.

---

### Post by nakama85 on 2008-11-27
> **JUDOHAWK said:**
> Well I never had xp on my harddrive, but thanks for that. I had a feeling I had to do something like that.

Glad to help

---

### Post by lswest on 2008-11-27
What you need to do is boot to the Ubuntu LiveCD.  Once it starts go to system-->administration-->partition manager

There you should shrink the ubuntu partition to a smaller size to free up space for XP.  This WILL take a while, so don't cancel it or reboot until it's done, best would be if you start it before going to bed and it should be done in the morning (unless you sleep less than 2 hours a day :P).  The time needed depends on the size of the partition, the clutter, and the read/write speed of your hdd.  Once that's done, make an ntfs partition from the free space, then boot to the XP install CD, and choose the NTFS partition that you want to install it to (should only be one).

Then, since XP will install its' bootloader, you'll need to restore GRUB using the following:
> For GRUB restore to MBR:
boot to the LiveCD (this is the easiest way IMHO) and then start a terminal (applications-->accessories-->terminal)and type:

```
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?)
quit
```


where the (hd?,?) and (hd?) corresponds to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).
If you would like a more detailed explanation catlett did a good job with his how-to [here]("http://ubuntuforums.org/showthread.php?t=224351") and also offers troubleshooting ideas. (taken from [my blog]("http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html"))

---

### Post by nakama85 on 2008-11-27
> **lswest said:**
> What you need to do is boot to the Ubuntu LiveCD.  Once it starts go to system-->administration-->partition manager

There you should shrink the ubuntu partition to a smaller size to free up space for XP.  This WILL take a while, so don't cancel it or reboot until it's done, best would be if you start it before going to bed and it should be done in the morning (unless you sleep less than 2 hours a day :P).  Once that's done, make an ntfs partition from the free space, then boot to the XP install CD, and choose the NTFS partition that you want to install it to (should only be one).

Then, since XP will install it's bootloader, you'll need to restore GRUB using the following:
 (taken from [my blog]("http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html"))

What lswest said

---

### Post by JUDOHAWK on 2008-11-27
> **lswest said:**
> What you need to do is boot to the Ubuntu LiveCD.  Once it starts go to system-->administration-->partition manager

There you should shrink the ubuntu partition to a smaller size to free up space for XP.  This WILL take a while, so don't cancel it or reboot until it's done, best would be if you start it before going to bed and it should be done in the morning (unless you sleep less than 2 hours a day :P).  The time needed depends on the size of the partition, the clutter, and the read/write speed of your hdd.  Once that's done, make an ntfs partition from the free space, then boot to the XP install CD, and choose the NTFS partition that you want to install it to (should only be one).

Then, since XP will install its' bootloader, you'll need to restore GRUB using the following:
 (taken from [my blog]("http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html"))


I think I can handle that lswest, but one question.  the (hd,?) stuff in there, Im assuming I have to replace the ? with something?  I know this sounds noobish, or will I know what to replace that with in the find command?   If you could help me out here that'd be great, and I have to admit, I love liveCDs lol.  So damn useful.

---

### Post by adult swim on 2008-11-27
whenever  you run find /boot/grub/stage1 it will return something like (hd0,0) use that number for the root (hd?,?) and just the first for (hd?)

---

### Post by JUDOHAWK on 2008-11-27
Thank you, that makes it much clearer.

---

### Post by kansasnoob on 2008-11-27
Perhaps this might help:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by JUDOHAWK on 2008-11-27
Another question and I feel even dumber XD

But, I resized it just fine, it says there is 25 GB of unallocated free space. I tried partitioning it as ntsf but that option is greyed out(this is from ubuntu here) and I can't do it from the xp setup disc because it still says it doesn't recognize a HDD.

---

### Post by lswest on 2008-11-27
probably because you're missing the ntfsprogs on the LiveCD.  I'd boot to Ubuntu, install GParted there along with the ntfsprogs with the following command: ```
sudo apt-get install gparted ntfsprogs
``` and then create the ntfs partition from there.  The reason it had to be done from the liveCD to resize is because you can't resize a partition that's in use.

Sorry about not being clear about what the ? should be replaced with, I was rushing out the door for school when I wrote that.

Glad we could help, and feel free to ask any more questions you might have.

---

### Post by JUDOHAWK on 2008-11-27
Thank you for that, I guess I need to learn a little bit at a time.

---

### Post by lswest on 2008-11-27
> **JUDOHAWK said:**
> Thank you for that, I guess I need to learn a little bit at a time.

We all do, I'm still learning something new every day.  As long as you're prepared to learn and aren't afraid to ask, then you'll do fine and learn everything you'll need to learn.

Glad we could help you out,
Lswest

---

### Post by Peter09 on 2008-11-27
Everyone seems to have given you some good advice here, I was just wondering what you were wanting XP for, if its gaming then thats OK, if you were needing to run applications that are not graphics intensive its worth considering VirtualBox before you go much further.

Sorry to confuse the issue :)

---

