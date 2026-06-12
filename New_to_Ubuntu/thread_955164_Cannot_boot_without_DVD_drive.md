---
title: "Cannot boot without DVD drive"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by thatdecade on 2008-10-21
I noticed this while I was building this machine, but did the workaround of getting a longer cable and leaving the dvd drive attached.

That workaround won't work for me any longer because I was moving the drive and snapped my long IDE cable. ... cheap connectors need too much force...  My other IDE cable only reaches one drive or the other.  Can reach both only with the case off and the hard drive hanging.

Anyway, so now I'm back to this.  The system hangs during the entire boot process from bios post to loading the OS until 5-10 minutes I get kicked to a prompt.

Tried disabling the slave channel in the bios. No change.  Just updated everything this afternoon and had several good reboots while the dvd was attached.

What I'm seeing:

BIOS to OS loading starts (3min)
GRUB Loading stage1.5. (2min)
GRUB Loading, please wait... (1min)
Starting up.. (1min)
[LOGO displayed, 2-3min]
BusyBox v1.1.3 yada yada, type help
(initramfs)_

I did find a thread with a similar problem, but have no idea what or where they are talking about. Not sure what fstab does or where to find it.  Am I correct in thinking it is one of the first files loaded by the OS and mounts the known drives?
[http://ubuntuforums.org/showthread.php?t=404561](http://ubuntuforums.org/showthread.php?t=404561)

I'll reconnect my dvd drive temporarily and let the hard drive dangle to finish a good boot to gui so we can solve this once and for all.

---

### Post by kilroy423 on 2008-10-21
> Not sure what fstab does or where to find it.

fstab is located in /etc/fstab , it is a configuration file for mounting things(cdrom, hdd).  If you want to view yours just run from a terminal 

```
cat /etc/fstab

or to edit

sudo vim /etc/fstab

```

---

