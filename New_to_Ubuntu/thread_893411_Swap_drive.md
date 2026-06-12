---
title: "Swap drive"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by alex199020 on 2008-08-18
Im going to be re-installing ubuntu in the next day or to but will be partitioning the drive its on so that i can access stuff like music from windows aswell. I noticed that when i used the guided methoed (not manual) for partitioning on my first install it made a swap partition. 
What is the purpose of this and should i make one when i install?
Thanks! (and sorry if theres already a thread, i tried search but couldn't find the answer)

---

### Post by finer recliner on 2008-08-18
yes, please allocate swap space.

swap space is just hard drive space that is used as virtual memory in case you run out of real physical memory. it is usually recommended to make your swap space about twice as large as the size of your physical RAM (example: if you have 1GB of RAM, then allocate 2GB of swap space)

using swap space is slow, so the OS will only use it when necessary.

---

### Post by decoherence on 2008-08-18
The swap partition is used for virtual memory -- it is equivalent to the pagefile in Windows, it gets used when you run out of physical RAM.

Yes, you should make one if it isn't done automatically.

---

### Post by billgoldberg on 2008-08-18
Yes, I suggest you use at least 1gb of ram, maybe even more. (I use 2gb).

---

### Post by alex199020 on 2008-08-18
Right, makes sense. So if im running 2gb of ram i should use 4gb of swap?
Thanks for the speedy replys.

---

### Post by porchrat on 2008-08-18
that and you need swap if you ever want the machine to hibernate as it needs a space on the drive to move the contents of the RAM to.

Not that I've ever been able to successfully hibernate my hardy install, regardless of swap.

---

### Post by finer recliner on 2008-08-18
> **alex199020 said:**
> Right, makes sense. So if im running 2gb of ram i should use 4gb of swap?
Thanks for the speedy replys.

4GB will be plenty. you could probably allocate 2GB and be fine too (unless you know you're going to be doing some very memory-intensive tasks like video editing)

---

### Post by alex199020 on 2008-08-18
Excellent. Thanks alot for the help :)

---

