---
title: "How to Backup Ubuntu?"
date: 2009-06-25
forum: Programming Talk
---

### Post by huangyingw on 2009-06-25
Hello, 
    My current SeaGate 1TB hard disk seems to would break down in the near future. I will go to digit mall to ask the reseller to replace one for me. 
    While currently , my task is to as fully as possible back up my Ubuntu.
    I wonder how could I fully back my Ubuntu system?
    Does Ubuntu itself support this feature?
    Or, I would like to write such a shell. 
    For example, if I would get the system installation time, so, I could try to write a shell to find out all the files which are modified just later than the system installation time, of course, ignoring some paths. So, I could fully back up the configuration files.
    And next, I would need a shell to list out all of the packages that I have currently installed.
    While I don't know how could I get the system installation time, and how could I get the installed packages list.
    Could someone give me a guide?
    Or, if you always re-install system, how could you restore to the latest state quickly?

---

### Post by huangyingw on 2009-06-25
Sorry for this rash thread..
I am googling....And I will post what I find.

---

### Post by Mirge on 2009-06-25
I've heard good things about [http://clonezilla.org/](http://clonezilla.org/)...

---

### Post by aysiu on 2009-06-25
Here are various ways you can back up your system:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by jimv on 2009-06-25
Creating an image of your patitions with something like PartImage or Clonezilla is the best way, IMHO.  You can also use Gparted to copy a partition.

In fact, Gparted might be the easiest...simply do this:

Plug in whatever drive you want to back up to.
Boot from a LiveCD.
Open System > Administration > Partition Editor.
Right click on the partition you want to back up and click Copy (may need to unmount it first).
Switch to your other drive, right click on a chuck of unallocated (unpartitioned) space, and click Paste.
Click Apply.

---

