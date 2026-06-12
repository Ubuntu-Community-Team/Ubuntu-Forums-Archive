---
title: "troubles compiling drivers"
date: 2010-03-04
forum: Programming Talk
---

### Post by pedrotuga on 2010-03-04
This might probably of a general support question. Since it concerns compiling using gnubuild i thought maybe i would be lucky if i posted on this section.

So, i bought this digital TV usb dongle, and i'm trying to compile its driver, but i am getting some 'no such file' error.

I downloaded the sources and installed them in the same fashion as described in here (this is just for reference... the details come right after...)
[https://www.dealextreme.com/forums/Default.dx/sku.8325~threadid.278942](https://www.dealextreme.com/forums/Default.dx/sku.8325~threadid.278942)
> hg clone [http://linuxtv.org/hg/~anttip/ec168/](http://linuxtv.org/hg/~anttip/ec168/)

When it completes downloading, go into the folder ~/ec168/ and run make.

Hopefully the compiling goes well, then you will have a lot of modules in the ~/ec168/v4l/ subfolder.

Then you have to download the firmware from [http://palosaari.fi/linux/v4l-dvb/firmware/ec168/dvb-usb-ec168.fw](http://palosaari.fi/linux/v4l-dvb/firmware/ec168/dvb-usb-ec168.fw)

( This file can also be found on your driver CD, called EC168BDA.bin. This has to be renamed to dvb-usb-ec168.fw )

Put this file in /lib/firmware/

Then load the following modules from the ~/ec168-2/v4l/ folder:

sudo insmod dvb-core.ko
sudo insmod dvb-usb.ko
sudo insmod ec100.ko
sudo insmod mxl5005s.ko
sudo insmod dvb-usb-ec168.ko

Fire up VLC, open capture device, set it to dvb, select frequency of your local transponder, and enjoy the show.



make doesn't compile successfully :(

```
p@p-laptop:~/dvbdongle/ec168$ make
make -C /home/p/dvbdongle/ec168/v4l 
make[1]: Entering directory `/home/p/dvbdongle/ec168/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/p/dvbdongle/ec168/v4l/firmware'
make[2]: Leaving directory `/home/p/dvbdongle/ec168/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/p/dvbdongle/ec168/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/p/dvbdongle/ec168/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-19-generic/build
make -C /lib/modules/2.6.31-19-generic/build SUBDIRS=/home/p/dvbdongle/ec168/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/p/dvbdongle/ec168/v4l/firedtv-1394.o
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:37: warning: 'struct hpsb_iso' declared inside parameter list
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:37: warning: its scope is only this definition or declaration, which is probably not what you want
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:53: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:54: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:61: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:62: error: implicit declaration of function 'dma_region_i'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:62: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:62: error: expected expression before 'unsigned'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:63: warning: assignment makes pointer from integer without a cast
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:82: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'node_of':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:87: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:87: warning: type defaults to 'int' in declaration of '__mptr'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:87: warning: initialization from incompatible pointer type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:87: error: invalid use of undefined type 'struct unit_directory'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'node_lock':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:92: error: implicit declaration of function 'hpsb_node_lock'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:92: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:92: error: (Each undeclared identifier is reported only once
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:92: error: for each function it appears in.)
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:93: error: 'quadlet_t' undeclared (first use in this function)
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:93: error: expected ')' before 'arg'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'node_read':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_read'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'node_write':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:103: error: implicit declaration of function 'hpsb_node_write'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'start_iso':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:114: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:114: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:116: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:118: warning: assignment makes pointer from integer without a cast
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:125: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:128: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'stop_iso':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:139: error: implicit declaration of function 'hpsb_iso_stop'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: At top level:
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:154: warning: 'struct hpsb_host' declared inside parameter list
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'fcp_request':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:167: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:168: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'node_probe':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:182: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:182: warning: type defaults to 'int' in declaration of '__mptr'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:182: warning: initialization from incompatible pointer type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:182: error: invalid use of undefined type 'struct unit_directory'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:187: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:187: error: 'quadlet_t' undeclared (first use in this function)
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:188: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:188: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:188: warning: assignment makes pointer from integer without a cast
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: At top level:
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:243: warning: 'struct unit_directory' declared inside parameter list
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'node_update':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:245: error: dereferencing pointer to incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: At top level:
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:253: error: variable 'fdtv_driver' has initializer but incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:254: error: unknown field 'name' specified in initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:254: warning: excess elements in struct initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:254: warning: (near initialization for 'fdtv_driver')
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:255: error: unknown field 'update' specified in initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:255: warning: excess elements in struct initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:255: warning: (near initialization for 'fdtv_driver')
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:256: error: unknown field 'driver' specified in initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:256: error: extra brace group at end of initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:256: error: (near initialization for 'fdtv_driver')
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:259: warning: excess elements in struct initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:259: warning: (near initialization for 'fdtv_driver')
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:262: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_highlevel')
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:264: error: unknown field 'fcp_request' specified in initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_highlevel')
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:271: error: implicit declaration of function 'hpsb_register_highlevel'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:272: error: invalid use of undefined type 'struct hpsb_protocol_driver'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:273: error: implicit declaration of function 'hpsb_register_protocol'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:276: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/p/dvbdongle/ec168/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/p/dvbdongle/ec168/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/p/dvbdongle/ec168/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/p/dvbdongle/ec168/v4l'
make: *** [all] Error 2
p@p-laptop:~/dvbdongle/ec168$ 

```

I checked i have linux-headers properly installed... i think

```
$ ls -l /usr/src/
total 32
drwxr-xr-x 23 root root 4096 2009-12-02 22:26 linux-headers-2.6.31-15
drwxr-xr-x  7 root root 4096 2009-12-02 22:26 linux-headers-2.6.31-15-generic
drwxr-xr-x 23 root root 4096 2009-12-10 23:24 linux-headers-2.6.31-16
drwxr-xr-x  7 root root 4096 2009-12-10 23:24 linux-headers-2.6.31-16-generic
drwxr-xr-x 23 root root 4096 2010-01-06 22:54 linux-headers-2.6.31-17
drwxr-xr-x  7 root root 4096 2010-01-06 22:54 linux-headers-2.6.31-17-generic
drwxr-xr-x 23 root root 4096 2010-02-08 01:17 linux-headers-2.6.31-19
drwxr-xr-x  7 root root 4096 2010-02-08 01:17 linux-headers-2.6.31-19-generic


$ uname -r
2.6.31-19-generic

```


can anybody tell me what can be causing the error?

---

### Post by MindSz on 2010-03-05
I see that you run 'make'. Most times it's better to use ```
$sudo make
``` since there might be some files that need installing in protected folders.

Other than that, I think you should contact the drivers' distributor.

---

### Post by Bachstelze on 2010-03-05
> **MindSz said:**
> I see that you run 'make'. Most times it's better to use ```
$sudo make
``` since there might be some files that need installing in protected folders.

**Never** do this unless you know **exactly** what you are doing. [font=monospace]make[/font] alone should **not** install anything, only build it.

---

