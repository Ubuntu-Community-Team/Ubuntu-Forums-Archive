---
title: "Bas command needed?"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by nnjond on 2012-03-02
Hi,

Can't shift this problem with a reboot; Any advice please?

Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove any packages.

---

### Post by whatthefunk on 2012-03-02
You have more than one package managing system open, so you need to close extra ones down before you install or remove any packages.  In a terminal, type "top" to see what programs are currently running.  To kill them from top, press "k" and then enter the PID.

---

### Post by enjoijesus94 on 2012-03-02
> **whatthefunk said:**
> You have more than one package managing system open, so you need to close extra ones down before you install or remove any packages.  In a terminal, type "top" to see what programs are currently running.  To kill them from top, press "k" and then enter the PID.

Or 
```
killall Applicationname
```

Put Name After Killall

---

### Post by nnjond on 2012-03-02
Thanks for your help. There are dozens of pids.

```
k 2043[CODE]

for instance returns

[CODE]Kill PID 2043 with signal [15]: 

```

Which is largely meaningless to me, and I can't recognise any package managers from the list. Can You?

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
 2259 nnjond    20   0  228m  78m  18m S 14.5  8.3   0:47.07 chromium-
 2209 nnjond    20   0  208m  75m  16m S  6.0  8.1   0:06.17 chromium-
 1160 root      20   0  114m  44m  16m S  1.3  4.8   0:51.96 Xorg     
 1987 nnjond    20   0  109m  21m  17m S  1.3  2.3   0:11.58 konsole  
 2203 nnjond    20   0  163m  34m  17m S  1.3  3.7   0:04.16 chromium-
 1454 nnjond    20   0  338m  33m  14m S  0.7  3.5   0:23.80 plasma-de
 2061 nnjond    20   0  479m  74m  26m S  0.7  7.9   0:17.25 chromium-
 2146 nnjond    20   0  145m  19m  12m S  0.7  2.1   0:00.40 chromium-
 1315 root      20   0  6320  260  184 S  0.3  0.0   0:01.01 udisks-da
 1429 nnjond    20   0  163m  11m 7012 S  0.3  1.2   0:16.86 kwin     
 1534 nnjond    39  19 45936 6852 1148 S  0.3  0.7   0:05.41 virtuoso-
 1543 nnjond    20   0 63840 2712 2304 S  0.3  0.3   0:00.25 kaccess  
 2043 nnjond    20   0  2820 1064  848 R  0.3  0.1   0:04.74 top      
 2197 nnjond    20   0  222m  85m  20m S  0.3  9.2   0:09.69 chromium-
 2215 nnjond    20   0  287m 150m  19m S  0.3 16.0   0:40.84 chromium-
    1 root      20   0  3320  764  368 S  0.0  0.1   0:00.53 init     
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd 
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.59 ksoftirqd
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset   
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper  
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns    
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.03 sync_supe
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-defau
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrit
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd  
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff  
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.03 khubd    
   16 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md       
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtask
   20 root      20   0     0    0    0 S  0.0  0.0   0:02.06 kswapd0  
   21 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd     
   22 root      39  19     0    0    0 S  0.0  0.0   0:00.00 khugepage
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 fsnotify_
   24 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-
   25 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 crypto   
   33 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kthrotld 
  156 root      20   0     0    0    0 S  0.0  0.0   0:00.52 scsi_eh_0
  164 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
  168 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
  181 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3
  184 root      20   0     0    0    0 S  0.0  0.0   
```

---

### Post by whatthefunk on 2012-03-02
> **nnjond said:**
> Thanks for your help. There are dozens of pids.

```
k 2043[CODE]

for instance returns

[CODE]Kill PID 2043 with signal [15]: 

```

From here, you type "y" and hit enter.

When did you get the original error message about package managers being open?  What were you doing?  I didnt see anything that would have access to package management,

---

### Post by enjoijesus94 on 2012-03-02
> **whatthefunk said:**
> From here, you type "y" and hit enter.

When did you get the original error message about package managers being open?  What were you doing?  I didnt see anything that would have access to package management,

Never Seen That Error Before??????

---

### Post by nnjond on 2012-03-02
Thanks again.

I turn on my pc; I'm alerted to updates. I click on it and muon package manager opens. The process is interrupted by the above message.

I don't know how any other package managers can being open?

---

### Post by whatthefunk on 2012-03-02
Seems that this is a known bug:
[https://bugs.kde.org/show_bug.cgi?id=284962](https://bugs.kde.org/show_bug.cgi?id=284962)

Comments in the bug report suggest this may work from a terminal:

```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

---

### Post by nnjond on 2012-03-02
Solved

Thanks

---

