---
title: "Linux kernel 3.0.4 is here"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-02
The Oneiric kernel 3.0.0-10.16 is building in Launchpad now and will soon be ready.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-10.16](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-10.16)

---

### Post by masuch on 2011-09-04
Hi,

I have compiled /amd64/ kernel 3.0.4 - source code taken from kernel.org and using ubuntu patches from "/~kernel-ppa/mainline/v3.0.4-oneiric".
I have been expecting to get more or less similar behavior as the kernel 3.0.0-10.16 ... .

But When I switch to any virtual terminal - I do not see anything even if it seems that I can logon/logoff - it is just black screen.

When I have installed 3.0.0-10.16 kernel - everything is fine.

Could anybody tell me what I missed ? I have changed only processor to CORE2 and mtune=native and mcore=native, the rest of the config is default.

Thanks for any advice or hit to linux newbee.

---

### Post by xebian on 2011-09-04
Running ok here with 3.0.4 and 3.1.0-rc4 direct from kernel.org no patches.  What are those Ubuntu patches anyway?

---

### Post by Gunss on 2011-09-04
> **masuch said:**
> Hi,

I have compiled /amd64/ kernel 3.0.4 - source code taken from kernel.org and using ubuntu patches from "/~kernel-ppa/mainline/v3.0.4-oneiric".
I have been expecting to get more or less similar behavior as the kernel 3.0.0-10.16 ... .

But When I switch to any virtual terminal - I do not see anything even if it seems that I can logon/logoff - it is just black screen.

When I have installed 3.0.0-10.16 kernel - everything is fine.

Could anybody tell me what I missed ? I have changed only processor to CORE2 and mtune=native and mcore=native, the rest of the config is default.

Thanks for any advice or hit to linux newbee.

mcpu is not used anymore and you are better served with march=native than mtune=native.

Where you changed these options?

---

### Post by masuch on 2011-09-05
> **Gunss said:**
> mcpu is not used anymore and you are better served with march=native than mtune=native.

Where you changed these options?

Hi,
Thanks for replay. I wrote it incorrectly. I have changed mtune=native and march=native in file /arch/x86/Makefile ... where  $(CONFIG_MCORE2) started.

---

### Post by masuch on 2011-09-05
> **Gunss said:**
> mcpu is not used anymore and you are better served with march=native than mtune=native.

Where you changed these options?

Hi,
I have attached the script which I am using to compile the kernel ubuntu way or without oneiric patches. I hope that script is working properly if I am running 3 computers with 3.0.4 kernel compiled by myself.

---

### Post by masuch on 2011-09-06
please , anybody can help ?

---

### Post by masuch on 2011-09-12
> **xebian said:**
> Running ok here with 3.0.4 and 3.1.0-rc4 direct from kernel.org no patches.  What are those Ubuntu patches anyway?


I have been following step by step how to compile kernel Ubuntu way, but I am extremely newbie in Linux kernel compilation. 
I would like to know as well for what purpose are those Ubuntu patches ?

---

