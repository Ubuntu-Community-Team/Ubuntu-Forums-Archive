---
title: "file recovery"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by frisco008 on 2008-10-18
I am using a live cd of ubuntu to recover some files off of a laptop.  I want to use an external hard drive plugged into the usb to do so...the external is ntfs and it won't mount...what do I do..help. 


Thanks:confused:

---

### Post by cariboo on 2008-10-18
What commands are you usinng to munt the external drive? How is the external drive formatted? Does the drive show up in dmesg when you plug it it. To check dmesg, open an Applcations-->Accessories-->Terminal and type:

```
dmesg
```

The output of dmesg should tell what the device number is, you should see something like sdb1. If you get a result then you should be able to mount it manually.

JIm

---

### Post by frisco008 on 2008-10-18
I have no clue...I stumbled on to ubuntu as it is.  I will have to look into what you said.  I just want to get files off of this laptop and reformat it and reinstall winxppro.

---

### Post by Xiong Chiamiov on 2008-10-18
Are you writing onto the external drive?  If so, you'll need the ntfs-3g driver (which is probably already installed with Ubuntu, although I don't know).

Someone else can probably help you with mounting it through the GUI-magic, but if necessary, I can help you mount it manually.

---

### Post by frisco008 on 2008-10-18
I don't really care how it is done I just need to get the external hard drive to be recognized thru ubuntu so I can transfer my files from the corrupt windows machine to the external hard drive.

Thanks

---

### Post by frisco008 on 2008-10-18
Bump...I really need to get these files off.


Thanks and sorry for being pesky.

---

### Post by jerome1232 on 2008-10-18
We can help you manually mount it but if it's not automounting I'm willing to bet you or whoever last used the drive didn't 'safely remove' it.

Ubuntu will not mount a drive that wasn't safely removed last time.

So let's try and mount and see if it throws errors or what.

To get started we need the output of this command. To open a terminal go Applications->Accessories->Terminal

```
sudo fdisk -l
```

(that's the small letter 'l' not the number 1)

---

### Post by frisco008 on 2008-10-19
It did error out....but it was a lengthy error and it did say something about that it was not removed properly.  So now what?  I am reformatting it in a windows machine so it has no partition on it.  But then what?

---

### Post by BDNiner on 2008-10-19
if it was not properly removed you need to connect the drive to a windows computer and boot it and then shut it down for windows to properly closed the NTFS file system. Reformatting the drive will also help, just make sure that you don't just unplug the drive when done, shut the computer down or eject it from windows.

---

### Post by bsharp on 2008-10-19
Since you're already reformatting the external, this really doesn't matter, but I believe you can mount a ntfs drive that wasn't properly removed by using the "-f" option of mount.

But, it doesn't matter since you reformatted it.

EDIT: After you delete the partition on the external, create a FAT partition. The FAT drivers have been around longer and are less likely (AFAIK) to corrupt any backups you are making.

---

### Post by jerome1232 on 2008-10-19
Just keep in mind fat isn't journaled and has a 4G file limit (which is the reason I couldn't use it if I wanted to, I have some very large archives)

---

### Post by frisco008 on 2008-10-20
ok the external still has a nearly 5 gig partition that is fat32 and 90ish that is NTFS.  I will plug it in in the morning and see what happens....got tired all of a sudden....oh ya I need sleep.

Thanks so far guys

---

### Post by frisco008 on 2008-10-20
Yay....It is working I got all the files off I needed.  Doing the reformat and properly removing the external more than likely helped....A huge thanks to all involved in this thread.  Ubuntu is a life saver.  Yay!!!

---

