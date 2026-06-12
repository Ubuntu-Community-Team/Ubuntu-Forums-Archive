---
title: "Ubuntu VM Performance."
date: 2013-08-15
forum: New to Ubuntu
---

### Post by ConcreteDonkey on 2013-08-15
I'm currently using VMwares workstation, all has been going fine even with the previous builds but as unity started getting added the experience is terrible. Not only that but it forces the VM in to a ridiculously high resolution causing a lot of scrolling on my part an.

Does anyone else have the same problem and would hopefully like to share a fix?

---

### Post by TheFu on 2013-08-15
Not a VMware Player - specific solution, but this applies to all virtualization tech. [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

1) preallocate the storage - no sparce
2) don't over allocate CPU - 1 per guest is probably fine.
3) don't over allocate memory - anything over 2G is overkill.
4) leave at least 1 CPU and 1G of RAM for the hostOS. On a dual-core box, it is impossible to accomplish, so just be cautious with too much workload.  I run 8 VMs on a fast Core 2 Extreme without issues, so this isn't a hard rule, just a strong suggestion for people with 4+ cores.
5) Lots of BIOS settings matter - both the the hostOS and guestOSes.
6) Avoid using virtual GPU 2D and 3D acceleration if you have **any** performance issues. Turn that off in the settings, get great performance, make a backup, then consider carefully if you really need the "cheese." 
7) Use virtio for storage and networking.
8) Select Intel ICH chipsets wherever possible.

That about covers it, but read the article to catch small things

Oh - if your VMs are on SSDs, you can use whatever storage model you like - sparse, encrypted, compressed, full, whatever. It just doesn't matter. On spinning HDDs, use fully-preallocated storage.

---

