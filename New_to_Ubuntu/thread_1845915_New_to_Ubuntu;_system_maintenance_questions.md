---
title: "New to Ubuntu; system maintenance questions?"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-09-18
I am new to Ubuntu, before i had Windows XP. I would like to know if there is an Ubuntu equivalent to Windows' Disk Defragmenter and Disk Cleanup, or if there are better ones. 
Also, are there any cache things to clear after you delete large files? I selected the "Delete" option, to permanently delete them, but are there any left-over cache files that will slow it down? On a related note, are there any other cache files that need to be cleared occasionally?

---

### Post by wildmanne39 on 2011-09-18
Hi, you really do not need to worry about all of that ubuntu is nothing like windows.

You can delete your browser history on a regular basis.
Thank you

---

### Post by Megaptera on 2011-09-18
Have a read of this thread too [http://ubuntuforums.org/showthread.php?t=1845164](http://ubuntuforums.org/showthread.php?t=1845164)

---

### Post by oldos2er on 2011-09-18
If you're using 'permanently delete' it bypasses ~/.local/share/Trash, so there is nothing further to do.

---

### Post by VanR on 2011-09-18
I use Ubuntu Tweak to do what little maintenance Ubuntu requires. (cleaning cache, package config, etc.

---

### Post by I2k4 on 2011-09-19
Not sure what "solved" the question, but you should look into "Bleachbit" which is fine cleaner.

---

### Post by MG&amp;TL on 2011-09-19
```
sudo apt-get autoremove
```

also appears to be sometimes necessary.

---

### Post by TenPlus1 on 2011-09-19
No need to defrag linux partitions but you could use a program called 'Bleachbit' which lets you delete all sorts of temp files and tidy up your system...  You can find it in the software-centre or synaptic package manager...

---

### Post by walt.smith1960 on 2011-09-19
One big difference between Windows (NTFS) and the file systems used by Linux (ext2,3,4) is that the ext. file systems are not nearly as prone to fragmentation as NTFS.  I've read ext *may* become fragmented but not nearly as bad.  Combine the fact that ext file systems don't fragment easily with many desktop users reinstalling every LTS release (18 months) or sooner file fragmentation doesn't seem like a real concern.  I'm pretty sure tmp files get deleted with logging out but the above posters mentioned maintenance tools if you feel the need.  The biggest maintenance saving with Linux is NO REGISTRY.  The bottom line is that Linux doesn't require the maintenance of Windows.

If a new installer took the time to learn how to set up a separate /home partition reinstalling becomes pretty simple.  User data, Program data and many settings are stored in the /home/user folder.  There's no registry containing personal or program settings so if the O.S. partition is corrupted or deleted, user data and most settings are still intact in the separate /home partition.

---

### Post by zhogan85 on 2011-09-19
I was just looking into this myself. This post details several preferred methods.

[http://ubuntuforums.org/showthread.php?t=1722616](http://ubuntuforums.org/showthread.php?t=1722616)

sudo apt-get autoremove
sudo apt-get autoclean

Both seem to be the method of choice, on average, along with BleachBit.

[This ]("https://help.ubuntu.com/community/AptGet/Howto")will also tell you more about the above commands (and others), if you're interested.

---

### Post by Paqman on 2011-09-19
> **walt.smith1960 said:**
> I've read ext *may* become fragmented but not nearly as bad.

Yep, you can get fragmentation on an EXT filesystem. All you need to do is fill it up too much (ie: over 90%) and it'll start fragmenting away quite nicely. That's why commands like those given above that clean out caches can be of use if your system is getting close to full. However, until it reaches that point there's no significant advantage to having a cleanout.

Getting rid of old kernels is a really fast way to free up lots of space. You really only need the latest (and a spare if you're uber paranoid), and the old ones take up over 100MB each. Just open up one of the more geeky package managers such as Synaptic and filter for installed packages starting "linux-image".

---

