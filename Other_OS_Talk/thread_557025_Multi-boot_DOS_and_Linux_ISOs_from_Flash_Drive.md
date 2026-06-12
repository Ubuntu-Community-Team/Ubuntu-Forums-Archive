---
title: "Multi-boot DOS and Linux ISOs from Flash Drive?"
date: 2007-09-22
forum: Other OS Talk
---

### Post by Githlar on 2007-09-22
I have a problem. I have a system recovery disk that I want to use for editing my partitions, but I don't have a CD to burn it on. I know it's possible to boot from a flash drive. Awesome.

But that go me thinking. I know some boot disks use a Syslinux bootsector, while others use a DOS bootsector. Well, what if I want to have multiple boot disks on my 2GB flash drive?

OK, so here are my thoughts:

1) Partition the disk into a separate partition for each disk and only flag one partition at a time as bootable. This would be really painstaking - especially if you don't have access to another machine.

2) Same as example number 1, but be able to switch the boot flag of each partition from each partition, e.g. Write a specialized program for each partition that will do this for me. I'll need a lot more technical insight for this.

3) Boot Syslinux and somehow boot both the DOS and Linux .iso files straight from Syslinux? Is this even possible? If so, it'd make the whole thing so much easier.

I'm open to any comments or questions you may have on this topic. And please, if there's a way I haven't thought of yet, I'd like to know =)

---

