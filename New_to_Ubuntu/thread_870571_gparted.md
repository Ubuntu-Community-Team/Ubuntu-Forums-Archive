---
title: "gparted"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by scrimple101 on 2008-07-25
I looked at my partitions through Gparted and noticed that there is a unallocated partition of 4.61 MiB. I duel boot with WinXP and was wondering if this partition is a rootkit. I have tried to delete if but have been unable with Gparted. Any idea what it is and if it is malicious how can i get rid of it? Regards, Robert.

---

### Post by ConMan318 on 2008-07-25
You said it's unallocated, so what do you mean you tried deleting it?  Unallocated means there's nothing there, so of course you can't delete it.

You should resize one of your partitions to use that space.  If you want to do that with your Ubuntu partition you will need the Gparted liveCD so you can resize without your Ubuntu partition being mounted (an active partition can't be resized).  The Gparted liveCD is very easy to rearrange your partitions with.

---

### Post by drowner on 2008-07-25
What happens when you try to delete it? Where is it located?

---

### Post by erfahren on 2008-07-26
> **scrimple101 said:**
> I looked at my partitions through Gparted and noticed that there is a unallocated partition of 4.61 MiB. I duel boot with WinXP and was wondering if this partition is a rootkit. I have tried to delete if but have been unable with Gparted. Any idea what it is and if it is malicious how can i get rid of it? Regards, Robert.
do you have an extended partition? that's normal with an extended partition

---

### Post by kansasnoob on 2008-07-26
> **ConMan318 said:**
> You said it's unallocated, so what do you mean you tried deleting it?  Unallocated means there's nothing there, so of course you can't delete it.

You should resize one of your partitions to use that space.  If you want to do that with your Ubuntu partition you will need the Gparted liveCD so you can resize without your Ubuntu partition being mounted (an active partition can't be resized).  The Gparted liveCD is very easy to rearrange your partitions with.

Exactly right! It's not a rootkit! It's just leftover space from a poorly done partitioning.

---

### Post by scrimple101 on 2008-07-26
Thanks everyone for your help, i'll give the gparted disk a go.

---

