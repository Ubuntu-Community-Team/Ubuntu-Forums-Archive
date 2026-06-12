---
title: "Not enough space on disk"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by peachka on 2012-06-19
I am using Ubuntu 12.04, which I'm running side by side with Windows 7.  When I try to download, I get an error message that says that I don't have enough space on my disk.  I tried to search for a solution, but I am very new to Ubuntu, and I haven't found an explanation that is clearly explained.

 I ran df --human-readable and this is what I got:

peachka@ubuntu:~$ df --human-readable
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   17G  135M 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           766M  868K  765M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  156K  1.9G   1% /run/shm
/dev/sda3       452G  122G  330G  27% /host

Obviously, I need more space on that first file, but I don't know how to get it there.  I downloaded Gparted, but I don't really know what to do with it.  Thanks in advance!

---

### Post by Elfy on 2012-06-19
You need to resize the disk or remove things from it.

Gparted will be no help as wubi does not use a partition.

[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

---

### Post by SilentMute on 2012-06-19
I ran into a similar problem and there's an application called Bleachbit that worked quite well at freeing up enough space to run smoothly ([http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/))

--

---

### Post by peachka on 2012-06-19
I can't do option 1 (Resize and duplicate the Wubi virtual Disk) because I'm no longer able to log into Windows.  I was having issues logging into Windows and decided to try Ubuntu.  I have not been able to log into Windows since.  I tried option 2, but I do not have enough space to create a live CD.

---

### Post by wilee-nilee on 2012-06-19
[COLOR=White].[/COLOR]

---

### Post by David Andersson on 2012-06-19
**If** you cannot resize the partition you may want save space by removing unnecessary or redundant files.

The Accessories>Disk Usage Analyzer can be used to find folders that contains lots of data. See if you can find downloaded movies, iso:s or other files that are not needed anymore.

This command in a terminal also lists folders, the ones with the most data shown last.
```
du -k | sort -n
```

You can remove cached deb-files from the system with this command
```
sudo apt-get autoclean
```

You can clear the cache in your web browser. For example, in Chromium go to Preferences>Under the hood>Clear Browsing Data, check Empty Cache only.

---

### Post by peachka on 2012-06-19
Is there a way to free up space on /dev/loop0 ?  I tried the other techniques, but this one remains full.  What could be on it that is 17 G?

---

### Post by wilee-nilee on 2012-06-19
You might want to consider where you are at.

You have a wubi install inside a broken windows, it is just a file in there.

It may be that we can get the windows running.

If it were me I would get to the wubi from a live cd, and save what you need, then fix or remove the windows, and do a actual partitioned install of ubuntu.

There are occasions when a user has no choice but a wubi, so I am not anti wubi per-say, but having it inside a broken windows is just not the best of situations.

Not to mention filing up a HD in general.

You want your horse in front of the cart not three miles behind. ;)

---

### Post by peachka on 2012-06-19
> **wilee-nilee said:**
> You might want to consider where you are at.

You have a wubi install inside a broken windows, it is just a file in there.

It may be that we can get the windows running.

If it were me I would get to the wubi from a live cd, and save what you need, then fix or remove the windows, and do a actual partitioned install of ubuntu.

There are occasions when a user has no choice but a wubi, so I am not anti wubi per-say, but having it inside a broken windows is just not the best of situations.

Not to mention filing up a HD in general.

You want your horse in front of the cart not three miles behind. ;)

Yep, I think this makes the most sense.  I'm attempting to make a live CD and then I'll do a clean install. Thank you!

---

### Post by wilee-nilee on 2012-06-19
> **peachka said:**
> Yep, I think this makes the most sense.  I'm attempting to make a live CD and then I'll do a clean install. Thank you!

Cool, could you mark the thread solved in the thread tools if you can. ;)

---

### Post by peachka on 2012-06-19
Everything is great now.  I just needed to ditch the broken Windows.  Thanks again.

---

