---
title: "raid?"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by squakie on 2014-01-02
What does one do if they want to use RAID in Ubuntu?  Is it best to have a smaller drive with just the OS, then the larger data drives in RAID?  Can /home be on the RAID drives?

---

### Post by CharlesA on 2014-01-02
I've always used the RAID (hardware or software) for data with a separate drive for the OS.

You can run RAID on the OS drive itself but I think you need to use the alternate CD to enable mdadm and whatnot.

---

### Post by squakie on 2014-01-02
My background tells me that if I use RAID on the OS drive, it should be shadowed only - not spanned as well.  Does that still hold true?

---

### Post by CharlesA on 2014-01-02
> **squakie said:**
> My background tells me that if I use RAID on the OS drive, it should be shadowed only - not spanned as well.  Does that still hold true?

Depends on what RAID level you want to use. You could stripe it with a RAID0, but that offers no redundancy at all.

---

### Post by squakie on 2014-01-02
Going to have to think on it.  I was hoping I could shadow the system drive, then stripe and shadow the others as I can afford to add them.  System would be the first, with a second for /home I guess (want data, etc., to go there).

Thanks.

---

### Post by andyfied on 2014-01-02
Heya squakie

A lot of what you decide will be based on what you want to do. I have my OS on one drive and back it up to a 4 disk RAID 5 where I keep a huge amount of my data and backups from my laptop too.

If you want redundancy then RAID 1 (mirrored) on your OS should be your best bet. You can simlink the contents of /home so they live on a second data RAID at some point. If you want your OS to be quicker then RAID 0 (striped) will be fine. Whatever you do, back it all up!

Good luck and have fun!

---

### Post by CharlesA on 2014-01-02
> **squakie said:**
> Going to have to think on it.  I was hoping I could shadow the system drive, then stripe and shadow the others as I can afford to add them.  System would be the first, with a second for /home I guess (want data, etc., to go there).

Thanks.

You could do a reshape with mdadm to change the RAID level and type, but RAID is no substitute for backups. :)

---

