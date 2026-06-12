---
title: "Change permission of external HDD"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by Jason_Sumner on 2014-07-14
I need to change the permissions of a lacie external hard drive for Mac. I've tried chown and nautilus but I have no idea how to use nautilus. Any ideas?

---

### Post by coffeecat on 2014-07-14
If this is a Lacie drive formatted with the journalled version of hfs+ for use with Apple hardware, you won't be able to change permissions and ownership from Ubuntu. Ubuntu - Linux generally - can mount hfs+ read-only. It cannot write to the filesystem, hence no changing of permissions.

Perhaps if you describe how you want to use this drive in Ubuntu, we can help with this.

---

### Post by Jason_Sumner on 2014-07-14
I need to get some information off of it. Old photos, videos, music, and some important documents. I try to access the files and it says I don't have permission to view files. The Mac that it was a backup of is dead.

---

### Post by coffeecat on 2014-07-14
Before I tell you the easy way to copy files off a journalled HFS+ we need to know whether this is a simple backup or whether this is a Time Machine backup. Time Machine backups introduce a whole new level of complexity if you don't have an Apple machine available. It's doable from Ubuntu but not straightforward.

---

### Post by Jason_Sumner on 2014-07-14
I'm 90% sure it's not a time machine backup. I also have access to an iMac if that helps.

---

### Post by Jason_Sumner on 2014-07-14
It's been a few years since I've needed these files. That's why I'm not 100% sure on wether or not it's a time machine backup.

---

### Post by coffeecat on 2014-07-14
OK - assuming it's not a Time Machine backup.

Click on the Lacie drive in the left pane of nautilus to mount it. Now ctrl-L to get the full path of the mountpoint of the Lacie drive. You'll see it highlighted in the address bar. It'll be something like /media/yourusername/Lacie. I'll use that below but change as necessary.

Now open a root-owned nautilus browser with this terminal command:

```
gksu nautilus /media/yourusername/Lacie
```

If you get an error about gksu not being installed, install it with:

```
sudo apt-get install gksu
```

And then try the previous command again, with the path to the mountpoint adjusted to what yours is. A root-owned nautilus window will open in the root of your Lacie filesystem, and you should be able to browse to wherever you want.

One tip. Because MacOS uses the same Unix permissions as Linux, and since your UID in the Mac files will be different from your Ubuntu UID, and since you are using a root-owned browser, I really can't be sure who your files will be owned by if you copy them to your Ubuntu home folder. In which case it is convenient to copy them to a Microsoft filesystem such as NTFS or FAT32 which will neatly "lose" the Unix permissions and ownership. FAT32 has a filesize limit of 4GB, so you may need to bear this in mind in case any of your files are that large.

If this does turn out to be a Time Machine backup this thread may help:

[http://ubuntuforums.org/showthread.php?t=2193764](http://ubuntuforums.org/showthread.php?t=2193764)

---

### Post by Jason_Sumner on 2014-07-14
Thanks for the help! I'll try this when I get home from work.

---

