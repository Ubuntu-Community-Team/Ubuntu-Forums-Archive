---
title: "Problem with asus usb-n13 in backtrack5 r3"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by ZEraX4 on 2013-02-11
HI

I have an ((ASUS USB-N13 <<chipset 8192cu>>)) and i using it in ubuntu ((specially <<backtrack 5 r3>> ))

in virtual machine ((VMware Workstation 9))

and i have problem when i write this command to install the driver and this is what i see :

```

root@bt:~/Desktop/rtl8192cu# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.2.6/build M=/root/Desktop/rtl8192cu  modules
make[1]: Entering directory `/usr/src/linux-source-3.2.6'


  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers

           is missing; modules will have no dependencies and modversions.


  CC [M]  /root/Desktop/rtl8192cu/core/rtw_cmd.o

In file included from /root/Desktop/rtl8192cu/core/rtw_cmd.c:24:

/root/Desktop/rtl8192cu/include/osdep_service.h:49:29: error: linux/smp_lock.h: No such file or directory

In file included from /root/Desktop/rtl8192cu/include/drv_types.h:69,

                 from /root/Desktop/rtl8192cu/core/rtw_cmd.c:25:

/root/Desktop/rtl8192cu/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:

/root/Desktop/rtl8192cu/include/rtw_recv.h:622: warning: cast from pointer to integer of different size

/root/Desktop/rtl8192cu/include/rtw_recv.h:622: warning: cast to pointer from integer of different size

make[2]: *** [/root/Desktop/rtl8192cu/core/rtw_cmd.o] Error 1

make[1]: *** [_module_/root/Desktop/rtl8192cu] Error 2

make[1]: Leaving directory `/usr/src/linux-source-3.2.6'

make: *** [modules] Error 2


```
and when i write : 

```
root@bt:~/Desktop/rtl8192cu# make install
install -p -m 644 8192cu.ko  /lib/modules/3.2.6/kernel/drivers/net/wireless/
install: cannot stat `8192cu.ko': No such file or directory
make: *** [install] Error 1
```

and i can see it in this command : 

```
root@bt:~# lsusb
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Please help me :)

I Forget something ((I installed the system on VMware <<NOW>> and i didn't do anything in it))

and other quistion ::can i link the internal adapter for Lap Top to the vmware and how ?::

Thanks in advance

---

