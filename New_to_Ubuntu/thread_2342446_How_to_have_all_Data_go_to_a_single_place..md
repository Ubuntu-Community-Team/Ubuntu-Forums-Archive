---
title: "How to have all Data go to a single place."
date: 2016-11-06
forum: New to Ubuntu
---

### Post by reb682 on 2016-11-06
I have Ubuntu 16.10 (64), Windows8, and Kubuntu (it says 17.04 but I don't know how I got that). The data is duplicated on the different OS's. How can I delete the data and have it all in one place while using the different OS's
I was told to do that on this forum earlier but do not know how to send it all to the same place. I do not mean delete. How to send it all to one place.
Thank you for any help.

---

### Post by Bucky Ball on 2016-11-06
It would help if you could let us see what you already have on the drive. One drive? More? Do you have /home directories in your / partitions on your *buntu installs or are you using a /home partition? Do you have one large data partition for either OS anywhere that is NOT on an OS partition?

The Win part I can't help you with linking to that partition, but Ubuntu, yes. You can use symlinks. 

If you create a large /data partition (call it what you want) and then create folders in there to match what you are using, e.g. /Videos, /Documents, etc. Plop your existing personal data to the appropriate folder on the /data partition.

Now, once you know it is safely there on the /data partition and NOT on the OS partitions, delete the folders in the /home directory (except hidden files and folders and 'lost & found'). Replace them with symlinks. 

They work like this. If your documents, say, are in /data/documents, then you would create a symlink in your /home/user directory like this, replacing the details with the right ones for you:

```
ln -s 'location to link to' 'name of symlink'
```

For example:
```
ln -s /media/data/Documents /home/reb682/Documents
```

This: '/media/data/Documents' is the /data partition. This: '/home/reb682/Documents' creates a symlink by that name in your /home directory inside you / partition. There is NO data in a symlink (well, it is a few Kbs). It is just a link to somewhere else. 

...  is your /data partition and it is mounted at /media/data. More details on [symlinks here]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979").

Once you get this set up correctly all OSs will be accessing the same data from the same place, you only need to backup the /data partition, and it doesn't matter whether that partition is NTFS or EXT*. No redundancy. I have three installs at the moment and they all use the data from one data partition. If I change something in one install and boot into another, exactly the same document, changes all there, just keep working. :)

Hope that helps. Any questions, fire away. ;)

PS: Just a point. If you have one Ubuntu install with a /swap and a /home partition, no need to create more. The second (or third or fourth) Ubuntu install (regardless of flavour) can use the existing /home and /swap partitions as they two OSs can't be booted at the same time so all good.

---

