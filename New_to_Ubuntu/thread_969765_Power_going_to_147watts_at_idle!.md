---
title: "Power going to 147watts at idle!"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by meniscus on 2008-11-03
Hi,

I'm in a spot of bother. I just logged onto ubuntu again after a month of absence 2 days ago on my dual boot system. Im monitoring my temps the whole time with lm sensors and its telling me my cpu is running at 64 degrees! I bought a wattmeter yesterday thinking the readings from  lmsensors were corrupt and its reading 147 watts!

What is going on? Ive nothing running as it just starts up like this. When i boot into windows all temps are fine?

Confused and worried!
Meniscus

---

### Post by meniscus on 2008-11-03
Sorry I forgot to add..

The temperture only goes up to 62 degrees on my profile. My brothers profile is normal. Is there a process running on mine thats making temperature rise so much?

---

### Post by FrostyFlames on 2008-11-03
64C or 64F?
What CPU?
Is it overclocked at all?

---

### Post by meniscus on 2008-11-04
64C. No not overclocked at all. 

I killed  a process command named python running on my profile and temperature returned to normal! What is going on?

---

### Post by scheuri on 2008-11-04
Hi there...

Please tell us what temperature it is now (normal is what??).

Also post us the exact command you were killing, even better...show us an output of top and ps aux with the process that seems to be causing this problems.

Maybe that helps us to identify the process and what it is doing (and why it might be running this way).

Cheers
scheuri

---

### Post by meniscus on 2008-11-04
Ive been trying for 2 hours to pipe the output of top to a text file but to no avail! 

Basically every time i log on to my profile there is some process according to top that needs 99% of cpu usage 

The output line of top is 

PID  User      PR  NI   VIRT  RES   SHR  S  %CPU   %MEM  COMMAND
6081 meniscus  39  19  17312  14m   11m  R  99.2%  1.4  python 

When i type kill 6081 in another terminal window temps return to normal? Any clues?

---

### Post by wizard10000 on 2008-11-04
> **meniscus said:**
> Sorry I forgot to add..

The temperture only goes up to 62 degrees on my profile. My brothers profile is normal. Is there a process running on mine thats making temperature rise so much?

Most likely - that's the first place I'd look.

---

### Post by handydan918 on 2008-11-04
top is a dynamic readout. try ps aux instead.

---

### Post by meniscus on 2008-11-04
Thank god for ps aux. Its output is the following

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1956   676 ?        Ss   13:41   0:00 init [2]      
root         2  0.0  0.0      0     0 ?        SN   13:41   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    13:41   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   13:41   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   13:41   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   13:41   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   13:41   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   13:41   0:00 [kacpid]
root        10  0.0  0.0      0     0 ?        S<   13:41   0:00 [kacpi_notify]
root       102  0.0  0.0      0     0 ?        S<   13:41   0:00 [kseriod]
root       138  0.0  0.0      0     0 ?        S    13:41   0:00 [pdflush]
root       139  0.0  0.0      0     0 ?        S    13:41   0:00 [pdflush]
root       140  0.0  0.0      0     0 ?        S    13:41   0:00 [kswapd0]
root       141  0.0  0.0      0     0 ?        S<   13:41   0:00 [aio/0]
root      1755  0.0  0.0      0     0 ?        S<   13:41   0:00 [ata/0]
root      1757  0.0  0.0      0     0 ?        S<   13:41   0:00 [scsi_eh_0]
root      1758  0.0  0.0      0     0 ?        S<   13:41   0:00 [scsi_eh_1]
root      1775  0.0  0.0      0     0 ?        S<   13:41   0:00 [khubd]
root      1795  0.0  0.0      0     0 ?        S<   13:41   0:00 [khpsbpkt]
root      1825  0.0  0.0      0     0 ?        S    13:41   0:00 [knodemgrd_0]
root      1879  0.0  0.0      0     0 ?        S<   13:41   0:00 [kjournald]
root      2117  0.0  0.1   2636  1068 ?        S<s  13:41   0:00 /sbin/udevd --d
root      2833  0.0  0.0      0     0 ?        S<   13:41   0:00 [kpsmoused]
root      2879  0.0  0.0      0     0 ?        S<   13:41   0:00 [shpchpd]
root      3921  0.0  0.1   2200  1148 ?        Ss   13:41   0:00 /usr/sbin/acpid
root      3999  0.0  0.1   2656  1164 ?        Ss   13:41   0:00 /sbin/syslog-ng
105       4030  0.0  0.0   2180   860 ?        Ss   13:41   0:00 /usr/bin/dbus-d
114       4045  0.0  0.5   7072  5540 ?        Ss   13:41   0:01 /usr/sbin/hald
root      4046  0.0  0.1   2916  1036 ?        S    13:41   0:00 hald-runner
114       4052  0.0  0.0   2028   808 ?        S    13:41   0:00 /usr/lib/hal/ha
114       4055  0.0  0.0   2024   812 ?        S    13:41   0:00 /usr/lib/hal/ha
114       4069  0.0  0.0   2028   840 ?        S    13:41   0:00 /usr/lib/hal/ha
root      4089  0.0  1.0  13612 11012 ?        S    13:41   0:00 perl /usr/share
root      4114  0.0  0.1  11796  1800 ?        Ss   13:41   0:00 /usr/sbin/gdm
cupsys    4157  0.0  0.1   4536  1896 ?        Ss   13:41   0:00 /usr/sbin/cupsd
root      4176  0.0  0.0   4904   928 ?        Ss   13:41   0:00 /usr/sbin/hpiod
hplip     4179  0.0  0.4   9668  4860 ?        S    13:41   0:00 python /usr/sbi
116       4250  0.0  0.0   5396  1000 ?        Ss   13:41   0:00 /usr/sbin/exim4
root      4297  0.0  0.0   1740   552 ?        S    13:41   0:00 /usr/sbin/hddte
daemon    4341  0.0  0.0   1600   308 ?        Ss   13:41   0:00 /usr/sbin/uptim
root      4396  0.0  0.0   2072   752 ?        Ss   13:41   0:00 /usr/sbin/hcid
root      4402  0.0  0.0   1668   500 ?        Ss   13:41   0:00 /usr/sbin/sdpd
root      4410  0.0  0.0   1832   468 ?        Ss   13:41   0:00 /usr/bin/hidd -
root      4415  0.0  0.0      0     0 ?        S<   13:41   0:00 [krfcommd]
root      4429  0.0  0.0   1716   304 ?        Ss   13:41   0:00 /sbin/mdadm --m
daemon    4470  0.0  0.0   1852   424 ?        Ss   13:41   0:00 /usr/sbin/atd
root      4489  0.0  0.0   2192   864 ?        Ss   13:41   0:00 /usr/sbin/cron
dhcp      4534  0.0  0.0   2400   652 ?        S<s  13:41   0:00 dhclient3 -pf /
root      4542  0.0  0.2   4640  2104 ?        S    13:41   0:00 /usr/sbin/apach
www-data  4543  0.0  0.0   4640   916 ?        S    13:41   0:00 /usr/sbin/apach
www-data  4544  0.0  0.0   4640   916 ?        S    13:41   0:00 /usr/sbin/apach
www-data  4545  0.0  0.0   4640   916 ?        S    13:41   0:00 /usr/sbin/apach
www-data  4546  0.0  0.0   4640   916 ?        S    13:41   0:00 /usr/sbin/apach
www-data  4549  0.0  0.0   4640   916 ?        S    13:41   0:00 /usr/sbin/apach
root      4615  0.0  0.0   1600   508 tty1     Ss+  13:41   0:00 /sbin/getty 384
root      4616  0.0  0.0   1600   508 tty2     Ss+  13:41   0:00 /sbin/getty 384
root      4617  0.0  0.0   1596   500 tty3     Ss+  13:41   0:00 /sbin/getty 384
root      4618  0.0  0.0   1596   504 tty4     Ss+  13:41   0:00 /sbin/getty 384
root      4619  0.0  0.0   1596   504 tty5     Ss+  13:41   0:00 /sbin/getty 384
root      4620  0.0  0.0   1596   504 tty6     Ss+  13:41   0:00 /sbin/getty 384
root      7916  0.0  0.2  12152  2612 ?        S    14:22   0:00 /usr/sbin/gdm
root      7921  4.8  1.2  18524 12924 tty7     Ss+  14:22   0:03 /usr/X11R6/bin/
meniscus   7962  0.4  0.9  20616 10332 ?        Ss   14:23   0:00 x-session-manag
meniscus   8017  0.0  0.0   4484   732 ?        Ss   14:23   0:00 /usr/bin/ssh-ag
meniscus   8018  0.0  0.0   4480   724 ?        Ss   14:23   0:00 /usr/bin/ssh-ag
meniscus   8021  0.0  0.0   2528   620 ?        S    14:23   0:00 /usr/bin/dbus-l
meniscus   8022  0.0  0.0   2180   944 ?        Ss   14:23   0:00 /usr/bin/dbus-d
meniscus   8024  0.5  0.3   6060  3536 ?        S    14:23   0:00 /usr/lib/libgco
meniscus   8027  0.0  0.0   2588   772 ?        S    14:23   0:00 /usr/bin/gnome-
meniscus   8030  0.3  0.9  28476  9548 ?        Sl   14:23   0:00 /usr/lib/contro
meniscus   8039  0.0  0.0   1656   472 ?        Ss   14:23   0:00 /bin/sh -c /usr
meniscus   8040  0.1  0.3   4972  3436 ?        S    14:23   0:00 /usr/bin/esd -t
meniscus   8047  0.9  0.8  14864  8320 ?        Ss   14:23   0:00 /usr/bin/metaci
meniscus   8052  2.1  1.5  37084 15548 ?        Ss   14:23   0:00 gnome-panel --s
meniscus   8054  1.7  1.6  72264 16732 ?        Ss   14:23   0:00 nautilus --no-d
meniscus   8058  0.2  0.2  39484  3096 ?        Ssl  14:23   0:00 /usr/lib/bonobo
meniscus   8062  0.0  0.3   8232  3288 ?        S    14:23   0:00 /usr/lib/gnome-
meniscus   8065  0.0  0.5  18292  5376 ?        Ss   14:23   0:00 gnome-volume-ma
meniscus   8073  0.1  0.7  18728  7656 ?        Ss   14:23   0:00 update-notifier
meniscus   8081  0.2  0.9  67184  9928 ?        Ssl  14:23   0:00 /usr/lib/evolut
meniscus   8085  0.0  0.4  12224  5084 ?        Ss   14:23   0:00 bt-applet --sm-
meniscus   8092  0.1  0.7  39148  8268 ?        Ss   14:23   0:00 gnome-cups-icon
meniscus   8096  0.0  0.6  27472  6788 ?        Ss   14:23   0:00 gnome-power-man
meniscus   8101  0.1  0.6  65236  6412 ?        Sl   14:23   0:00 /usr/lib/evolut
meniscus   8115  0.1  0.8  60376  8492 ?        S    14:23   0:00 /usr/lib/gnome-
meniscus   8146  0.5  1.0  30292 11384 ?        S    14:23   0:00 /usr/lib/gnome-
meniscus   8150  0.0  0.0   2504   936 ?        S    14:23   0:00 /usr/lib/nautil
meniscus   8153 88.6  1.4  17312 14632 ?        RN   14:23   0:35 python /usr/lib
meniscus   8177  0.2  0.2   5320  2316 ?        S    14:23   0:00 xscreensaver -n
meniscus   8202  9.2  1.3  49412 14372 ?        Rl   14:23   0:00 gnome-terminal
meniscus   8205  0.0  0.0   2504   804 ?        S    14:23   0:00 gnome-pty-helpe
meniscus   8206  0.2  0.1   4444  2008 pts/0    Ss   14:23   0:00 bash
meniscus   8215  0.0  0.0   2472   984 pts/0    R+   14:24   0:00 ps aux

```

---

### Post by JohnFH on 2008-11-04
It's not clear from that output, what the process is doing.  We would need to get the full command of the process.  

You can investigate the process by doing things like inspecting the open files (lsof -p 8153), or having a look in the process directory (/proc/8153).  It might also help to have a look at the process tree to see the process dependencies (pstree).

---

### Post by meniscus on 2008-11-04
Here is everything

open files
```

OMMAND  PID    USER   FD   TYPE DEVICE    SIZE    NODE NAME
python  5292 meniscus  cwd    DIR    3,2    4096 3883010 /home/meniscus
python  5292 meniscus  rtd    DIR    3,2    4096       2 /
python  5292 meniscus  txt    REG    3,2 1019680  410075 /usr/bin/python2.4
python  5292 meniscus  mem    REG    0,0               0 [heap] (stat: No such file or directory)
python  5292 meniscus  mem    REG    3,2 9919727 2212192 /var/cache/apt/pkgcache.bin
python  5292 meniscus  mem    REG    3,2   40208  934006 /lib/libgcc_s.so.1
python  5292 meniscus  mem    REG    3,2  888612  416789 /usr/lib/libstdc++.so.6.0.8
python  5292 meniscus  mem    REG    3,2  852480  413018 /usr/lib/libapt-pkg-libc6.4-6.so.3.51.0
python  5292 meniscus  mem    REG    3,2  133932  413023 /usr/lib/python2.4/site-packages/apt_pkg.so
python  5292 meniscus  mem    REG    3,2   25460  410931 /usr/lib/gconv/gconv-modules.cache
python  5292 meniscus  mem    REG    3,2  208336  639817 /usr/lib/locale/en_IE.utf8/LC_CTYPE
python  5292 meniscus  mem    REG    3,2 1248904  933974 /lib/tls/i686/cmov/libc-2.4.so
python  5292 meniscus  mem    REG    3,2  149284  933978 /lib/tls/i686/cmov/libm-2.4.so
python  5292 meniscus  mem    REG    3,2    9652  934172 /lib/tls/i686/cmov/libutil-2.4.so
python  5292 meniscus  mem    REG    3,2    9640  933977 /lib/tls/i686/cmov/libdl-2.4.so
python  5292 meniscus  mem    REG    3,2   95056  933988 /lib/tls/i686/cmov/libpthread-2.4.so
python  5292 meniscus  mem    REG    3,2   20848  410570 /usr/lib/python2.4/lib-dynload/struct.so
python  5292 meniscus  mem    REG    3,2   15656  414314 /usr/lib/python2.4/lib-dynload/_locale.so
python  5292 meniscus  mem    REG    3,2   21480  410569 /usr/lib/python2.4/lib-dynload/strop.so
python  5292 meniscus  mem    REG    3,2  105112  934075 /lib/ld-2.4.so
python  5292 meniscus    0r   CHR    1,3            4732 /dev/null
python  5292 meniscus    1w   CHR    1,3            4732 /dev/null
python  5292 meniscus    2w  FIFO    0,5           14361 pipe
```

Contents of proc

```
attr     cwd      fd    mounts      oom_score  smaps  status
auxv     environ  maps  mountstats  root       stat   task
cmdline  exe      mem   oom_adj     seccomp    statm  wchan

```


pstree

```
init&#9472;&#9516;&#9472;acpid
     &#9500;&#9472;apache&#9472;&#9472;&#9472;5*[apache]
     &#9500;&#9472;atd
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;bt-applet
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dhclient3
     &#9500;&#9472;events/0
     &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;2*[{evolution-alarm}]
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;2*[{evolution-data-}]
     &#9500;&#9472;exim4
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9472;&#9472;2*[ssh-agent]
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-cups-icon
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-panel
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;top
     &#9474;                &#9500;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo
     &#9500;&#9472;gnome-volume-ma
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-keyb
     &#9474;                    &#9492;&#9472;hald-addon-stor
     &#9500;&#9472;hcid
     &#9500;&#9472;hddtemp
     &#9500;&#9472;hidd
     &#9500;&#9472;hpiod
     &#9500;&#9472;khelper
     &#9500;&#9472;knodemgrd_0
     &#9500;&#9472;krfcommd
     &#9500;&#9472;ksoftirqd/0
     &#9500;&#9472;kswapd0
     &#9500;&#9472;kthread&#9472;&#9516;&#9472;aio/0
     &#9474;         &#9500;&#9472;ata/0
     &#9474;         &#9500;&#9472;kacpi_notify
     &#9474;         &#9500;&#9472;kacpid
     &#9474;         &#9500;&#9472;kblockd/0
     &#9474;         &#9500;&#9472;khpsbpkt
     &#9474;         &#9500;&#9472;khubd
     &#9474;         &#9500;&#9472;kjournald
     &#9474;         &#9500;&#9472;kpsmoused
     &#9474;         &#9500;&#9472;kseriod
     &#9474;         &#9500;&#9472;2*[pdflush]
     &#9474;         &#9500;&#9472;scsi_eh_0
     &#9474;         &#9500;&#9472;scsi_eh_1
     &#9474;         &#9492;&#9472;shpchpd
     &#9500;&#9472;mapping-daemon
     &#9500;&#9472;mdadm
     &#9500;&#9472;metacity
     &#9500;&#9472;mixer_applet2
     &#9500;&#9472;nautilus
     &#9500;&#9472;perl
     &#9500;&#9472;python
     &#9500;&#9472;sdpd
     &#9500;&#9472;sh&#9472;&#9472;&#9472;esd
     &#9500;&#9472;syslog-ng
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd
     &#9500;&#9472;update-notifier&#9472;&#9472;&#9472;python
     &#9500;&#9472;uptimed
     &#9500;&#9472;watchdog/0
     &#9492;&#9472;xscreensaver



```

---

### Post by JohnFH on 2008-11-04
Ok, I'm not too sure why, but it looks like update-notifier process is taking the CPU time.  I'm guessing that since you haven't logged on for a month, the system is doing automatic updates.  Have you left it long enough to complete the updates?  It shouldn't take that long at all, but depends on the speed of your system and how patient you are. :)

Try the following:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Then reboot.  If you still get the same problem, try turning off update-notifier.  I'm running Kubuntu so don't use the Gnome update-notifier, so not sure how to turn that off.  

Let me know if that helps.

---

### Post by meniscus on 2008-11-04
Thanks. ill try that

---

### Post by sdennie on 2008-11-04
You can get the output of top with:

```

top -n 1

```

That just runs top for 1 iteration instead of continuously.  To get the output that will likely be useful in figuring out what is causing your problem, try:

```

ps aux | grep python

```

Edit:
Didn't notice the second page to this.  If you need to disable the update notifier for some reason, you can do it with System->Preferences->Sessions and then disabling update-notifier and logging back in (you may have to kill the running update notifier though).  However, that's an odd problem and if disabling update-notifier fixes it, you should really file a bug.

---

### Post by coolbrook on 2008-11-04
What's your watt meter reading when you boot into Windows?

---

