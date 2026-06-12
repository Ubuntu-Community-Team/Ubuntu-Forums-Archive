---
title: "dual booting ubuntu and windows 7"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by XD Aequitas 40 on 2012-10-04
Hello,

I have bought a laptop that appears to already be partitioned.  So my only question is, am I good to go as far as installing Ubuntu on the logical drive?  I have never dual booted before so I thought I would ask for advice first.  

Thanks!

---

### Post by Mark Phelps on 2012-10-04
That drive is formatted NTFS -- MS Windows filesystem.  The only way you can install TO that drive is using Wubi -- which will install from INSIDE MS Windows.  Unless you only intend to do this to try out Ubuntu for a short term, I would recommend against using Wubi.

Since you already have the 4-partition limit, installing Ubuntu to its own partition(s) is not going to be a simple process.  You will first have to decide WHICH existing partition to remove in order to then create a new one for Ubuntu.

You will also then have to shrink the Win7 OS partition to make room.  Use ONLY the Win7 OS Disk Management tool to do this.  Do NOT use the Ubuntu installer with the slider option -- as that risks corrupting the Win7 OS partition and rendering Win7 unbootable as a result.

And finally, once you have shrunk the Win7 OS parition, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You may need that later to restore the Win7 boot loader should that become corrupted during the Ubuntu installation.

---

### Post by XD Aequitas 40 on 2012-10-04
Looks like im going to have my hands full. At least I know where to start though.  Thanks for the advice!

---

### Post by DuckHook on 2012-10-04
...and for Pete's sake, *back up* all of your critical data first so that a mishandled repartitioning doesn't nuke your life. I know it's elementary, but I've lost count of the grief caused by failure to take this simple precaution. Let us know how it goes.

---

