---
title: "[SOLVED] File system readability in Windows"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-10-05
Question: I recently converted from Ubuntu 8.04 to Debian Lenny.

Now these two systems are quite the same, since Ubuntu is based on Debian, but when I installed an ext2/3 installable file system in Windows XP & Vista, I could only read the Ubuntu partition, not the Debian partition. Why?

Does Ubuntu use ext2 and Debian ext3, and the installable ext2/3 file system not really support ext3???

---

### Post by louieb on 2008-10-05
I guess in windows your using either [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")  or [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") . I've had some some trouble in the past with the read only viewer.  If your using the read only viewer might what to try the the one with write support. 

Both should work with ext2 and ext3 file systems. 

Ubuntu and Debian  can use ext2, ext3 and few other file systems. If i remember right ext3 is the default for both.

---

### Post by WitchCraft on 2008-10-05
> **louieb said:**
> I guess in windows your using either [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")  or [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") . I've had some some trouble in the past with the read only viewer.  If your using the read only viewer might what to try the the one with write support. 

Both should work with ext2 and ext3 file systems. 

Ubuntu and Debian  can use ext2, ext3 and few other file systems. If i remember right ext3 is the default for both.

I'm using
Ext2 IFS Win w/write support
and [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

I think I'll try chysocome


Edit: Ah, now I checked and there is a new version of [http://ext2fsd.sourceforge.net/projects/projects.htm](http://ext2fsd.sourceforge.net/projects/projects.htm) from May 2008.
Now it works, I guess it was a bug:

> 
Features  implemented or bugs fixed:
    1, ext3 journal check and replay implemented. If the journal is
        not empty ext2fsd will replay the journal and make the file
        system consistent as an ext2 file system.

    2, flexible-inode-size supported. recent Linux are using 256-byte
        inode that fails 0.45 and before to show all the files.


Problem solved.

---

