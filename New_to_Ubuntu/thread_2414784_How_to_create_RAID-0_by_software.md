---
title: "How to create RAID-0 by software"
date: 2019-03-15
forum: New to Ubuntu
---

### Post by 123barbon04 on 2019-03-15
Hello Ubuntu Community, i have a question

I want to create a RAID-0 by software like in windows, but in Linux.

Help

---

### Post by TheFu on 2019-03-16
Use **mdadm**.

---

### Post by mastablasta on 2019-03-18
is raid0 even necessary these days with SSD available?

How to: [https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)

---

### Post by TheFu on 2019-03-18
> **mastablasta said:**
> is raid0 even necessary these days with SSD available?

How to: [https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)

I wouldn't use RAID0 except for temporary, working, storage, even on SSDs.  If you are doing 4K video editing, there certainly is a need for RAID0 on SSDs.  That's just one example. There most certainly are other good uses for RAID0.

But overnight, I'd get any of those working files backed up regardless of the storage.  Backups aren't optional, ever.

SSDs, at least the enterprise versions, have a fantastic longevity, durability, performance. But some applications need even more performance. Plus, lots of people are confused into thinking that SATA SSDs have performance near NVMe SSDs, which they don't.  For a desktop, SATA SSDs can flood the SATA bus, but NVMe can support up-to 10x more performance on the right hardware, with the right settings.  3000 Mbps vs 32000 Mbps. Big difference.

---

