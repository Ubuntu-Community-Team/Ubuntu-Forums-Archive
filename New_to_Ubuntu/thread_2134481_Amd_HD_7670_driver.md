---
title: "Amd HD 7670 driver"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by BobosAbelMihai on 2013-04-11
Hello everyone. First please excuse my english if I make some mistakes. I am new to ubuntu, so far i had some problems but i kept fixing them but one problem i simply cannot find any solution.
My system is a Toshiba Satellite L855-149, I7,Amd HD 7670, 4 GB Ram. I use ubuntu 12.10 , 64 bits.

First time, i was able to install the driver for my video card using this commands:
```
sudo apt-get install linux-source
sudo sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run

```

But, after that the system made an Update, and everything crashed, i believe it was because of Kernel. I reinstalled the system, and now with the same command i cannot install the driver, it gives me this error:
> 
Check if system has the tools required for installation. fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-27-generic/build/include/linux/version.h cannot be found on this system.

Another thing is that my system overheats very very fast, and all 8 CPUS are 30-40% used , thing that never happend before.

Please help me and tell me what to do.
Thank you.

---

### Post by wickedpuppy on 2013-04-11
First we install kernel header

```
sudo apt-get install linux-headers-$(uname -r)
```

Then try reinstalling the driver. Does it still shows the same error as before?

---

### Post by ajgreeny on 2013-04-11
Double check that you have the linux-headers-3.5.0-27 and linux-headers-3.5.0-27-generic installed.

They seem not to be installed by default when the new kernel is installed or updated.

---

### Post by BobosAbelMihai on 2013-04-11
I installed the kernel header, then the driver and everything worked.

The problem with the overheating maybe now will vanish, at least that's what i hope.

Thank you very much.

---

