---
title: "Ubuntu Hard Disk size not updating"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by samubunto on 2012-01-06
Hey Guys,

I have ubuntu running on VM Ware server, and I changed my hard disk size, but it is not updating on the server. I increased the size to 200 GB from 120GB and the system still says 120GB. Do I need to do anything from ubuntu in order for it to take effect?

Thanks for your help.

---

### Post by sanderd17 on 2012-01-06
Take a look at Gparted, maybe the partition didn't stretch along with your harddisk.

---

### Post by lukeiamyourfather on 2012-01-06
> **sanderd17 said:**
> Take a look at Gparted, maybe the partition didn't stretch along with your harddisk.

Increasing the virtual disk size is equivalent to cloning a hard disk to a larger one. The partitions are still the same size as they were before. To take advantage of the extra space the partition will need to be extended or another partition will need to be created.

---

