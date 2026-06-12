---
title: "Anyone patched the 3.1 kernel for AppArmor compatibility yet?"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-09-02
I'm running Unity 3D beta 1 on a Linux 3.1rc4 mainline kernel.

Everything is running fine (since I purged the Trista PPA) except...

I'm still getting a boot error saying the (3.1) kernel isn't patched for AppArmor compatibility - been getting it for weeks.

Anyone had luck patching Linux 3.1 for AppArmor?!?!?

---

### Post by VinDSL on 2011-09-03
Interesting!

As fate would have it, I just installed an AppArmor update in Oneiric beta 1 via Synaptic.

Here are the results...

```

Setting up apparmor (2.7.0~beta1+bzr1774-1ubuntu1) ...
Installing new version of config file /etc/apparmor.d/abstractions/ubuntu-email ...
Installing new version of config file /etc/apparmor.d/abstractions/X ...
 * Starting AppArmor profiles                                                   Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 73): profile /sbin/dhclient network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 76): profile /usr/lib/telepathy/mission-control-5 network rules not enforced
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 76): profile /usr/lib/telepathy/telepathy-* network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 170): profile /usr/lib/cups/backend/cups-pdf network rules not enforced
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 170): profile /usr/sbin/cupsd network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.tcpdump (/etc/apparmor.d/usr.sbin.tcpdump line 64): profile /usr/sbin/tcpdump network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 141): profile /usr/bin/evince network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 141): profile /usr/bin/evince-previewer network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 141): profile /usr/bin/evince-thumbnailer network rules not enforced
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 73): profile /sbin/dhclient network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 76): profile /usr/lib/telepathy/mission-control-5 network rules not enforced
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 76): profile /usr/lib/telepathy/telepathy-* network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 170): profile /usr/lib/cups/backend/cups-pdf network rules not enforced
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 170): profile /usr/sbin/cupsd network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.tcpdump (/etc/apparmor.d/usr.sbin.tcpdump line 64): profile /usr/sbin/tcpdump network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 141): profile /usr/bin/evince network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 141): profile /usr/bin/evince-previewer network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 141): profile /usr/bin/evince-thumbnailer network rules not enforced
cat: /sys/kernel/security/apparmor/profiles: No such file or directory
invoke-rc.d: initscript apparmor, action "reload" failed.

```

Is anyone else running Linux 3.1 (just curious)?  LoL!  :D

---

### Post by MacUntu on 2011-09-03
That's the latest patch set I could find: [http://www.kernel.org/pub/linux/security/apparmor/apparmor-3.0-patches.tgz](http://www.kernel.org/pub/linux/security/apparmor/apparmor-3.0-patches.tgz)

You likely need to modify it a bit so it applies to the current kernel.

Note, that you also need to patch the kernel to enable ureadahead to collect new .pack files (that patch is in ureadahead sources, but also terribly outdated). That ureadahead patch worked with 3.0 IIRC: [http://paste.ubuntu.com/681082/](http://paste.ubuntu.com/681082/)

---

