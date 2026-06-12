---
title: "Partition File System unknown"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Houmie on 2012-09-14
Hi After a successful installation of Ubuntu, I have the following error in GParted

[IMG]http://i.imgur.com/DP3yJ.png[/IMG]

When I right click on it and ask for information I get this:

[IMG]http://i.imgur.com/YX1nw.png[/IMG]

Any idea please?

---

### Post by mips on 2012-09-14
What was on that partition before you installed ubuntu?

---

### Post by Bucky Ball on 2012-09-14
Don't know. I would personally right click and delete it. It seems to be in an otherwise empty extended partition. 

I'm a bit confused at the fact you don't have a /swap partition.

---

### Post by oldfred on 2012-09-14
It is the swap partition.

If you click on encrypt /home when you install, it encrypts swap also. 

And gparted cannot see encrypted data, so it does not know what it is. If you look in fstab you will see it as swap with encryption.

---

### Post by Bucky Ball on 2012-09-14
> **oldfred said:**
> It is the swap partition.

If you click on encrypt /home when you install, it encrypts swap also. 

And gparted cannot see encrypted data, so it does not know what it is. If you look in fstab you will see it as swap with encryption.

Ah ha!

---

### Post by Bucky Ball on 2013-08-07
***Thread Closed.***

Aging and inactive for nearly a year.

---

