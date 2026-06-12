---
title: "Install and configure kernel sources"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by pedro21 on 2013-02-07
Hi,

I'm trying to manually install a driver for a CAN device, and on the installation instructions there is a note which states:
"It is absolutely necessary to install the kernel sources and configure them to comply with the running kernel, before installing the CAN-driver!"

I don't know exactly what this means and how to do it. The only thing I did was "sudo apt-get install linux-source", which created the folder "linux-source-3.2.0" in /usr/src (does this mean that I installed the kernel sources or just downloaded them?). After that, I don't know what else to do.
Can somebody help me on this?

I'm using ubuntu 12.04.1, kernel v3.2.0-37-generic, 64-bit.

Thanks in advance!

Best regards,
Pedro

---

### Post by ptn107 on 2013-02-07
You don't want the entire source code for the linux kernel.  It's big and unnecessary.  You just need to install the kernel headers.  The following command at a terminal will do just that and pull in everything else needed.

```
sudo apt-get install linux-headers-generic
```

---

