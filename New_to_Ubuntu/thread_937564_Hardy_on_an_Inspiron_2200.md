---
title: "Hardy on an Inspiron 2200"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by queelix on 2008-10-04
Hi

I am having a problem with Hardy freezing (cap lock and scroll lock blinking - kernel panic?) after about 5 to 20 minutes of use on a Dell Inspiron 2200.  The machine dual boots XP and runs that fine.

Anyone else have this issue and find a solution?

Thanks.

---

### Post by tigerstripedcat on 2008-10-04
Those are freakin annoying.  Things you can try:

1) Kernel options.  Depending on your configuration (you'll need to do some googling) you might need kernel options in your /etc/grub/menu.lst like 
noapic 
nolapic 
pci=noacpi 
acpi=off 
no_timer_check  
notsc
acpi_use_timer_override 
I've had to use these at various times on different computers to fix stability issues.

2) Get the latest kernel.  Google for kernelcheck.  2.6.26 might support your configuration better, and kernelcheck is able to easily install a vanilla kernel

3) You can go through /var/log/syslog.  Grep for the word "restart" and then look for what's right before it.  This might show you what is causing this.

TSC

---

### Post by queelix on 2008-10-09
I ended up installing the Ibex beta (Kernel 2.6.27-4) and it no longer has this problem.

---

