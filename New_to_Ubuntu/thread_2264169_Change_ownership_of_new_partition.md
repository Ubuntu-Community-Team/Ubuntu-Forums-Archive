---
title: "Change ownership of new partition"
date: 2015-02-05
forum: New to Ubuntu
---

### Post by David4321 on 2015-02-05
I just created 2 new ext4 partitions using gparted on my primary hard drive. System is running Lubuntu current version. Cannot write to partitions.

I have seen many threads on this topic, and cannot get any of the solutions to work yet.

I hate having to do such tasks in terminal - is there any other way? Is there a way to recreate the partitions with correct ownership as workaround?

If neither, please help with correct terminal commands. Please, step by step and very complete and simple as possible - terminal is new to me.

Thanks!

---

### Post by bab1 on 2015-02-05
> **David4321 said:**
> I just created 2 new ext4 partitions using gparted on my primary hard drive. System is running Lubuntu current version. Cannot write to partitions.

I have seen many threads on this topic, and cannot get any of the solutions to work yet.

I hate having to do such tasks in terminal - is there any other way? Is there a way to recreate the partitions with correct ownership as workaround?

If neither, please help with correct terminal commands. Please, step by step and very complete and simple as possible - terminal is new to me.

Thanks!
Partitions don't have permissions or ownership.  The file system has permissions and ownership.  What directories do you need access to?  

The terminal is the easiest way of solving the problem.  Post the output of ```
df -h
```...this shows that various mounted partitions and their mountpoints.

Then we can assist you further.

---

### Post by yancek on 2015-02-06
It would also be useful to know the filesystem type on the new partitions, if they are Linux or other.

---

### Post by bab1 on 2015-02-06
> **yancek said:**
> It would also be useful to know the filesystem type on the new partitions, if they are Linux or other.
That was described in the first sentence of the OP's first post.  > I just created 2 new ext4 partitions using gparted on my primary hard drive.

---

