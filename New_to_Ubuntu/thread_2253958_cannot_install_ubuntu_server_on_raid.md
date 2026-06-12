---
title: "cannot install ubuntu server on raid"
date: 2014-11-23
forum: New to Ubuntu
---

### Post by winston3 on 2014-11-23
I tried to install ubuntu server by following the instruction here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID). I have an error at the very end of the process. "No boot loader has been installed, either because you chose not to or because your specific architecture doesn't support a boot loader yet." I have no idea how to solve it since I'm new to Ubuntu. Can anyone please help me regarding this issue?

---

### Post by sandyd on 2014-11-23
> **winston3 said:**
> I tried to install ubuntu server by following the instruction here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID). I have an error at the very end of the process. "No boot loader has been installed, either because you chose not to or because your specific architecture doesn't support a boot loader yet." I have no idea how to solve it since I'm new to Ubuntu. Can anyone please help me regarding this issue?
What version of Ubuntu are you using?

The issue may be that the guide you have followed is a guide for Ubuntu 9.10, and not for your version of Ubuntu (Ubuntu 9.10 which is now End Of Life and no longer supported). An updated guide (for Ubuntu 12.04) can be found at [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

---

### Post by mastablasta on 2014-11-24
> **winston3 said:**
>  I have an error at the very end of the process. "No boot loader has been installed, either because you chose not to or because your specific architecture doesn't support a boot loader yet." 

GRUB is the boot loader. sometime during install you forgot to tell it where to install it or you told it to install it on the wrong place. did you maybe install it on media you used to create the image of the OS on?

---

