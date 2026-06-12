---
title: "Xubuntu 14.04 boots to blank screen"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by Andrew_Buczek on 2014-09-18
I'm running an HP Pavilion dv9700 laptop (32 bits), on which I set up a dual boot with Windows and Xubuntu 14.04. When I reach the page asking which OS to use, and I choose Ubuntu, it brings up the Xubuntu loading page, and then the screen goes blank. Recovery mode still works, of course, but I don't feel quite confident enough to start messing around with it.
I'm actually ready to run the laptop solely off of Xubuntu, I'd just like to transfer my files to a different computer before I reinstall.
The detailed disk usage reveals what seems like a fairly obvious problem, but I'm not sure how to go about fixing it.
```
Filesystem    Size    Used    Avail    Use%    Mounted on
/dev/sdb5      31G     29G        0    100%    /
none          4.0K       0     4.0K      0%    /sys/fs/cgroup
udev          1.5G    4.0K     1.5G      1%    /dev
tmpfs         303M    1.1M     302M      1%    /run
none          5.0M       0     5.0M      0%    /run/lock
none          1.5G       0     1.5G      0%    /run/shm
none          100M       0     100M      0%    /run/user
```
Running "clean" in the recovery menu yields:
```
"0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.



```

---

### Post by Rob Sayer on 2014-09-20
I don't see anything in the first bit that would cause that, and running clean is for removing old unused packages.  Not only will that not likely help either it's something you should be very careful about using because it can remove things you don't want removed.  But that shouldn't be a problem in a fresh install.

My first impulse would be to try booting with nomodeset.  Here's a guide:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jeffrey-cyr on 2015-01-16
Hello, I just ran into this exact problem with a different system. What is in common is that on both systems the hard drives are full. I think this is not leaving enough room X to make temp files somewhere.

To the point:

What worked for me was to remove a few gigs of stuff I didn't need and then I rebooted. I used SSH from another computer as only X is truly not working, but if you can boot to a shell or ftp or whatever lets you delete stuff (boot from USB or cd) I'm sure you'll be back up in moments.

Good luck.

---

