---
title: "2 installed operating systems, a way to view the other?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by anchor1te on 2008-07-23
Hello all,

I have XP and Hardy dual-boot.  Is there a way to view the other OS from the one that is running?  I have seen a lot of info about VirtualBox and VMWare, but don't want to re-install, just run the other.


Any help would rock!

---

### Post by ibutho on 2008-07-23
With Virtualbox and Vmware, you install an OS "inside" another OS. You cannot access operating systems already installed on separate partitions.

---

### Post by H3retic on 2008-07-23
> **anchor1te said:**
> I have XP and Hardy dual-boot.  Is there a way to view the other OS from the one that is running?  I have seen a lot of info about VirtualBox and VMWare, but don't want to re-install, just run the other.

Unfortunately, it can't be done as far as I know.  If both operating systems were run side by side they would both be significantly slower.

As you meantioned, certain people install Windows in virtualbox instead of rebooting.  

Sorry! :(

---

### Post by IanW on 2008-07-23
You should be able to view your XP partition from Ubuntu, just by mounting the drive.
To view Ubuntu from XP, you'll need a program/driver called [EXT2 IFS For Windows](http://www.fs-driver.org/).

These solutions are for data only, you will not be able to run programs on the other OS.

---

### Post by neurostu on 2008-07-23
No you cannot view a second OS from within the first...

If you want to run Windows in Ubuntu (or visa versa) the guest OS must be installed on a virtual machine running on the host os.

---

### Post by anchor1te on 2008-07-23
Oh well, was trying to get around the fact of booting out of Ubuntu into XP for work stuff.  Thanks!

---

