---
title: "How to free disc space"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by unclejames on 2008-06-12
So, I've been successfully using Ubuntu Hardy Heron for a bit now, on my little Asus Eee pc.

After quite a few system updates, alarmingly my free space has dramatically dropped - from the two meg, ish, that was free after the installation, to, well nothing.

I notice it stored all the old Linux kernels, so I've gone through and deleted those, but what else doesn't delete itself after an update, and how can I get this working a little better? Ubuntu doesn't work very well with only a few meg free!

All help gratefully received.

---

### Post by drs305 on 2008-06-12
You can remove all the packages in /var/cache/apt/archives . These can be safely removed and restored later if necessary:
```
sudo apt-get clean
```

You can also empty trash folders. If you have recently deleted large files, they may still be on your system hogging space. To see where all your Trash files are located (including root's):
```
sudo find / -type d -iname Trash
```

You can then look at these directories and decide which of them you want to delete.
```
gksudo nautilus
```

---

### Post by kpkeerthi on 2008-06-12
[http://ubuntuforums.org/showthread.php?t=820804](http://ubuntuforums.org/showthread.php?t=820804)
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by decoherence on 2008-06-12
If cleaning the apt cache doesn't free up enough space,  Applications -> Accessories -> Disk Usage Analyzer can be helpful in finding big files and folders you forgot you had.

---

### Post by ukripper on 2008-06-12
This very good howto to clean up you junk files and orphaned files.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by unclejames on 2008-06-12
Thanks for all the replies. I now have 148 meg free. I must confess not to understanding where the 1.5G has gone that I used to have free, so I'll continue playing, but it's a great start.

---

### Post by unclejames on 2008-06-12
(Sorry - probably worthwhile mentioning that I store nothing on this machine - literally, the only downloads on this machine have been package updates. I deleted around six linux kernels, and even after running 'autoclean', I'm not convinced that the auto-update is deleting the rest of the update information.)

---

### Post by ukripper on 2008-06-12
> **unclejames said:**
> (Sorry - probably worthwhile mentioning that I store nothing on this machine - literally, the only downloads on this machine have been package updates. I deleted around six linux kernels, and even after running 'autoclean', I'm not convinced that the auto-update is deleting the rest of the update information.)

autoclean only cleans partial packages.

you need followign command:

```
sudo apt-get clean
```

this will delete all the downloaded packages in /var/cache/apt/archives directory

---

### Post by editrix on 2008-06-12
You might also want to check your .strigi folder, if you have Strigi installed. The files it creates are huge.

---

### Post by unclejames on 2008-06-12
sudo apt-get clean freed around 43 meg, which was the last update I reckon.

Still unsure where the other 1gig has come from; not sure whether it'll continue filling up. Ayway, now exactly 250M free.

---

### Post by Herman on 2008-06-12
Sometimes (mainly after restoring an operating system from a dd or partimage backup, the file system needs to be resized to fill up the entire partition.
This is easy to do with a Live CD, using the command, resize2fs, as explained in this link, [What to do if your file system doesn't fit your partition]("http://users.bigpond.net.au/hermanzone/p10.htm#What_to_do_if_your_file_system_doesnt").
Running resize2fsck won't hurt anything, and it might help. Chances are it will solve your problem if you can remember restoring you operating system from a partimage backup. If you have never done anything like that, then it probably won't do anything at all.

---

