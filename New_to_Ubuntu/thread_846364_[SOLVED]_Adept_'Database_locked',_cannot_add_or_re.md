---
title: "[SOLVED] Adept 'Database locked', cannot add or remove packages"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by penguinbreath on 2008-07-01
```
Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.
```

I get the above message when I try to open either Adept-updater or Adept-manager. I believe this problem happened after a crash with Adept. I rebooted and I am still having this problem.


top from terminal gives me this output:
```
top - 13:40:45 up 12 min,  1 user,  load average: 0.15, 0.36, 0.33
Tasks: 104 total,   2 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6%us,  2.0%sy,  0.0%ni, 90.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1035372k total,   718308k used,   317064k free,   107824k buffers
Swap:  3028212k total,        0k used,  3028212k free,   410264k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6089 *  20   0 33404  14m  11m R  2.0  1.4   0:00.50 konsole
 4927 root      20   0 36212  20m 4892 S  1.3  2.0   0:15.26 Xorg
 6106 *  20   0  2308 1108  852 R  0.7  0.1   0:00.04 top
 5798 *  20   0  157m  62m  24m S  0.3  6.1   0:34.68 firefox
    1 root      20   0  2844 1692  544 S  0.0  0.2   0:01.28 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  147 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  148 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  149 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1480 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd
 1482 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1503 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ata/0
 1510 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux
 2238 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 2240 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 2488 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kjournald
 2705 root      16  -4  2420  964  380 S  0.0  0.1   0:00.52 udevd
 3049 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
 3097 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 4484 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty
 4485 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty
 4489 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty
 4490 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty
 4492 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty
 4660 root      20   0  2456 1352  692 S  0.0  0.1   0:00.00 acpid
```




I have no idea what might be causing this, so any help would be greatly appreciated. :)

---

### Post by skatemyturf on 2008-07-01
hey iam having the same problem i have figured out that inmy case and most likely the same as yours that aptitude has been removed due to a crash.

---

### Post by ibuclaw on 2008-07-01
It will most likely be that the lock file is still present in the tmp folder. It shouldn't be too hard to spot, most of them are named as a **.lock** file.

try
```
find /tmp -type f -iname adept -print
```
In the terminal to see if it comes up with anything.

If you get nothing, try /var instead.

Then rm the file.

Regards
Iain

---

### Post by penguinbreath on 2008-07-01
> hey iam having the same problem i have figured out that inmy case and most likely the same as yours that aptitude has been removed due to a crash.

I typed **aptitude -h** in the terminal, and I got a help file. So I do not think aptitude is missing in my case. :confused:

---

### Post by penguinbreath on 2008-07-01
> **tinivole said:**
> It will most likely be that the lock file is still present in the tmp folder. It shouldn't be too hard to spot, most of them are named as a **.lock** file.

try
```
find /tmp -type f -iname adept -print
```
In the terminal to see if it comes up with anything.

If you get nothing, try /var instead.

Then rm the file.

Regards
Iain

I tried:
```
sudo find /tmp -type f -iname adept -print
```
```
sudo find /var -type f -iname adept -print

```
However I do not get any results. Any ideas?

---

### Post by penguinbreath on 2008-07-01
Typed in ```
sudo dpkg --configure -a
``` in terminal and my problem is gone.

Thanks everyone!

---

