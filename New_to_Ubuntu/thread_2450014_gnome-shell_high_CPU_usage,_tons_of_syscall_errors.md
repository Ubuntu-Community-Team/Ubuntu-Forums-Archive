---
title: "gnome-shell high CPU usage, *tons* of syscall errors"
date: 2020-09-05
forum: New to Ubuntu
---

### Post by cdef on 2020-09-05
Hi there,

Prelude - This is my first full Ubuntu installation on my laptop. I'm comfortable in the shell, but am not the most well versed in debugging installation and driver issues.

Problems (tl;dr): 
[LIST=1]
[*]the gnome-shell process has extremely high CPU usage (>40% when moving the mouse, >20% when typing, totally fine when idle) 
[*]the gnome-shell process triggers a ton of errors when making the recvmsg syscall. 
[*]moving my mouse around leaves stuttering visual artifacts which disappear when idle. 
[/LIST]

I'm fairly certain these are all related, but I'm not sure how. If anyone has any ideas how to solve this problem, I'd be happy to try them out. 

Things I have tried that haven't worked:
[LIST]
[*]Refreshing the shell with Alt-F2 R successfully refreshes, but does not fix the problem. 
[*]Running ubuntu-drivers autoinstall does not work, there are no drivers available to install. 
[/LIST]

Below is the output of various commands for more context on this issue. Sorry if it's too much output, just wanted to give as much as possible.

**=== SYSTEM INFORMATION ===**

** inxi -F**
```

System:
  Host: laptop1 Kernel: 5.4.0-45-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Convertible System: Dell product: Inspiron 7573 v: N/A 
  serial: <superuser/root required> 
  Mobo: Dell model: 0GYWGJ v: A00 serial: <superuser/root required> 
  UEFI: Dell v: 1.13.1 date: 12/10/2018 
Battery:
  ID-1: BAT0 charge: 21.9 Wh condition: 21.9/42.0 Wh (52%) 
CPU:
  Topology: Quad Core model: Intel Core i7-8550U bits: 64 type: MT MCP 
  L2 cache: 8192 KiB 
  Speed: 800 MHz min/max: 400/4000 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 5: 800 6: 800 7: 800 8: 800 
Graphics:
  Device-1: Intel UHD Graphics 620 driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2) v: 4.6 Mesa 20.0.8 
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-45-generic 
Network:
  Device-1: Intel Wireless 7265 driver: iwlwifi 
  IF: wlp1s0 state: up mac: c0:b6:f9:f5:17:cf 
Drives:
  Local Storage: total: 476.94 GiB used: 210.90 GiB (44.2%) 
  ID-1: /dev/sda vendor: SK Hynix model: SC311 SATA 512GB size: 476.94 GiB 
RAID:
  Hardware-1: Intel 82801 Mobile SATA Controller [RAID mode] driver: ahci 
Partition:
  ID-1: / size: 467.96 GiB used: 210.89 GiB (45.1%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 40.0 C mobo: 35.0 C sodimm: 37.0 C 
  Fan Speeds (RPM): cpu: 0 
Info:
  Processes: 266 Uptime: 49m Memory: 15.38 GiB used: 1.93 GiB (12.6%) 
  Shell: bash inxi: 3.0.38

```

**lspci -vvv**
```

00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07) (prog-if 00 [VGA controller])
    DeviceName:  Onboard IGD
    Subsystem: Dell UHD Graphics 620
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 142
    Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at f000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```




**=== EVIDENCE === **

**strace -c -p**  (60 seconds idle, not moving mouse or typing)
```

% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 35.93    0.035036          21      1639           poll
 29.82    0.029083           7      3686      3119 recvmsg
 10.36    0.010098          11       858        52 ioctl
 10.11    0.009857          16       599           writev
  4.69    0.004576           4      1074           mprotect
  3.03    0.002950           6       437           write
  2.61    0.002544          11       214        26 futex
  1.52    0.001484           7       198           read
  1.45    0.001417           3       390           getpid
  0.17    0.000168           6        25           munmap
  0.11    0.000104          13         8           getrusage
  0.08    0.000080           0       126           sendmsg
  0.06    0.000058           4        14           mmap
  0.02    0.000023           7         3           timerfd_create
  0.02    0.000019           6         3           timerfd_settime
  0.01    0.000008           4         2           openat
  0.01    0.000005           1         4           fstat
  0.00    0.000003           0         5           close
  0.00    0.000003           1         2           fcntl
  0.00    0.000000           0         1           restart_syscall
------ ----------- ----------- --------- --------- ----------------
100.00    0.097516                  9288      3197 total

```

**strace -c -p**  (60 seconds active, moving mouse around)
[I]Check the first line, 180k/230k of recvmsg syscalls were errors
Really not sure how to go about investigating the cause of this, nevermind fixing it[/I]
```

% time seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 28.29    0.644837           2    229797    185715 recvmsg
 25.61    0.583750           7     82802      4148 ioctl
 24.44    0.557121           5    107969           poll
  8.86    0.202057           4     44475           writev
  7.12    0.162312           2     54198           write
  2.63    0.059966           2     27082           getpid
  1.87    0.042654           2     17435           read
  0.58    0.013265          10      1230           munmap
  0.35    0.008074           4      1682           mprotect
  0.22    0.005049           8       588        30 futex
  0.01    0.000121         121         1           restart_syscall
  0.00    0.000107           0       300       250 stat
  0.00    0.000099           1        72           sendmsg
  0.00    0.000069           3        23           mmap
  0.00    0.000060          60         1           clone
  0.00    0.000050           2        18         7 openat
  0.00    0.000028           7         4           getrusage
  0.00    0.000022           1        16           fstat
  0.00    0.000021           1        16           close
  0.00    0.000011           2         5           recvfrom
  0.00    0.000010           1         6           fcntl
  0.00    0.000007           1         6           timerfd_create
  0.00    0.000004           0         6           timerfd_settime
  0.00    0.000001           0         3           lseek
  0.00    0.000000           0         1           madvise
  0.00    0.000000           0         1           fchmod
  0.00    0.000000           0         1           fchown
------ ----------- ----------- --------- --------- ----------------
100.00    2.279695                567738    190150 total

```

**top** output when active
```

top - 14:37:17 up 48 min,  1 user,  load average: 0.73, 0.78, 0.74
Tasks: 260 total,   1 running, 259 sleeping,   0 stopped,   0 zombie
%Cpu(s):  6.5 us,  1.6 sy,  0.0 ni, 90.7 id,  0.0 wa,  0.0 hi,  1.1 si,  0.0 st
MiB Mem :  15753.2 total,  11589.6 free,   1693.9 used,   2469.7 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.  13424.5 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND  
   8398 chris     20   0 4280820 277144 101932 S  45.4   1.7   2:30.62 gnome-s+ 
   8215 chris     20   0  861828  89080  55068 S  14.6   0.6   0:59.88 Xorg     
  10386 chris     20   0  977256  55588  40992 S   4.3   0.3   0:14.46 gnome-t+ 
    244 root     -51   0       0      0      0 S   2.3   0.0   0:23.87 irq/51-+ 
   8820 chris     20   0    7032   3932   3644 S   1.7   0.0   0:06.76 libinpu+ 
   8606 chris     20   0   27496  12160   5880 S   1.3   0.1   0:03.40 python3  
      1 root      20   0  169048  13064   8324 S   1.0   0.1   0:11.85 systemd  
    135 root      20   0       0      0      0 I   1.0   0.0   0:04.08 kworker+ 
  11683 chris     20   0 1143996  80328  48864 S   1.0   0.5   0:09.63 nautilus 
  11901 root      20   0       0      0      0 I   0.7   0.0   0:00.89 kworker+ 
     11 root      20   0       0      0      0 I   0.3   0.0   0:04.75 rcu_sch+ 
    544 root      20   0       0      0      0 I   0.3   0.0   0:00.28 kworker+ 
    747 root      20   0   81880   3716   3376 S   0.3   0.0   0:00.30 irqbala+ 
   7777 root      20   0       0      0      0 I   0.3   0.0   0:01.18 kworker+ 
   9950 chris     20   0 2453676 134664 103232 S   0.3   0.8   0:02.40 Web Con+ 
  11982 chris     20   0 2638492 198252 136880 S   0.3   1.2   0:05.01 Web Con+ 
  12126 root      20   0       0      0      0 I   0.3   0.0   0:00.27 kworker+

```

**Picture of mouse artifacts** on desktop.
They only appear when the mouse is moving, and disappear after a second of mouse inactivity.
[ATTACH=CONFIG]286886[/ATTACH]

---

