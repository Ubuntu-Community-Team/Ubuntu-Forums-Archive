---
title: "export block device over firewire"
date: 2009-02-24
forum: Programming Talk
---

### Post by mrsteveman1 on 2009-02-24
Couldn't decide if this is the right forum or not but here goes....

There has been talk of implementing a software SBP2 target in the new firewire stack in the kernel going back at least 2 years from what i can see:

> Implement an SBP-2 target using the in-kernel SCSI target framework as an alternative to Endpoint (Oracle's SBP-2 target implementation in userspace).

[http://ieee1394.wiki.kernel.org/index.php/To_Do#New_drivers]("http://ieee1394.wiki.kernel.org/index.php/To_Do#New_drivers")

Thats the wiki, the same thing is mentioned in some of the mailing lists. Was this ever implemented? I can't find anything that looks like this sort of driver in the newest kernel source, so is it planned?

Second as mentioned above, this was supposed to replace the extremely old Oracle Endpoint software, which basically takes a block device or an image file and exports it over firewire for use by another machine as if it were just a firewire disk. However when i compile the source, available here:

[http://oss.oracle.com/projects/endpoint/dist/files/endpoint-0.1.0.tar.gz]("http://oss.oracle.com/projects/endpoint/dist/files/endpoint-0.1.0.tar.gz") 

.....on Intrepid with all the required libraries and dev files installed, it compiles but spits this message out when run. I'm not a developer but i can read C pretty well, can someone tell me if i need to change something, or if the code is just too old to compile and run now? It is from 2003. Any help even if it is to tell me it won't work, is appreciated :D

> root@live:~/endpoint-0.1.0/src# ./endpoint
*** glibc detected *** ./endpoint: double free or corruption (fasttop): 0x081a7080 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7efe454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7f004b6]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb8036c06]
/usr/lib/libglib-2.0.so.0[0xb802064b]
/usr/lib/libglib-2.0.so.0[0xb80206b5]
/usr/lib/libglib-2.0.so.0(g_hash_table_remove_all+0x3a)[0xb802138a]
/usr/lib/libglib-2.0.so.0(g_hash_table_destroy+0x2d)[0xb80214dd]
./endpoint[0x804a2f9]
./endpoint[0x804a5d1]
./endpoint[0x804b23b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7ea5685]
./endpoint[0x804a241]
======= Memory map: ========
08048000-08054000 r-xp 00000000 00:12 23516      /root/endpoint-0.1.0/src/endpoint
08054000-08055000 r--p 0000b000 00:12 23516      /root/endpoint-0.1.0/src/endpoint
08055000-08056000 rw-p 0000c000 00:12 23516      /root/endpoint-0.1.0/src/endpoint
081a7000-081c8000 rw-p 081a7000 00:00 0          [heap]
b7d00000-b7d21000 rw-p b7d00000 00:00 0 
b7d21000-b7e00000 ---p b7d21000 00:00 0 
b7e55000-b7e62000 r-xp 00000000 00:12 668        /lib/libgcc_s.so.1
b7e62000-b7e63000 r--p 0000c000 00:12 668        /lib/libgcc_s.so.1
b7e63000-b7e64000 rw-p 0000d000 00:12 668        /lib/libgcc_s.so.1
b7e64000-b7e65000 rw-p b7e64000 00:00 0 
b7e65000-b7e8d000 r-xp 00000000 00:12 110        /lib/libpcre.so.3.12.1
b7e8d000-b7e8e000 r--p 00027000 00:12 110        /lib/libpcre.so.3.12.1
b7e8e000-b7e8f000 rw-p 00028000 00:12 110        /lib/libpcre.so.3.12.1
b7e8f000-b7fe7000 r-xp 00000000 00:12 32         /lib/tls/i686/cmov/libc-2.8.90.so
b7fe7000-b7fe9000 r--p 00158000 00:12 32         /lib/tls/i686/cmov/libc-2.8.90.so
b7fe9000-b7fea000 rw-p 0015a000 00:12 32         /lib/tls/i686/cmov/libc-2.8.90.so
b7fea000-b7fee000 rw-p b7fea000 00:00 0 
b7fee000-b7ff3000 r-xp 00000000 00:12 2726       /usr/lib/libraw1394.so.8.2.0
b7ff3000-b7ff4000 r--p 00004000 00:12 2726       /usr/lib/libraw1394.so.8.2.0
b7ff4000-b7ff5000 rw-p 00005000 00:12 2726       /usr/lib/libraw1394.so.8.2.0
b7ff5000-b80aa000 r-xp 00000000 00:12 635        /usr/lib/libglib-2.0.so.0.1800.2
b80aa000-b80ab000 r--p 000b4000 00:12 635        /usr/lib/libglib-2.0.so.0.1800.2
b80ab000-b80ac000 rw-p 000b5000 00:12 635        /usr/lib/libglib-2.0.so.0.1800.2
b80b1000-b80b3000 rw-p b80b1000 00:00 0 
b80b3000-b80cd000 r-xp 00000000 00:12 26         /lib/ld-2.8.90.so
b80cd000-b80ce000 r-xp b80cd000 00:00 0          [vdso]
b80ce000-b80cf000 r--p 0001a000 00:12 26         /lib/ld-2.8.90.so
b80cf000-b80d0000 rw-p 0001b000 00:12 26         /lib/ld-2.8.90.so
bffbb000-bffd0000 rw-p bffeb000 00:00 0          [stack]
Aborted


---

### Post by pepijndevos on 2009-03-12
I'm looking for the same thing.
I know Macs can do it, and I'd like an Ubuntu thumbdrive that lets me access any computer as a FireWire or even USB drive.
This is useful for loads of purposes, backup/resture/rescue things, reuse of old computers as HDD's, etc, etc...

Maybe the easy way is to start Ubuntu with a low runlevel and do something with a samba share?

---

### Post by mrsteveman1 on 2009-03-13
> **pepijndevos said:**
> I'm looking for the same thing.
I know Macs can do it, and I'd like an Ubuntu thumbdrive that lets me access any computer as a FireWire or even USB drive.
This is useful for loads of purposes, backup/resture/rescue things, reuse of old computers as HDD's, etc, etc...

Maybe the easy way is to start Ubuntu with a low runlevel and do something with a samba share?

That would be useful, a small linux distro that would fit on a key, that would on startup look for all mountable filesystems and make all of them available over samba by default.

We will have to see if the kernel implementation gets merged some time, maybe i will have a look around the various kernel development trees to see if they are working on it. I really need raw access to a block device though so firewire is essential.

Apparently you can also get a small module with a USB device controller on it that can then be used to export block devices over USB with the USB-gadget kernel module which is already in most distros. Problem is you need a special hardware chip for every machine you wish to make available as a USB device.

---

