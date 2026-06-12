---
title: "Unbuntu  doesnt recognise my 2nd Hard Drive"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by andilou on 2012-06-13
I hope that someone can help.The Bios accepts the additional HD but when I go into ubuntu Desktop there is no sign of the extra HD. I've run fdisk and it is there.
I am very new with ubuntu and not aware of what I may have to do to be able to use the HD.
Any help would be gratefully received.

---

### Post by idoitprone on 2012-06-13
> **andilou said:**
> I hope that someone can help.The Bios accepts the additional HD but when I go into ubuntu Desktop there is no sign of the extra HD. I've run fdisk and it is there.
I am very new with ubuntu and not aware of what I may have to do to be able to use the HD.
Any help would be gratefully received.


plugin your hdd
```
dmesg | tail
```

if it can read your hdd then it should show up

---

### Post by andilou on 2012-06-13
I've tried that and it does show as there but when I go to Home there is no sign of the extra Hard Drive.
What am I doing wrong.

---

### Post by idoitprone on 2012-06-13
> **andilou said:**
> I've tried that and it does show as there but when I go to Home there is no sign of the extra Hard Drive.
What am I doing wrong.

that command display the kernel log

If the kernel reads it then its fine

run

```
blkid
```

I can write a command to mount it

---

### Post by Jimmyfj on 2012-06-13
Your disk probably isn't mounted and your are most probably not the owner of the disk.

You do not write what kind of disk you are using, so I assume that the disk is a SATA disk. To change ownership of the disk at get it mounted try this command:

```
sudo chown -R user:user /dev/sda
```

user:user is in both cases your normal login-name.

You should now be able to see, and use the disk.

---

### Post by wilee-nilee on 2012-06-13
Have you added the HD to fstab, it will not be in the side panel of home then.

---

### Post by deadflowr on 2012-06-13
Did you set up the hard drive in anyway yet?
Did you allocate the unallocated disk space to an ext4 filesystem or did you just plug it into your system?
If not, simply either install or use the liveCD and run gparted and  set your partition tables and filesystems. We'll help with the process.

---

### Post by teward on 2012-06-13
is this a USB external hard drive?

---

### Post by andilou on 2012-06-28
sorry for the delay ,have been away for a few weeks.
No it is fixed internally and is a sata. Been in Bios and it is recognized there.
I did try doing the partitioning part thought I had done it right but being new at this game I am learning and not very well at the moment.
Any help is welcome.

---

### Post by Ms. Daisy on 2012-06-29
What will the second hard drive's function be? Do you want to install an operating system on it? Will it simply store backup data?  Whatever the purpose of the second drive is will tell you how to partition and format it. If we know what you'll use it for we can steer you in the right direction.
 
To access the second drive you need to understand "mount" in linux. I'm taking the liberty and assuming that you don't yet understand it.  Check this out:
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by andilou on 2012-07-20
Thank you for the help,yes I am new to all this in ubuntu and still cant get out of the habit of relying on the OS to do all the work.
I have now been able to locate the hidden HD and can now enjoy the use of the extra HD.
Sorry again for the delay as I am only able to respond at intervals.
Again thank you all ,perhaps one day Ill remember Im not using Windows.

---

