---
title: "[IDEA] Track memory usage"
date: 2010-01-23
forum: Programming Talk
---

### Post by carlosgs91 on 2010-01-23
.

---

### Post by jpkotta on 2010-01-23
There is a mechanism in the kernel called the oom killer, which kills processes that are using "too much" memory when total free memory goes to zero.  But usually that never happens, because almost everyone uses swap, which uses your hard disk for memory.  Hard disks are orders of magnitude slower than memory, so that is the slow down you're seeing.  The solution is *not* to disable swap, but to get more memory.  There *might* be a way to limit memory to certain processes with the kernel, but I'm not sure.  I'd start looking for things like control groups.

Applications have no idea of how much memory there is.  They simply ask for whatever memory they need, and if they get denied, they either crash or show an error message.

So your options are: get more memory or kill some applications.  What I do is run htop and press 'M' to sort by memory usage.  Then I can kill the processes from htop (or just close them in the usual way).  You don't need to use htop; any decent process viewer will have the ability to sort by memory usage.

---

### Post by Can+~ on 2010-01-23
> it's not like a Windows freeze where you have to reboot your computer, in Ubuntu everything is still working fine but that application slow a lot your computer.

The computer slows down because the kernel starts a more aggressive swapping routine, sending a larger amount of pages to the HDD.

What you describe is the OOM killer (which was already mentioned by the above post). If you prefer your processes to be denied of memory and crash/error, then turn off [swappiness]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?") to a very low amount.

---

### Post by carlosgs91 on 2010-01-23
.

---

### Post by Can+~ on 2010-01-23
> **carlosgs91 said:**
> The major problem is when I suspend my laptop. When I "turn it on" again after being suspended, most of the times it takes about 3-5 minutes to work fine!!! and there're not specials process over there taking a lot of RAM or CPU usage.

I post a pic of my RAM and SWAP usage right now:

[http://img138.yfrog.com/img138/108/screenshot6v.png](http://img138.yfrog.com/img138/108/screenshot6v.png)

That's Adobe's Flash causing trouble, and seems like a common issue, a quick search in ubuntuforums yields a lot of info on the subject.

---

### Post by carlosgs91 on 2010-01-23
.

---

### Post by Can+~ on 2010-01-23
> **carlosgs91 said:**
> How do you know if it's Adobe's Flash or not? That graphic does not show any process!

I meant the process you named "npviewer.bin". Do a quick search and you'll find that plenty of people are in the same boat as you are.

---

### Post by d3v1150m471c on 2010-01-23
```

d3v11@d3v11m4ch1n3:~$ sysctl -q vm.swappiness && sysctl -q vm.vfs_cache_pressure && free -m
vm.swappiness = 10
vm.vfs_cache_pressure = 20
             total       used       free     shared    buffers     cached
Mem:          2894       1023       1870          0         36        694
-/+ buffers/cache:        292       2602
Swap:         8479          0       8479

```

Runs smoother than exlax

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2528  1492 ?        Ss   19:20   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   19:20   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   19:20   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   19:20   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   19:20   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   19:20   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        R<   19:20   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   19:20   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   19:20   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   19:20   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   19:20   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S<   19:20   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S<   19:20   0:00 [kintegrityd/0]
root        16  0.0  0.0      0     0 ?        S<   19:20   0:00 [kintegrityd/1]
root        17  0.0  0.0      0     0 ?        S<   19:20   0:00 [kblockd/0]
root        18  0.0  0.0      0     0 ?        S<   19:20   0:00 [kblockd/1]
root        19  0.0  0.0      0     0 ?        S<   19:20   0:00 [kacpid]
root        20  0.0  0.0      0     0 ?        S<   19:20   0:00 [kacpi_notify]
root        21  0.0  0.0      0     0 ?        S<   19:20   0:00 [kacpi_hotplug]
root        22  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata/0]
root        23  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata/1]
root        24  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata_aux]
root        25  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksuspend_usbd]
root        26  0.0  0.0      0     0 ?        S<   19:20   0:00 [khubd]
root        27  0.0  0.0      0     0 ?        S<   19:20   0:00 [kseriod]
root        28  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmmcd]
root        29  0.0  0.0      0     0 ?        S<   19:20   0:00 [bluetooth]
root        30  0.0  0.0      0     0 ?        S    19:20   0:00 [khungtaskd]
root        31  0.0  0.0      0     0 ?        S    19:20   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S    19:20   0:00 [pdflush]
root        33  0.0  0.0      0     0 ?        S<   19:20   0:00 [kswapd0]
root        34  0.0  0.0      0     0 ?        S<   19:20   0:00 [aio/0]
root        35  0.0  0.0      0     0 ?        S<   19:20   0:00 [aio/1]
root        36  0.0  0.0      0     0 ?        S<   19:20   0:00 [ecryptfs-kthr]
root        37  0.0  0.0      0     0 ?        S<   19:20   0:00 [crypto/0]
root        38  0.0  0.0      0     0 ?        S<   19:20   0:00 [crypto/1]
root        46  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_0]
root        47  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_1]
root        48  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_2]
root        49  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_3]
root        50  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_4]
root        51  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_5]
root        57  0.0  0.0      0     0 ?        S<   19:20   0:00 [kstriped]
root        58  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpathd/0]
root        59  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpathd/1]
root        60  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpath_handle]
root        61  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksnapd]
root        62  0.0  0.0      0     0 ?        S<   19:20   0:00 [kondemand/0]
root        63  0.0  0.0      0     0 ?        S<   19:20   0:00 [kondemand/1]
root        64  0.0  0.0      0     0 ?        S<   19:20   0:00 [kconservative]
root        65  0.0  0.0      0     0 ?        S<   19:20   0:00 [kconservative]
root        66  0.0  0.0      0     0 ?        S<   19:20   0:00 [krfcommd]
root       332  0.0  0.0      0     0 ?        S<   19:20   0:00 [i915/0]
root       336  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_6]
root       337  0.0  0.0      0     0 ?        S<   19:20   0:00 [usb-storage]
root       343  0.0  0.0      0     0 ?        S<   19:20   0:00 [i915/1]
root       352  0.0  0.0      0     0 ?        S<   19:20   0:00 [usbhid_resume]
root       428  0.0  0.0      0     0 ?        S<   19:20   0:00 [kjournald2]
root       491  0.0  0.0   3040   768 ?        S    19:20   0:00 upstart-udev-br
root       493  0.0  0.0   2752  1176 ?        S<s  19:20   0:00 udevd --daemon
root       670  0.0  0.0   2748  1180 ?        S<   19:20   0:00 udevd --daemon
root       671  0.0  0.0   2748  1164 ?        S<   19:20   0:00 udevd --daemon
root       717  0.0  0.0      0     0 ?        S<   19:20   0:00 [kpsmoused]
root       764  0.0  0.0      0     0 ?        S<   19:20   0:00 [phy0]
root       780  0.0  0.0      0     0 ?        S<   19:20   0:00 [hd-audio0]
root       944  0.0  0.0   1848   548 ?        Ss   19:20   0:00 dd bs=1 if=/pro
102        947  0.0  0.0   3040  1448 ?        Ss   19:20   0:00 dbus-daemon --s
107        971  0.0  0.1   6252  4240 ?        Ss   19:20   0:00 hald --daemon=y
root       973  0.0  0.1   8588  3312 ?        Ss   19:20   0:00 gdm-binary
syslog     980  0.0  0.0  34440  1804 ?        Sl   19:20   0:00 rsyslogd -c4
avahi      999  0.0  0.0   2820  1508 ?        Ss   19:20   0:00 avahi-daemon: r
avahi     1002  0.0  0.0   2820   532 ?        Ss   19:20   0:00 avahi-daemon: c
root      1033  0.0  0.1  18576  3808 ?        Ssl  19:20   0:00 NetworkManager
root      1038  0.0  0.0   3900  2116 ?        S    19:20   0:00 /usr/sbin/modem
root      1074  0.0  0.1  20496  2992 ?        Ssl  19:20   0:00 /usr/sbin/conso
root      1104  0.0  0.0   1700   548 tty4     Ss+  19:20   0:00 /sbin/getty -8
root      1107  0.0  0.0   1700   544 tty5     Ss+  19:20   0:00 /sbin/getty -8
root      1170  0.0  0.0   3336  1212 ?        S    19:20   0:00 hald-runner
root      1177  0.0  0.0   1700   544 tty2     Ss+  19:20   0:00 /sbin/getty -8
root      1178  0.0  0.0   1700   544 tty3     Ss+  19:20   0:00 /sbin/getty -8
root      1180  0.0  0.0   1700   548 tty6     Ss+  19:20   0:00 /sbin/getty -8
root      1181  0.0  0.0   1972   860 ?        Ss   19:20   0:00 acpid -c /etc/a
daemon    1193  0.0  0.0   1960   420 ?        Ss   19:20   0:00 atd
root      1194  0.0  0.0   2088   864 ?        Ss   19:20   0:00 cron
clamav    1312  0.0  0.0   3112  1056 ?        Ss   19:20   0:00 /usr/bin/freshc
kernoops  1327  0.0  0.0   3340   916 ?        Ss   19:20   0:00 /usr/sbin/kerne
root      1344  0.0  0.1   8520  3272 ?        S    19:20   0:00 /usr/lib/gdm/gd
root      1345  9.6  1.2  83184 37876 tty7     Ds+  19:20   5:45 /usr/bin/X :0 -
root      1373  0.0  0.0   6684  2348 ?        Ss   19:20   0:00 /usr/sbin/cupsd
root      1521  0.1  0.0   4260  2412 ?        SNs  19:20   0:06 /usr/sbin/prelo
root      1571  0.0  0.0   3408  1116 ?        S    19:20   0:00 /usr/lib/hal/ha
root      1573  0.0  0.0   4780  2208 ?        S    19:20   0:00 /sbin/wpa_suppl
root      1574  0.0  0.0   3408  1116 ?        S    19:20   0:00 /usr/lib/hal/ha
root      1585  0.0  0.0   3404  1140 ?        S    19:20   0:00 /usr/lib/hal/ha
root      1607  0.0  0.0   2140   944 ?        S    19:20   0:00 /sbin/dhclient
root      1620  0.0  0.0   3412  1148 ?        S    19:20   0:00 hald-addon-inpu
root      1621  0.0  0.0   3412  1140 ?        S    19:20   0:00 hald-addon-stor
root      1622  0.0  0.0   3412  1140 ?        S    19:20   0:00 hald-addon-stor
root      1623  0.0  0.0   3420  1128 ?        S    19:20   0:00 /usr/lib/hal/ha
107       1625  0.0  0.0   3256  1120 ?        S    19:20   0:00 hald-addon-acpi
root      1660  0.0  0.0   1700   540 tty1     Ss+  19:20   0:00 /sbin/getty -8
root      1673  0.0  0.0   8628  2932 ?        S    19:20   0:00 /usr/lib/gdm/gd
d3v11     1761  0.0  0.2  25764  6640 ?        Ssl  19:20   0:00 gnome-session
d3v11     1909  0.0  0.0   4704   612 ?        Ss   19:21   0:00 /usr/bin/ssh-ag
d3v11     1912  0.0  0.0   3380   716 ?        S    19:21   0:00 /usr/bin/dbus-l
d3v11     1913  0.0  0.0   2972  1304 ?        Ss   19:21   0:00 /bin/dbus-daemo
d3v11     1922  1.2  0.1 159652  4884 ?        Ssl  19:21   0:43 /usr/bin/pulsea
d3v11     2842  0.0  0.0  10628  2912 ?        S    19:21   0:00 /usr/lib/pulsea
d3v11     2844  0.0  0.1   7636  4636 ?        S    19:21   0:00 /usr/lib/libgco
root      2849  0.0  0.0   5188  2692 ?        S    19:21   0:00 /usr/lib/device
d3v11     2890  0.0  0.1  41896  3028 ?        Sl   19:21   0:00 gnome-keyring-d
d3v11     2893  0.0  0.2  96688  8764 ?        Ssl  19:21   0:01 /usr/lib/gnome-
d3v11     2895  0.0  0.2  22828  7412 ?        Ss   19:21   0:00 seahorse-daemon
d3v11     2899  0.0  0.0   5740  2160 ?        S    19:21   0:00 /usr/lib/gvfs/g
d3v11     2906  0.0  0.0  29788  2484 ?        Ssl  19:21   0:00 /usr/lib/gvfs//
d3v11     2918  0.0  0.3  20100  9668 ?        S    19:21   0:02 /usr/lib/notify
d3v11     2919  0.0  0.0   1748   556 ?        S    19:21   0:00 /bin/sh /usr/bi
d3v11     2934  0.0  0.0   3164   912 ?        S    19:21   0:00 syndaemon -i 0.
d3v11     2994  2.1  1.2 127460 36632 ?        S    19:21   1:17 /usr/bin/compiz
d3v11     2995  0.1  0.6  43164 19724 ?        S    19:21   0:05 gnome-panel
d3v11     2998  0.1  1.1  98724 32640 ?        S    19:21   0:04 nautilus
d3v11     3002  0.1  0.3  19604  9284 ?        S    19:21   0:03 emerald --repla
d3v11     3004  0.0  0.4  33996 12188 ?        S    19:21   0:00 nm-applet --sm-
d3v11     3005  0.0  0.3  94788 10992 ?        S    19:21   0:00 gnome-volume-co
d3v11     3006  0.0  0.2  17528  7084 ?        S    19:21   0:00 gnome-power-man
d3v11     3007  0.0  0.3  68728 11472 ?        Sl   19:21   0:00 /usr/lib/evolut
d3v11     3011  0.0  0.2  17380  6504 ?        S    19:21   0:00 /usr/lib/gnome-
d3v11     3012  0.0  0.1  16924  5720 ?        S    19:21   0:00 /usr/lib/policy
root      3016  0.0  0.1   5952  3496 ?        S    19:21   0:00 /usr/lib/policy
root      3018  0.0  0.0   5016  2788 ?        S    19:21   0:00 /usr/lib/device
root      3019  0.0  0.0   4820   752 ?        S    19:21   0:00 devkit-disks-da
d3v11     3022  0.0  0.1  41660  3488 ?        Ssl  19:21   0:00 /usr/lib/bonobo
d3v11     3024  0.0  0.0  17676  2844 ?        Ss   19:21   0:00 gnome-screensav
d3v11     3027  0.0  0.0  14552  2944 ?        S    19:21   0:00 /usr/lib/gvfs/g
d3v11     3034  0.8  0.2  22980  8620 ?        S    19:21   0:29 /usr/lib/gnome-
d3v11     3036  0.0  0.0   6360  2800 ?        S    19:21   0:00 /usr/lib/gvfs/g
d3v11     3038  0.0  0.0   6592  2212 ?        S    19:21   0:00 /usr/lib/gvfs/g
d3v11     3049  0.0  0.0   5740  2236 ?        S    19:21   0:00 /usr/lib/gvfs/g
d3v11     3571  0.1  1.2 110560 36948 ?        Sl   19:21   0:04 pidgin
d3v11     3628  0.0  0.3  44260 11184 ?        Sl   19:21   0:00 /usr/lib/evolut
d3v11     3632  0.0  0.2  62668  8520 ?        Sl   19:21   0:00 /usr/lib/evolut
d3v11     4407  0.0  0.0   5608  1832 ?        S    19:22   0:00 /usr/lib/gvfs/g
d3v11     4419  9.4  1.6 203088 49756 ?        Sl   19:22   5:30 totem /home/d3v
d3v11     7787  0.0  0.0   1748   528 ?        S    19:25   0:00 /bin/sh /usr/bi
d3v11     7799  0.0  0.0   1748   540 ?        S    19:25   0:00 /bin/sh /usr/li
d3v11     7803  6.1  3.2 301812 96740 ?        Sl   19:25   3:21 /usr/lib/swiftf
root     11609  0.0  0.0   2576   788 ?        Ss   19:29   0:00 /bin/dbus-daemo
root     11610  0.0  0.0   3380   708 ?        S    19:29   0:00 dbus-launch --a
d3v11    20427  0.2  0.4  38536 13768 ?        Sl   20:17   0:00 gnome-terminal
d3v11    20428  0.0  0.0   1900   708 ?        S    20:17   0:00 gnome-pty-helpe
d3v11    20429  0.0  0.1   6160  3448 pts/0    Ss   20:17   0:00 bash
d3v11    23270  0.0  0.0   2640  1020 pts/0    R+   20:20   0:00 ps -aux

```

---

### Post by dwhitney67 on 2010-01-24
> **carlosgs91 said:**
> Ok, I don't have this problem a lot of times and I have 4GB of RAM, that should be more than enough. I can try changing the use of my SWAP (I have only 666mb of SWAP)

For 2GB or more of RAM, I believe it is recommended that you have 2GB of swap space (on the HDD).  Even though you have 4GB of RAM, the 2GB of swap should be sufficient.

You are operating with 666MB of swap... ouch!

You can read more about it here:
[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)

---

### Post by Can+~ on 2010-01-24
From the page that dwhitney posted:

> A note about Desktop and Laptop

If you are going to suspend to disk, then you need swap space more than actual RAM. For example, my laptop has 1GB RAM and swap is setup to 2GB. This only applies to Laptop or desktop but not to servers. 

---

### Post by carlosgs91 on 2010-01-24
.

---

### Post by Sylslay on 2010-01-24
I use 1gb memory and 486 mb swap speace. 
Swap is use some time but no more than 60mb, when loads programs run at once.

for memory usege see in system monitor, 

or in terminal:

free
top

commadns

---

### Post by carlosgs91 on 2010-01-25
.

---

