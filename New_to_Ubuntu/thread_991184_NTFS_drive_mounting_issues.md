---
title: "NTFS drive mounting issues"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by vergeh on 2008-11-23
I have a couple questions. First, is there any way to have ubuntu mount my NTFS drives on boot? 

Second, my XP installation has problems shutting down. As such, half the time my drives are unmountable because they're marked in-use by the improperly shut-down Windows. If I choose to force mount the drives, what are the associated risks involved...and how do I go about doing it?

---

### Post by marshall.robert on 2008-11-23
this involves getting a little dirty with the terminal...

first you will want to type this

```

sudo gedit /ect/fstab

```

then 

```

sudo mkdir /media/win

```

then add a line similar to this, but change /dev/sda2 to your drive

```

# Entry for /dev/sda2 :
/dev/sda2 /media/win ntfs-3g defaults,force

```

that should do it, see how that works.

I have found this is the best way to sort this kind of problem, it means you dont have to do anything afterwards, there are other methods using an ntfs config program but it doesnt sort your problem of shutting down improperly

---

### Post by Michael.Godawski on 2008-11-23
> First, is there any way to have ubuntu mount my NTFS drives on boot? 
Yes. But you need some additional applications. 
See here:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
[*][https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
[/LIST]

---

### Post by diablo75 on 2008-11-23
I don't think I had to do anything to mount an NTFS drive on 8.10 other than opening my places menu and clicking on it.  But you check to see if you have the ntfs config utility (search for "ntfs" in Applications>Add/Remove) needs to be installed.

As for the errors you are encountering, the key is to make sure you shut windows down properly before attempting to mount an NTFS drive with Ubuntu.  Sometimes it takes booting into windows, mounting the drive, and shutting Windows down twice in a row to knock the kinks out.  I wouldn't recommend force mounting a drive that has an in-use status.  You could really screw your data up big time.

---

### Post by drs305 on 2008-11-23
the simplest way, install ntfs-config (and may as well ntfsprogs):
```
sudo apt-get install ntfs-config ntfsprogs
```

Run ntfs-config from System Tools, NTFS Configuration Tool.
Tick the enable write, put in a mountpoint (which will be in /media) and the tool will make the appropriate entry in fstab.

Note: ntfsprogs contains 'ntfsfix', which can remedy unclean ntfs shutdowns; the best method is still to go back to windows and accomplish a clean shutdown from there.

---

### Post by vergeh on 2008-11-26
I should have been more clear in my OP, but I can mount my NTFS drive just fine by clicking on it in the 'places' menu, unless it has not shut down properly.

The improper shutdowns are not anything I can fix. I have a [bad capacitor]("http://en.wikipedia.org/wiki/Capacitor_plague"), and so my computer tends to shut down without warning. Funnily enough, it does this more in Windows than in Linux.

Marshall Robert's solution seems the most viable, but how do I tell which sda# my windows drive is? Also, can forcing a mount mess up my drives?

---

