---
title: "ifb device missing in v2.6.20.3-ubuntu"
date: 2007-06-13
forum: Packaging and Compiling Programs
---

### Post by safroud on 2007-06-13
Hello,

I need to use the Intermediate Functional Block device (ifb), the Kernel module is not compiled and  when I try to compile it from the Kernel source , I don't find the corresponding option in the configuration menu.

According to [http://linux-net.osdl.org/index.php/IFB](http://linux-net.osdl.org/index.php/IFB)

The option is located here :

Device drivers -> Network device support -> Intermediate Functional Block support


Any help to get ifb working ?

Many thanks in advance.

---

### Post by zorlem on 2007-12-18
It's in the kernel, but is not visible as an option in config by default because it depends on another item to be selected first. Here is the relevant part of <kernel-source>/drivers/net/Kconfig
[cut]
config IFB
        tristate "Intermediate Functional Block support"
        depends on NET_CLS_ACT
        ---help---
          This is an intermediate driver that allows sharing of
          resources.
[/cut]
So, to be visible in your make *config you have to first enable NET_CLS_ACT, which is located under: Networking -> Networking Options -> QoS and/or fair queueing -> Actions. After you select this option IFB becomes available for selection under Device Drivers -> Network Device Support -> Intermediate Functional Block support.

Hope this helps.

Have fun!

---

