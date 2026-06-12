---
title: "[SOLVED] Won't shut down"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-03
Hello.

My computer won't restart or shut down when I press the shutdown/restart buttons.
It only logs off.

 ```


Sep  3 00:05:36 ajzimmerman-desktop -- MARK --
Sep  3 00:18:41 ajzimmerman-desktop kernel: [ 4428.369139] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:41 ajzimmerman-desktop kernel: [ 4428.369152] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:41 ajzimmerman-desktop kernel: [ 4428.369160] end_request: I/O error, dev sr0, sector 0
Sep  3 00:18:41 ajzimmerman-desktop kernel: [ 4428.371318] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:41 ajzimmerman-desktop kernel: [ 4428.371322] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:41 ajzimmerman-desktop kernel: [ 4428.371327] end_request: I/O error, dev sr0, sector 0
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.479225] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.479236] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.479245] end_request: I/O error, dev sr0, sector 0
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.480625] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.480631] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.480635] end_request: I/O error, dev sr0, sector 8
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.482015] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.482019] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.482024] end_request: I/O error, dev sr0, sector 0
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.494433] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.494445] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.494451] end_request: I/O error, dev sr0, sector 0
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.495843] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.495848] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.495852] end_request: I/O error, dev sr0, sector 8
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.497226] sr 3:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.497230] sr 3:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
Sep  3 00:18:47 ajzimmerman-desktop kernel: [ 4433.497235] end_request: I/O error, dev sr0, sector 0
Sep  3 00:45:36 ajzimmerman-desktop -- MARK --
Sep  3 01:05:36 ajzimmerman-desktop -- MARK --
Sep  3 01:11:29 ajzimmerman-desktop kernel: [ 7593.998221] printk: 4 messages suppressed.
Sep  3 01:11:30 ajzimmerman-desktop kernel: [ 7593.998236] gvfs-fuse-daemo[6393] general protection rip:7f2283ad0423 rsp:7fff8d6fade0 error:0
Sep  3 01:11:30 ajzimmerman-desktop shutdown[12406]: shutting down for system reboot
Sep  3 01:25:36 ajzimmerman-desktop -- MARK --
Sep  3 01:32:42 ajzimmerman-desktop kernel: [ 8865.581635] gvfs-fuse-daemo[12547] general protection rip:7f4b868e8423 rsp:7fff90511d40 error:0
Sep  3 01:32:42 ajzimmerman-desktop shutdown[14534]: shutting down for system reboot
Sep  3 01:33:07 ajzimmerman-desktop shutdown[14564]: shutting down for system reboot
Sep  3 01:33:27 ajzimmerman-desktop shutdown[14588]: shutting down for system halt
```I have no idea what is going on.

---

### Post by pmlxuser on 2008-09-03
try in the terminal

```

$sudo shutdown -r now

```
to restart
or
```

$sudo shutdown -h now

```
to shutdown and report what happens please

---

### Post by Elephantman5 on 2008-09-03
> **pmlxuser said:**
> try in the terminal

```

$sudo shutdown -r now

```to restart
or
```

$sudo shutdown -h now

```to shutdown and report what happens please

```
ajzimmerman@ajzimmerman-desktop:~$ sudo shutdown -r now

The system is going down for reboot NOW!desktop (pts/0) (Wed Sep  3 01:59:06 
shutdown: timeout opening/writing control channel /dev/initctl
init: timeout opening/writing control channel /dev/initctl
ajzimmerman@ajzimmerman-desktop:~$ 
```

```
ajzimmerman@ajzimmerman-desktop:~$ sudo shutdown -h now

The system is going down for system halt NOW!op (pts/0) (Wed Sep  3 02:00:16 
shutdown: timeout opening/writing control channel /dev/initctl
init: timeout opening/writing control channel /dev/initctl
ajzimmerman@ajzimmerman-desktop:~$ 


```

---

### Post by Elephantman5 on 2008-09-03
sudo reboot -f 
did it.

Then I tried it normally and it worked.
Wondering what the -f was, and why it happened in the first place. ('m assuming force)

---

### Post by pmlxuser on 2008-09-03
Great!

yeah -f means force

possibly another precess of shutdown did not complete well and maybe it locked some files for shutting down.

---

### Post by Elephantman5 on 2008-09-03
Thanks for the help.
It's a pleasure.

---

