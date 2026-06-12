---
title: "Grub Rescue issue"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by sricharanch on 2013-02-16
Hi!
I am using Ubuntu 12.04 as a dual boot along with windows7 with Ubuntu on a separate partition. I have tried increasing swap size using Gparted in live cd mode using the Ubuntu 10.04 disc. In the process I have come across resizing Ubuntu partition and deleting the swap file and creating a new one. After that I was left out with a problem of unknown file system Grub rescue problem at boot and I was unable to boot my system into either OS. Also I tried some thing looking into the forums and I can make it to a lime editing mode. But when I tried command boot there, I got a problem called kernel not loaded. Can any one please help me with this issue?

---

### Post by grahammechanical on 2013-02-16
I am going to assume that as you are posting on this forum you have access to a computer. So, I recommend Ubuntu Secure Remix to you.

[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

That has a utility Boot Repair. That might fix this issue. At least you can use it to collect information about your boot/partition set up that you can post a link to. That in turn might provide information that others can use to help you.

I do not understand why you cannot boot into Windows 7. Your actions may have messed up booting into Ubuntu but they should not have prevented the loading of the Grub boot loader or the loading of Windows 7.

The fact that you get a Grub Rescue prompt tells me that Grub is trying to do its job but it is not pointing to the Linux kernel. Or it cannot read the file system that it is looking on for a kernel.

I suspect that in deleting the swap partition and then creating a new swap partition that you changed the Universally Unique Identifier (UUID) labels for the partitions. Grub uses those UUIDs to know where to look for the kernels that we select to boot into. They are recorded in the Grub configuration files.

I strongly advise you to recover all your important data from both Ubuntu and Windows because a re-install of Ubuntu might be the simplest method of fixing this problem. Painful, yes. Simple, also yes.

Regards.

---

