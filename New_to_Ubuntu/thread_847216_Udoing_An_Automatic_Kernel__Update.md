---
title: "Udoing An Automatic Kernel  Update"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2008-07-02
My iBurst broadand modem has been working all the time.  Yesterday, it refused to go on.  However, it works in Windows.  My gut feeling is that it might be related to the automatic software updates.  Virtualbox also refused to work.  I got a message that said something to the effect of: Virtual kernel driver not installed. After typing: $sudo /etc/init.d/vboxdrv setup it worked again.

Now, I want to know how do I undo software updates.

Thanks in advance.

Arnold

---

### Post by Xerp on 2008-07-02
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[https://help.ubuntu.com/community/SynapticHowto#How%20to%20force%20the%20installation%20of%20a%20package%20version](https://help.ubuntu.com/community/SynapticHowto#How%20to%20force%20the%20installation%20of%20a%20package%20version)

---

### Post by chrisccoulson on 2008-07-02
Virtualbox will stop working with each new kernel because it relies on the use of a kernel module. The kernel module will need to be rebuilt for each kernel you run. I'm not familiar with Virtualbox, so I can't help you with rebuilding the kernel module. I'm sure someone else will be able to help.

Kernel updates often contain important security fixes, so you should normally upgrade.

How are the drivers for your iBurst modem installed?

---

