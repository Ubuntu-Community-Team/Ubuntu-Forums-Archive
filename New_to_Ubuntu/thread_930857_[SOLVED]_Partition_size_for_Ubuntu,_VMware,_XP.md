---
title: "[SOLVED] Partition size for Ubuntu, VMware, XP"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by akelsall on 2008-09-26
Hello,

     I read through several posts and have a good idea about swap and root partition sizes now (think I'm leaning to 1GB swap and 10-15GB root), and probably 40+GB for /home. What I'm working towards is moving completely away from M$ in the next few months. 

In the mean time, as I wean myself off M$ and learn how to use Linux, I need to run XP along with Linux. What I'm planning to do is load VMware and create a Virtual Machine with XP (to avoid having to dual boot. I want to be able to run both at the same time). According to M$s' website, XP Pro requires 1.5GB of disk space. So, my question is, should I allocate more for XP since it's running "inside" VMware? Also, should I create a separate partition for the VMware software? I should also mention that I'm going to keep VMware installed so that I can also load Cisco Call Manager software and run it along side Linux. 

Thanks,

Andy

---

### Post by zephyrcat on 2008-09-26
Having Windows inside a virtual machine should not affect the disk space used (except of course for the size of the application), however you will definitely want more than 1.5GB for XP. Most virtual machine software will let you have the file holding the virtual hard drive dynamically expand, so you can just choose that and not worry about it.

---

### Post by mikewhatever on 2008-09-27
It's a good idea to let XP in vmware have a bit more then 1.5 BG. While MS may think it's enough, they also seem confident XP can run on 128 MB of RAM.
:lolflag:
I think about 4 GB is OK. You can also easily back it up by burning the whole thing to a DVD. If something goes wrong, just copy the files back to the HDD, no need to reinstall.
A separate partition is feasible, but not necessary. Completely up to you.

---

### Post by davidryder on 2008-09-27
When you create the HDD for your VM you can (at least in VirtualBox) select dynamically expanding image. This way it will grow as needed. I think I started mine out at 5gb.

---

