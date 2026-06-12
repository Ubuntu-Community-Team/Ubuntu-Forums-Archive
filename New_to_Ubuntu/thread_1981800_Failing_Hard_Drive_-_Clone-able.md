---
title: "Failing Hard Drive - Clone-able?"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Shadius on 2012-05-17
Hey all,

I'm running Ubuntu and Windows XP on two separate hard drives, and I recently logged into my Windows and got a message that my Windows hard drive is failing. Since I still need Windows and it never came with a separate install CD so I can't re-install it to another hard drive, I was wondering if I can clone my Windows from the failing hard drive to a better hard drive? Is this the only way to save my Windows XP? What can I do? 

Thanks for any help.

---

### Post by westie457 on 2012-05-17
Yes it can be cloned in a number of ways.
Some options for you to consider:-

Clonezilla from here
[http://clonezilla.org/](http://clonezilla.org/)

Or the dd command ```
man dd
``` for more information

Clonezilla might be able to clone to a smaller hard drive, cannot say for sure as have never used it.

The dd command must use a drive of at least the same capacity as the one being copied.

---

### Post by Shadius on 2012-05-17
> **westie457 said:**
> Yes it can be cloned in a number of ways.
Some options for you to consider:-

Clonezilla from here
[http://clonezilla.org/](http://clonezilla.org/)

Or the dd command ```
man dd
``` for more information

Clonezilla might be able to clone to a smaller hard drive, cannot say for sure as have never used it.

The dd command must use a drive of at least the same capacity as the one being copied.

Great. Thank you. When cloning the bad drive, the errors won't get cloned as well, right? Like the bad sectors?

---

### Post by westie457 on 2012-05-17
> **Shadius said:**
> Great. Thank you. When cloning the bad drive, the errors won't get cloned as well, right? Like the bad sectors?

dd does a byte for byte copy of the data on the disk platters. When it encounters a bad sector or sectors that cannot be read they are skipped. Getting technical now and having a bit of a guess when the heads on the original drive move the ones on the receiving drive move a corresponding amount. For example drive A skips 6 sectors drive B will skip those same sectors as well. The hard drive will be able to use those missed sectors later.

Now I am confused :lolflag:

---

### Post by Shadius on 2012-05-17
> **westie457 said:**
> dd does a byte for byte copy of the data on the disk platters. When it encounters a bad sector or sectors that cannot be read they are skipped. Getting technical now and having a bit of a guess when the heads on the original drive move the ones on the receiving drive move a corresponding amount. For example drive A skips 6 sectors drive B will skip those same sectors as well. The hard drive will be able to use those missed sectors later.

Now I am confused :lolflag:

LOL Thanks for that explanation. As long as the errors don't get cloned as well, and I can save my Windows XP.

---

