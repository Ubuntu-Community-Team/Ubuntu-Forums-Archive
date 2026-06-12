---
title: "Ubuntu will not boot properly"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by qwertyatom100 on 2013-05-14
I have just tried to install Ubuntu 12.04LTS on a Windows XP laptop and after selecting Ubuntu as the OS to run it loads for a while and then drops me into busybox. Is there any way to fix this?:(

---

### Post by TheFu on 2013-05-14
Are you certain it is "busybox"?  I doubt that shell is even installed for ubuntu. 

Could you be at a root maintenance window?  

Could it be that X/Windows is failing to start and that is the only issue?

I'd check the /var/log/Xorg.0.log for some hints.  If the machine is older, then the graphics card chips might not be supported by default.

---

### Post by qwertyatom100 on 2013-05-14
Found the problem, it's trying to boot from hdd 0,0. How to fix? (I want it to boot from hard drive 1)

---

### Post by TheFu on 2013-05-14
The easy answer is to let** Boot Repair** handle it.
Google for "boot repair ubuntu" and follow those instructions.

---

