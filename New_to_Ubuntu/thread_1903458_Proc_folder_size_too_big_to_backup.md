---
title: "Proc folder size too big to backup?"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-01-02
Am using SpiderOak to backup my complete Ubuntu system using 100G. On checking the /proc folder properties, it reports the size is 1.28TB!. How can this be when I am only using 9.4G of my drive's total capacity of 450G?  Any ideas?

---

### Post by fdrake on 2012-01-02
the proc folder is a set of virtual filesystems and devices:
see here for an explanation  [http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379](http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379)
> 
The /proc directory is not a normal directory. If you were to boot from a boot cd and look at that directory on your hard drive you would see it as being empty. When you look at it under your normal running system it can be quite large. However it doesn't seem to be using any hard disk space. This is because it is a virtual file system. In other words it is just a means of easily peeking and poking at the guts of the linux system through a file and directory type interface. When you look at a file in the /proc directory you are looking directly at a range of memory in the linux kernel and seeing what it can see. In fact many utility programs get their information from this /proc directory. By knowing where to look you can get the same and more information just by reading the appropriate file in the /proc directory.


---

### Post by Lars Noodén on 2012-01-02
Don't back up /proc, /dev, /run or /sys.  [hier](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html) goes into details, but it is used for communication with the kernel.  If you look at the output from [mount](http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html), you can see that it is not a regular file system.

You can also probably get away with skipping /tmp and /var/tmp, too.

---

### Post by sisco311 on 2012-01-02
/proc and /sys are virtual filesystems so you don't have to backup them. The content of /dev is created and deleted dinamicaly by udev so you don't have to back it up. The lost+found directories must be also skipped since they are partition-specific.

For some pointers, see:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
The Arch Wiki also provides some good information:
[https://wiki.archlinux.org/index.php/Backup](https://wiki.archlinux.org/index.php/Backup)

---

