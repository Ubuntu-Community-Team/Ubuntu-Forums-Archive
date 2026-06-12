---
title: "Trouble using Gparted."
date: 2008-10-09
forum: New to Ubuntu
---

### Post by ceaser_salad on 2008-10-09
Hi

Been running hardy for a week now, and just remembered that my second hard drive is still ntfs formatted. I'd like to format it to ext3, like my main hdd. Trouble is I dont have enough space to back up my files(roughly 60gb). 

I've got a 120gb drive I'm saving for an ibook upgrade, but its formatted to hfs+(or atleast thats what I thought, until I had a look at it in gparted). I'd like to format it to ext3 as well, for meantime, and then reformat it back to hfs+ when I install OSX on it. Will the mac bios read it once its ext3? I cant seem to get rid of the first 8 partitions.

This screen shot might make things clearer.

Thanks.

---

### Post by simtaalo on 2008-10-09
> **ceaser_salad said:**
> Hi

Been running hardy for a week now, and just remembered that my second hard drive is still ntfs formatted. I'd like to format it to ext3, like my main hdd. Trouble is I dont have enough space to back up my files(roughly 60gb). 

I've got a 120gb drive I'm saving for an ibook upgrade, but its formatted to hfs+(or atleast thats what I thought, until I had a look at it in gparted). I'd like to format it to ext3 as well, for meantime, and then reformat it back to hfs+ when I install OSX on it. Will the mac bios read it once its ext3? I cant seem to get rid of the first 8 partitions.

This screen shot might make things clearer.

Thanks.

simple answer is dont bother trying to convert the filesystem when you dont have anyway of backing up your data. find a friend with some spare space or something like that, i cant stress enough that playing around with gparted without having data backed up is foolish.

---

### Post by Nxion on 2008-10-09
Yes, It should read it fine. I have a mac book Pro and Ubuntu saw the partition and was able to format it to ext3 then after I was done I popped it back in the laptop and it saw hte ext and formatted it back to hfs+.

---

### Post by LowSky on 2008-10-09
Dont be a fool save your data b4 messsing with gParted

---

### Post by ceaser_salad on 2008-10-09
Ok, I'm glad that I'll still be able to use the 120 in my ibook. 

I guess I didnt make the link between needing to make a backup, and having an-used hard drive with sufficient space, clear enough. Sorry:-)

Looking at this screen shot, what should my next move be?

---

### Post by simtaalo on 2008-10-09
well seems from there you choose which filesystem you want the partition to use and then press add.

---

### Post by ceaser_salad on 2008-10-09
So would I set it to be a primary, or extended partition? 
And what do the free space before, and after settings refer to(sounds like a dumb question, but I've been on windows for the last 10 years, and never came across anything like that)?

---

### Post by ceaser_salad on 2008-10-09
Thanks for your help. I've partitioned the drive, and all seems well. 
Now I cant seem to copy-paste files into this drive(right clicking shows paste in grey). 

Is there something I've missed?

---

### Post by jerome1232 on 2008-10-09
Permissions, you don't have permission to copy to it.

you need to either chown it as you, or chmod it so anyone can write to it. You'll  need to adjust /media/mount-point to wherever it's mounted.

```
sudo chown $USER:$USER /media/mount-point
```

or

```
sudo chmod o+rw /media/mount-point
```

---

### Post by ceaser_salad on 2008-10-09
I tried those codes, and was told that no such file directory exists. Was I supposed to edit your codes? Still feeling my way around linux:-)

---

### Post by jerome1232 on 2008-10-09
Well yeah I don't know where the disk is mounted, you need to adjust the part that says /media/mount-point

If you aren't sure where's it's mounted type mount and it should give you a listing of where everything is mounted and post it here

```
mount
```

---

### Post by ceaser_salad on 2008-10-09
Doh...

Here you go.

---

### Post by jerome1232 on 2008-10-09
I'm guessing based on what you posted earlier that you formated this drive ext2 correct? If so then it's /dev/sdc1 mounted at /media/disk,

btw next time you post text output, just copy/paste into here (ctrl+shift+c when in the terminal)

```
sudo chown $USER:$USER /media/disk

#or to make it writeable to anyone

sudo chmod o+rw /media/disk
```

---

### Post by ceaser_salad on 2008-10-09
Ok. I'm getting closer now, but I think I missed something. I'm getting this message now:

"The folder "backup" cannot be copied because you do not have permissions to create it in the destination."

---

### Post by ceaser_salad on 2008-10-09
As my pc isn't on a network, and I'm the only one ever likely to use it, is there a way to disable the need for permissions?

---

### Post by ceaser_salad on 2008-10-09
I've been fiddling around on my own(sounds bad:-I), rebooted, and still get permission denied when I try to make a folder or paste a file.

---

### Post by caljohnsmith on 2008-10-09
Ceaser_salad, if you want to copy your files and are having problems with permissions, one way to do it is to open Ubuntu's graphical file browser as root user:
```
gksudo nautilus
```
Then simply do a copy/paste of your files. Give that a try, and let me know if that will work for you.

---

### Post by ceaser_salad on 2008-10-09
Success! Thanks for your help! I'll have to write that command down somewhere:-)

---

### Post by Gannon8 on 2008-10-09
edit: oops, wrong thread :P

---

