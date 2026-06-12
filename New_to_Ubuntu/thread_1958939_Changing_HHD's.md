---
title: "Changing HHD's"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by KPKPW on 2012-04-15
Can you help me? I have a old (2005) desktop computer that died. Can I take out the hard drive and put it (as the only hard drive or 2ND) in my used 2006 IBM Think-Center M50? The IBM came with Linux installed and I have many Linux OS's I can reinstall. My old hard drive had Windows XP-Home on it and all my info. If you need more info on the computers I will dig after you tell me yes or no. Thanks for any help.   Wendell

---

### Post by jf812 on 2012-04-15
Considering the HDD is compatible with the newer system and it had enough spare HDD bays, i can't see why you couldn't. Also, as they are made around the same time, there is also a good chance that the HDD from the old desktop will be compatable with the IBM. Do you know whether the drive is IDE or SATA?

---

### Post by KPKPW on 2012-04-16
Both HHD's are SATA. What happens if I replace the current HHD with the one from the old dead computer and try to boot it?
Thanks "jf812" for trying to help me.  Wendell (KPKPW)

---

### Post by Grenage on 2012-04-16
Don't replace the Linux drive with the Windows Drive, just add it so that it runs alongside. That way you can access the data using the Linux install (assuming that the HD wasn't the fault).

---

### Post by audiomick on 2012-04-16
+1 letting it run alongside the linux system.

If you try and boot from the old windows drive, it is likely that it wont work. If the XP install is corrupted, it wont boot on anything.

If it was something else that died on the old computer, I believe you still wont be able to boot an XP install on different hardware. I believe XP had already started with that security nonsense that registers which hardware it is installed on, and demands a new registration if it detects too many hardware changes.

If you want to permanently mount the old drive, you will have to make changes to your fstab file, I think.

Assuming you have made the move to Ubuntu and do not need the XP install, I would suggest moving the data you need from the old drive onto (a data partition on) the current drive with the linux install, then re-format the old drive to a Linux file system to be used with the Linux install.

Here are some links to information about mounting, which is what you will have to do one way or another if you install the old drive into the Linux machine. The last one is relevant if you want to retain the partition(s) from the old XP install for whatever reason.

[https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by KPKPW on 2012-04-16
Thanks everyone, it'll take me some time to read and "try" to figure out all you have said.

---

### Post by Grenage on 2012-04-17
> **KPKPW said:**
> Thanks everyone, it'll take me some time to read and "try" to figure out all you have said.

Well as for the cloning side of things, gnu ddrescue can be installed (on a Debian/Ubuntu machine) using:

```
sudo apt-get install gddrescue
```

The basic syntax, and an example is:

```
ddrescue [options] infile outfile [logfile]
ddrescue /dev/sdb /dev/sdc /home/user/logfile
```

You can find a basic guide [here]("https://help.ubuntu.com/community/DataRecovery").  Do _not_ arbitrarily run commands, make sure that you know which disc (sda/sdb/sdc/etc) is which.  If in doubt, ask.

[Clonezilla]("http://clonezilla.org/") can be booted from a CD, has a GUI, and may be a more comfortable environment.

---

