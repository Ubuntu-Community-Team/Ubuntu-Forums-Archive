---
title: "Kernel Hacking with VMWare"
date: 2009-03-11
forum: Programming Talk
---

### Post by grubby23 on 2009-03-11
Hi

I have downloaded the source code of the Kernel (linux-source-2.6.27) and
I wanna now make some slight modifications in some files. I am wondering if there is any possibility with VMWare to get this new Kernel running when
booting the virtual machine? In some Kernel Hacking introductions it is recommended to configure LILO in such a way that it points to the new Kernel. But this is not really an option for me I guess when I run a virtual machine? Any useful tips would be appreciated of how I can get
the modified Kernel running in my VM!

Thanks!

---

### Post by dwhitney67 on 2009-03-11
I am running VMware Server on my M$ workstation.  As a guest OS, I use Ubuntu 8.10.

Yesterday, I rebuilt the Ubuntu kernel (using this [guide]("http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/")), and rebooted with the new kernel.  VMware didn't seem to care one bit.

I suspect that you are thinking that the problem is bigger than it really is.  VMware doesn't care what kernel you use; what matters is if your kernel can deal with VMware.  :-)

---

