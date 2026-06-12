---
title: "NFS mount fails - portmap problem?"
date: 2016-01-19
forum: New to Ubuntu
---

### Post by mark_lewis2 on 2016-01-19
Situation:

I am moving a 14.04 server (previously upgraded from 12.04) from a VirtualBox VM to it's own dedicated hardware.  On the new box, I've made a brand new install of 14.04 DESKTOP, with the necessary server packages installed.  Among other things, I'm using backuppc (on my Ubuntu server), as a backup solution for my home network (4 Win based PCs) using a NFS share from my NAS (Netgear ReadyNAS NV+, aging but trustworthy) as the backup store. All this has been operating quite stably on the VM version of my server for weeks.  Installing and moving configuration to the new hardware has been pretty straight-forward until setting up the NFS mount of the backup store.  What works on my old VM doesn't seem to work on the new dedicated box.  All other network related stuff (Apache2, CIFS shares) have worked without problems.

One odd thing.  After a full day of trying to get the NFS mount working and pouring over web pages refering to that problem, after a reboot, the mount suddenly was working.  Thinking that I had overcome that hurdle, but not understanding excatly how, I wen't on to the next task.  A few hours later, just as suddenly, the mount was no longer working.  I am racking my brains for what of the seemingly unrelated things I was doing could have affected the mount.  Not coming up with anythiing, so...

Here are the relevant parts of my configuration:

/etc/fstab fragment from VM version
```
192.168.1.97:/c/backups /var/lib/backuppc nfs noatime,async,hard,nfsvers=3,tcp,intr,rsize=8192,wsize=8192 0 0
```

/etc/fstab fragment from standalone version
```
192.186.1.97:/c/backups /var/lib/backuppc nfs noatime,async,hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192 0 0
```

Trace of verbose mount VM version (succeeds)
```
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "192.168.1.97:/c/backups"
mount: node:  "/var/lib/backuppc"
mount: types: "nfs"
mount: opts:  "noatime,async,hard,nfsvers=3,tcp,intr,rsize=8192,wsize=8192"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "192.168.1.97:/c/backups"
mount: external mount: argv[2] = "/var/lib/backuppc"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,noatime,hard,nfsvers=3,tcp,intr,rsize=8192,wsize=8192"
mount.nfs: trying 192.168.1.97 prog 100003 vers 3 prot TCP port 2049
mount.nfs: trying 192.168.1.97 prog 100005 vers 3 prot TCP port 1988
mount.nfs: timeout set for Tue Jan 19 12:34:12 2016
mount.nfs: trying text-based options 'hard,nfsvers=3,tcp,intr,rsize=8192,wsize=8192,addr=192.168.1.97'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: prog 100005, trying vers=3, prot=6
```

Trace of verbose mount standalone version (fails, trace truncated)
```
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "192.186.1.97:/c/backups"
mount: node:  "/var/lib/backuppc"
mount: types: "nfs"
mount: opts:  "noatime,async,hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "192.186.1.97:/c/backups"
mount: external mount: argv[2] = "/var/lib/backuppc"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,noatime,hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192"
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: portmap query failed: RPC: Unable to receive
mount.nfs: Connection timed out
mount.nfs: timeout set for Tue Jan 19 12:48:13 2016
mount.nfs: trying text-based options 'hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192,addr=192.186.1.97'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192,addr=192.186.1.97'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192,addr=192.186.1.97'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192,addr=192.186.1.97'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'hard,tcp,nfsvers=3,intr,rsize=8192,wsize=8192,addr=192.186.1.97'
mount.nfs: prog 100003, trying vers=3, prot=6
<etc>
```

Note that the succeeding trace shows no portmap query failure and does move on to a different prog before the mount succeeds.  This seems like the most fruitful point of inquiry, but my google searches haven't turned up anyway to find out more about what is going on.  Doesn't seem to have been a problem for anyone else.

rpcinfo -p of NAS
```

   program vers proto   port  service
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100011    1   udp    955  rquotad
    100011    2   udp    955  rquotad
    100011    1   tcp    958  rquotad
    100011    2   tcp    958  rquotad
    100024    1   udp  32765  status
    100024    1   tcp  32765  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp   1024  mountd
    100005    1   tcp   1988  mountd
    100005    2   udp   1024  mountd
    100005    2   tcp   1988  mountd
    100005    3   udp   1024  mountd
    100005    3   tcp   1988  mountd
    100021    1   udp   1026  nlockmgr
    100021    3   udp   1026  nlockmgr
    100021    4   udp   1026  nlockmgr
    100021    1   tcp   3476  nlockmgr
    100021    3   tcp   3476  nlockmgr
    100021    4   tcp   3476  nlockmgr
```

What else would be useful to see?

---

### Post by cariboo on 2016-01-19
Linux doesn't use drive letters, instead of c use /dev/sda1, or whatever your partition is labelled.

---

### Post by steeldriver on 2016-01-19
cariboo it's a network filesystem - the /c designation seems to be what Netgear uses for their NAS exports (it's the same on my even older sparc-based readynas device) i.e.

```

$ sudo showmount -e 192.168.1.127
Export list for 192.168.1.127:
/c/home   192.168.1.0/24
/c/media  192.168.1.0/24
/c/public 192.168.1.0/24
/c/backup 192.168.1.0/24

```

---

### Post by cariboo on 2016-01-20
> **steeldriver said:**
> cariboo it's a network filesystem - the /c designation seems to be what Netgear uses for their NAS exports (it's the same on my even older sparc-based readynas device) i.e.

```

$ sudo showmount -e 192.168.1.127
Export list for 192.168.1.127:
/c/home   192.168.1.0/24
/c/media  192.168.1.0/24
/c/public 192.168.1.0/24
/c/backup 192.168.1.0/24

```

DIdn't know that, thanks for the info.

---

