---
title: "Installing ubuntu with 5 partitions"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by O-pos on 2008-05-09
Hello,

I would like to create following partitions on my new laptop:

windows
personal files and documents (part of an extended partition)
/home (part of an extended partition)
root
swap

how can I create the extended partion with ubuntu installer?

---

### Post by overdrank on 2008-05-09
> **O-pos said:**
> Hello,

I would like to create following partitions on my new laptop:

windows
personal files and documents (part of an extended partition)
/home (part of an extended partition)
root
swap

how can I create the extended partion with ubuntu installer?

HI and I installed Hardy on my son's system yesterday and notice that was not a option on the installer. But you can use gparted on the live cd to create the extended partition and then install.

---

### Post by dracker on 2008-05-09
In the installer you can edit the partitions selecting "manual configuration" in the "select where you want to install ubuntu" page, you can delete and create partitions, also you can format them and select where they will be mounted.
Anyway, I've never used this to change the partition table, I use gparted as it has been said before since it's right there on the live Cd.


PS: This is one of my first post to help somebody :oops: if I made a mistake please forgive me

---

