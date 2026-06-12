---
title: "How much swap is installed by default on Lubuntu?"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by Androzani1 on 2012-10-28
Thread title says it all.

---

### Post by ajgreeny on 2012-10-28
If you let the installer partition your disk automatically I think it will make a swap partition equal to your ram.

I may be wrong about that as I always manually partition when installing, and make a separate /home partition.  I recommend you do the same, if you're prepared to try, as it makes it much simpler if you ever need to reinstall, which when I first started using Ubuntu in 2005, was something I did a few times having messed up the system trying things out which I ought not to have done.

Actually, it made me learn a lot quicker when I made those mistakes, so perhaps it is not something to fear too much.  Just make sure you have good backups of all your personal files in /home.

---

### Post by TenPlus1 on 2012-10-28
As far as I'm aware this depends on how much physical memory you have installed on your computer...  Generally enough for a laptop to hybernate to the swap file plus a little extra...  Although if you have 2gb or more of memory I tend to disable swap completely...

---

### Post by Androzani1 on 2012-10-29
> **ajgreeny said:**
> If you let the installer partition your disk automatically I think it will make a swap partition equal to your ram.

I may be wrong about that as I always manually partition when installing, and make a separate /home partition.  I recommend you do the same, if you're prepared to try, as it makes it much simpler if you ever need to reinstall, which when I first started using Ubuntu in 2005, was something I did a few times having messed up the system trying things out which I ought not to have done.

Actually, it made me learn a lot quicker when I made those mistakes, so perhaps it is not something to fear too much.  Just make sure you have good backups of all your personal files in /home.

I'll have a backup of my files, but I think I'll just let the installer do its thing.

---

### Post by kurt18947 on 2012-10-29
> **TenPlus1 said:**
> As far as I'm aware this depends on how much physical memory you have installed on your computer...  Generally enough for a laptop to hybernate to the swap file plus a little extra...  Although if you have 2gb or more of memory I tend to disable swap completely...

Or, if you don't hibernate (suspend to disk) but are short on RAM, you can create a swap **file** rather than a swap partition.  For someone limited to 4 partitions and dual booting with Windows, this can be useful.

---

