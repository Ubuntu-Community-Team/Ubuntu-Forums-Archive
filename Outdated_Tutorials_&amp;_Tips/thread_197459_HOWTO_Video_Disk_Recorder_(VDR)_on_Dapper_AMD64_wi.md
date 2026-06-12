---
title: "HOWTO: Video Disk Recorder (VDR) on Dapper AMD64 with TT Budget card support."
date: 2006-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by blazko on 2006-06-15
Hello all,

Although there are 64 bit VDR packages available for Dapper, they miss the Softdevice plugin - so owners of DVB-s cards with no built-in MPEG decoder cannot use VDR this way.

So I have updated my HOWTO on compiling and installing VDR (64bit) on Dapper:

[http://neveprise.net/main.do?id=howto-vdr-ubuntu64src]("http://neveprise.net/main.do?id=howto-vdr-ubuntu64src")

Feedback welcome.

Greetings, Timo

---

### Post by lmandrake on 2006-08-16
Hello blazko,

your guide is really good :) Everybody who wants to use the latest vdr version should have a look at it.

Maybe you could put your guide into the vdr or ubuntu wiki? Or allow other people to do this.

Cu
lmandrake

---

### Post by Jussi Kukkonen on 2006-08-22
> **blazko said:**
> 

So I have updated my HOWTO on compiling and installing VDR (64bit) on Dapper:

[http://neveprise.net/main.do?id=howto-vdr-ubuntu64src]("http://neveprise.net/main.do?id=howto-vdr-ubuntu64src")


Thanks for the howto. I didn't actually follow it myself, but it had many useful pieces of information.

> Feedback welcome.
Here goes:

One of the reasons I didn't follow the guide was that you didn't use package management (as in, you did *make; make install; etc...* instead of *dpkg-buildpackage ...; dpkg -i ...*) -- was there a reason for that or are you just more familiar with compiling by hand? The debianization seems like quality work to me, and having the packages in dpkg-database is a Good Thing™ in my opinion. It looks like things might have been easier too (no symbolic linking by hand, compile flag defaults mostly better, no need to have sources in certain place). Also, a related hint: You don't need to install required compile dependencies by hand, a better method (especially when advicing others with possibly different setups) is *apt-get build-dep vdr-plugin-softdevice*.

I had to compile ffmpeg too, because of the missing *--enable-shared* flag in the ubuntu binary. I used stock ubuntu source, though (again, to get it easily into dpkg). Seems to work fine... Then again, I'm not that familiar with ffmpeg. You seemed to think upgrading to cvs version is advisable, could you elaborate on that? (give me an excuse to break a fully functioning vdr box :) )

With softdevice I started with 0.2.3a also, but have recently started using the cvs-version. I can recommend this, it feels better in many ways -- no more picture ratio change problems, better deinterlace filters, etc. The development seems to be a lot faster than the release schedule shows...

---

### Post by Eskas on 2006-09-27
I have followed this guide, but can't get vdr to work.

when I run ./runvdr-softdevice i get:
```

[softdevice] processing args 
[softdevice]   argv [0] = softdevice 
[softdevice]   argv [1] = -vo 
vo_argv: xv:full 
[ProcessArgs] xv: start up fullscreen 
[softdevice] initializing Plugin 
[softdevice] Initializing Video Out 
./runvdr: line 34: 24349 Segmentation fault      ./vdr -w 60 -u media 
--config=../etc --lib=../lib --plugin='softdevice -vo xv:full'Wed Sep 
27 07:44:54 CEST 2006 reloading DVB driver 

```

systemlog:
```

Sep 27 07:46:45 mackan-desktop vdr: [24505] VDR version 1.4.2 started 
Sep 27 07:46:45 mackan-desktop vdr: [24505] loading plugin: 
../lib/libvdr-softdevice.so.1.4.2 
Sep 27 07:46:45 mackan-desktop vdr: [24505] loading ../etc/setup.conf 
Sep 27 07:46:45 mackan-desktop vdr: [24505] loading ../etc/sources.conf 
Sep 27 07:46:45 mackan-desktop vdr: [24505] loading ../etc/diseqc.conf 
Sep 27 07:46:45 mackan-desktop vdr: [24505] loading ../etc/channels.conf 
Sep 27 07:46:45 mackan-desktop vdr: [24505] loading ../etc/svdrphosts.conf 
Sep 27 07:46:45 mackan-desktop vdr: [24505] loading ../etc/keymacros.conf 
Sep 27 07:46:45 mackan-desktop vdr: [24505] reading EPG data from 
/home/media/Video/Recordings/epg.data 
Sep 27 07:46:45 mackan-desktop vdr: [24505] probing /dev/dvb/adapter0/frontend0 
Sep 27 07:46:45 mackan-desktop vdr: [24506] video directory scanner 
thread started (pid=24505, tid=24506) 
Sep 27 07:46:45 mackan-desktop vdr: [24506] video directory scanner 
thread ended (pid=24505, tid=24506) 
Sep 27 07:46:45 mackan-desktop vdr: [24507] video directory scanner 
thread started (pid=24505, tid=24507) 
Sep 27 07:46:45 mackan-desktop vdr: [24507] video directory scanner 
thread ended (pid=24505, tid=24507) 
Sep 27 07:46:45 mackan-desktop kernel: [17204565.868000] dst_ca_open: 
Device opened [ddef1a80] 
Sep 27 07:46:45 mackan-desktop kernel: [17204565.868000] dst_ca_ioctl: 
 Getting Slot capabilities 
Sep 27 07:46:45 mackan-desktop kernel: [17204565.868000] put_checksum: 
 Computing string checksum. 
Sep 27 07:46:45 mackan-desktop kernel: [17204565.868000] put_checksum: 
 -> string length : 0x07 
Sep 27 07:46:45 mackan-desktop kernel: [17204565.868000] put_checksum: 
 -> checksum      : 0xb5 
Sep 27 07:46:45 mackan-desktop kernel: [17204565.932000] dst_put_ci: 
Put Command 
Sep 27 07:46:45 mackan-desktop vdr: [24505] CAM doesn't support link 
layer interface 
Sep 27 07:46:45 mackan-desktop vdr: [24505] found 1 video device 
Sep 27 07:46:45 mackan-desktop vdr: [24505] initializing plugin: 
softdevice (0.2.3): A software emulated MPEG2 device 
Sep 27 07:46:45 mackan-desktop kernel: [17204566.068000] 
ca_get_slot_caps:  -->dst_put_ci SUCCESS ! 
Sep 27 07:46:45 mackan-desktop kernel: [17204566.068000] 
ca_get_slot_caps:  Slot cap = [185] 
Sep 27 07:46:45 mackan-desktop kernel: [17204566.068000] 
=================================== 
Sep 27 07:46:45 mackan-desktop kernel: [17204566.068000]  7 64 0 0 0 0 0 185 
Sep 27 07:46:45 mackan-desktop kernel: [17204566.068000] dst_ca_ioctl: 
 -->CA_GET_CAP Success ! 
Sep 27 07:46:45 mackan-desktop kernel: [17204566.068000] 
dst_ca_release:  Device closed.

```

Anyone knows what's wrong?

---

