---
title: "New Install  Keeps Locking Up"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by drironside on 2008-07-02
I've dual booted Ubuntu 8.04 on a separate partition on the same hard drive with Vista.  Vista is still working fine, but my Ubuntu install locks up every so often.  Sometimes it's only for a few seconds, but other times the only way out is to restart the computer.  What could be going on?

---

### Post by starcannon on 2008-07-02
What wifi card do you have? I've been reading about this lockup and noticing a broadcom trend:

```
lshw -C network
```

I don't know if it has anything to do with the lockups, I know I have 8.04 on a bunch of different machines, none of them lock up, I use Nvidia, ATi, Intel, and even a VIA graphics chips.

---

### Post by drironside on 2008-07-02
> **starcannon said:**
> What wifi card do you have? I've been reading about this lockup and noticing a broadcom trend:

```
lshw -C network
```

I don't know if it has anything to do with the lockups, I know I have 8.04 on a bunch of different machines, none of them lock up, I use Nvidia, ATi, Intel, and even a VIA graphics chips.

I'm running on a wired home network.  It's a Gateway desktop.  Don't remember what video card is in here - I'd have to go back to the Vista side of this dual boot. It's located on the same hard drive in another partition.

I ran that code you posted in the terminal and here is what I got:

joann@joann-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:04:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:61:9c:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.101 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes

---

