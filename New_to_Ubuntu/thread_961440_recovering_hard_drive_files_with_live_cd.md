---
title: "recovering hard drive files with live cd"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by dtregembo on 2008-10-28
I read a response to a guy trying to recover his files from his windows system but the response did not say how. I am an ignorant newbie who needs to be bottle fed at times.

I have a laptop I installed ubuntu 8.04 on and it has decided that the laptop screen is closed and needs to go to sleep, so I cannot transfer the files I stored there while putting ubuntu on my desktop. ugh!

I do have a usb stick. I loaded the live cd figuring I could use it to transfer the files from the hard drive to the stick (seemed logical at the time), but it will not mount the hard drive in order to transfer them. I tried using the system settings disk management to get it to enable that partition without luck. It only wants to read the files system the live cd setup.

If you could tell me exactly how to go about this I would greatly appreciate it. I have removed microsoft from my computers, but only know enough about computers and gnu/linux to be dangerous! LOL I am smart enough to know I want to be FREE :-)

---

### Post by aeiah on 2008-10-28
it should auto mount any filesystems it finds on your laptop, so its a bit strange. incidentally, does your laptop think the lid is closed even when booting into safe mode / recovery mode? if not, try using that and either copy files to your usb drive from the commandline or by using the startx command to start the gui.

if you still want to use the livecd, perhaps you need to manually mount your partitions. see what devices are available to you in the livecd by typing ```

ls /dev/sd*
```
and / or
```

ls /dev/hd*
```
and mounting what you find by using ```

mkdir tempdir
mount /dev/sda1 tempdir
```

replace the names with appropriate ones

---

### Post by dtregembo on 2008-10-28
Thanks very much for the response!

I think the problem is the button on my laptop that tells it the lid is closed. It does it in recovery mode, safe mode, etc. The only time it will not do it is with the live cd, but then the live cd will not mount sda1. If I do start the recovery mode I can go into the terminal and run commands there without it sleeping.

With your help I was able to access the hard drive that way, and I successfully mounted the stick using your mkdir tempdir trick! I love linux - it is definitely a learning process!

I was able to find and access all my files on the hard drive, so now I just need to copy them to the stick and transfer them to my desktop. Learning curve there too!

Thanks so much for the help and the responses - I got some private ones too!

I love the community in Linux and look forward to becoming intelligent enough to be able to contribute too! Keep up the great work you guys are doing and the contributions you make to our freedom!

---

