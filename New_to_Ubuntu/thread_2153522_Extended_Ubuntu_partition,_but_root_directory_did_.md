---
title: "Extended Ubuntu partition, but root directory did not change size"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by Tha_Libster on 2013-06-11
SOLVED: The filesystem hadn't been extended properly, which was likely a result of me having extended the partition from windows. A simple "resize2fs -p /dev/sda7" after booting from a liveUSB did the trick.

I extended the size of my Ubuntu partition from Windows (dual boot), but the extra space seems to have gone to directories other than root (/run/shm and udev). How do I allocate the space to the root directory instead? Here is the result of df -h:

```
/dev/sda7             3.7G  3.1G  428M  89% /
udev                  3.9G  4.0K  3.9G   1% /dev
tmpfs                 1.6G  884K  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.9G  156K  3.9G   1% /run/shm
/dev/sda1             296M   44M  253M  15% /boot/efi
/home/aaron/.Private  3.7G  3.2G  416M  89% /home/aaron
```

EDIT: I had omitted the last line of the result of df -h because I thought it was just restating the size of sda7, but now I realize that it must be contributing separately to the total size of 20 GB. What is it? Is it just a backup for my root directory or something?

---

### Post by dino99 on 2013-06-11
An "Extended" partition is like a container where you set "logical" partition(s) inside.

boot on a livecd/usb, then load gparted to resize the / partition (usually set around 12/15 Gb)

---

### Post by Tha_Libster on 2013-06-11
I get the following when I load GParted (though not from liveUSB). I'm not sure how to do what you suggest from what it's telling me. It also says that 18.9 GB is being used on sda7, which I'm sure is false, and contradicts the df -h log I posted earlier.

[IMG]http://i.imgur.com/77EeJtT.png[/IMG]

---

### Post by oldfred on 2013-06-11
I see an efi partition. This must then be an UEFI system and then it uses gpt partitioning. With gpt partitioning you do not have primary, extended nor logical partitions like the 30 year old MBR(msdos) partitioning use previously.

Not sure if your encryption of /home changes how things are reported or not?

Have you emptied trash?

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

---

### Post by Tha_Libster on 2013-06-19
The system is indeed UEFI, and the trash is empty. 

So the .Private directory is a result of me encrypting the HD? It only contains about 600 MB of data, but according to df -h it has 3.7 GB allocated.

Is there an easy way for me to reallocate memory from this system to the root? Or from /run/shm? (3.9GB there seems excessive, but I wouldn't know) TBH I would be okay with getting rid of the encryption to remove this allocation entirely, if such a thing is possible.

EDIT: maybe this helps?

[IMG]http://i.imgur.com/TSzdDE7.png[/IMG]

---

### Post by oldfred on 2013-06-19
I still assume your encryption must be part of the issue. And I have never used encryption to know details.

My system monitor and df -h essentially agree (within 1GB). But some tools like Disk Usage Analyzer do not match as my linked folders from other partitions get added to / as if they were one large partition.

---

