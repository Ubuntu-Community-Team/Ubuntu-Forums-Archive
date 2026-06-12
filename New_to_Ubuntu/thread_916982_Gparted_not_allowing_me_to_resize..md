---
title: "Gparted not allowing me to resize."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Anathallo on 2008-09-11
I need to resize a partition so I installed Gparted. However, on the partitions I need to resize it shows a key next to it, I dont know how to unlock it or whatever I need to do. Any ideas?

---

### Post by snowpine on 2008-09-11
Hi there, you can't resize a partition while it is mounted and in use. You may be able to right click the partition and choose Unmount, if it's not your / or /home partition. Otherwise, try booting from the Ubuntu Live CD and running GParted from there.

---

### Post by Anathallo on 2008-09-11
Ok, I am on the live cd and I can resize them. I want to resize one partition and move the other partition into the free space. How do I do this?

---

### Post by medya on 2008-09-11
snowpine is right, you need to unmount your partions , to do that simply type this in your terminal.

> sudo umount -a


it unmounts all the mounted partions (except root and home)

---

### Post by oilchangeguy on 2008-09-11
> **Anathallo said:**
> Ok, I am on the live cd and I can resize them. I want to resize one partition and move the other partition into the free space. How do I do this?

delete the un-needed partition. then resize the other partition to take over the unallocated space.

---

### Post by Anathallo on 2008-09-11
Yeah, I need to resize the root partition though :/ so I am on the live cd.

---

### Post by Anathallo on 2008-09-11
> **oilchangeguy said:**
> delete the un-needed partition. then resize the other partition to take over the unallocated space.

I need both of the partitions though. 
Ok, what I do is resize sda2 so it is smaller. 
This leaves "unallocated space"
I want to add this unallocated space onto sda1.

---

### Post by Idefix82 on 2008-09-11
Can't you "resize" sda1 and make it bigger now that you have free space?

---

### Post by Anathallo on 2008-09-11
I haven't applied it yet and it's not letting me move sda1 into the free space.
If I apply it will I be able to move sda1 into the free space?

---

### Post by Anathallo on 2008-09-11
Ok, I applied it and it just finished there. Now I have a shrunk partition -sda2- and a partition I am unable to do resize or move - sda2. In the middle of these is 14gb's of unallocated space which I need to merge with sda2. How can I do this? It is driving me round the bend :< 

P.S. The only thing it lets me do with the unallocated space is make it into a new partition.

---

### Post by Anathallo on 2008-09-11
bump :(

---

### Post by hubie on 2008-09-11
Can you describe your partition scheme as well as what you want to do?  GParted is very particular about the order things get done, so if you are trying to grow a partition near the front, you have to work in cooperation with all the other ones.  In other words, if you want to grow your first partition and it doesn't have room following it, you need to shrink and/or move the partitions to the right to make more free space.

---

