---
title: "Ubuntu 12.04 LTS x64 - Highpoint RocketRAID 2314pm RAID 5 and JBOD Arrays"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by lschnaidt on 2013-05-20
I'm trying to migrate away from Microsoft Windows 7 x64 SP1 Ultimate to UBUNTU 12.04 x64.

I currently am having a heck of time getting my RRAID2314 drivers installed, so I can access my RAID5 Array of 8TB and my JBOD Array of 7TB.  I can't get the drivers to compile and work with the 3.5 linux kernal.

Has anyone successfully installed these drivers, and if you have can you please help me?  I am a novice when it comes to the command line, but I can follow instructions very well.

I've tried editting the source to ignore the kernal version after 2.6, but alas it didn't work. 

Please HELP!

-loren

---

### Post by lschnaidt on 2013-05-20
I tried this, [http://blog.unclesniper.org/archives/3-HighPoint-RocketRAID-230x-on-Linux-3.0.html](http://blog.unclesniper.org/archives/3-HighPoint-RocketRAID-230x-on-Linux-3.0.html)

But it failed miserably.

serper@sabertooth:~/Downloads/rr231x_0x-linux-src-v2.5/product/rr2310pm/linux$ make install
[CC] /home/serper/Downloads/rr231x_0x-linux-src-v2.5/osm/linux/os_linux.c
In file included from /lib/modules/3.5.0-23-generic/build/include/linux/kernel.h:4:0,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/cache.h:4,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/time.h:7,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/stat.h:60,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/module.h:10,
                 from /home/serper/Downloads/rr231x_0x-linux-src-v2.5/osm/linux/osm_linux.h:21,
                 from /home/serper/Downloads/rr231x_0x-linux-src-v2.5/osm/linux/os_linux.c:6:
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:8:2: error: unknown type name &#8216;__kernel_long_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:9:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:10:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:11:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:12:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:13:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:14:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:15:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:18:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:19:2: error: unknown type name &#8216;__kernel_ulong_t&#8217;
/lib/modules/3.5.0-23-generic/build/include/linux/sysinfo.h:21:22: error: &#8216;__kernel_ulong_t&#8217; undeclared here (not in a function)
In file included from /lib/modules/3.5.0-23-generic/build/include/linux/kernel.h:15:0,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/cache.h:4,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/time.h:7,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/stat.h:60,
                 from /lib/modules/3.5.0-23-generic/build/include/linux/module.h:10,
                 from /home/serper/Downloads/rr231x_0x-linux-src-v2.5/osm/linux/osm_linux.h:21,
                 from /home/serper/Downloads/rr231x_0x-linux-src-v2.5/osm/linux/os_linux.c:6:
/lib/modules/3.5.0-23-generic/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [os_linux.o] Error 1

---

### Post by lschnaidt on 2013-05-21
150 views and no one has a solution to compiling rr231x_0x-linux-src-v2.5-091022-1618 for ubuntu 12.10 (linux kernel 3.5)?

The only solutions I have seen available are for kernel 3.0 or 2.6.  No such patch that I am aware of is out there for newer kernel builds.

I have two arrays with a total of 15TB of data on 2 sansdigital towerraid untits.  One unit is RAID5 the other is JBOD.  Neither with work without the rr231x_0x (2314pm to be exact) drivers installed.  I'm completely stuck and frustrated.  If Windows is the only way to use this, then I will continue to be slave to Microsoft.  A burden I would not wish on my worst enemy!

Long live Linux, Long live ubuntu with gnome 3!  Unity , NO!

-loren

---

### Post by lschnaidt on 2013-05-21
I emailed Highpoint and they sent me a copy of the 2.6 source files, which are not on the website.  They compile and install perfectly with CLI and Web GUI installed, it's working perfectly now.

Yay!!

-loren

---

### Post by ryangood on 2013-06-11
Can you possibly send me the 2.6 version of the drivers?

---

