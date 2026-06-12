---
title: "Little paranoia"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by dkdfsklj on 2013-06-01
Hello people. I think someone is spying on my computer. Please help how to ensure is it true or not.

---

### Post by Old_Grey_Wolf on 2013-06-01
What have you seen that makes you think someone may be spying on you?

Without some information, all we can do is point you to wiki pages, etc. that are very long articles about securing you computer and detecting intrusions.

---

### Post by dkdfsklj on 2013-06-01
> **Old_Grey_Wolf said:**
> What have you seen that makes you think someone may be spying on you?

Without some information, all we can do is point you to wiki pages, etc. that are very long articles about securing you computer and detecting intrusions.

I am dumb as can be. Maybe I can show you processes that are running on my system but I don't how to do it.

---

### Post by Old_Grey_Wolf on 2013-06-01
To show us running processes paste this command in the terminal and hit enter:
```
ps aux
```
Post the output of the command in a response to this thread. Please use the CODE TAGs, i.e., the # icon.

EDIT: I see that your posts are being edited for language. Stop it now before you get an infraction or worse.

---

### Post by QIII on 2013-06-01
dkdfsklj --

It may have seemed a small thing, but I have edited your post.  

From the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules"):

> **Profanity:** We have users of all age groups and of all tolerance  levels where profanity is concerned. A language filter is in place to  catch most major forms of profanity that may accidentally be used. Do  not attempt to circumvent the language filter by using variations or  slight misspellings of profanities.

Thanks!

---

### Post by dkdfsklj on 2013-06-01
That is
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3664  2036 ?        Ss   Jun01   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Jun01   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Jun01   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Jun01   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Jun01   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    Jun01   0:00 [migration/1]
root        10  0.0  0.0      0     0 ?        S    Jun01   0:00 [ksoftirqd/1]
root        12  0.0  0.0      0     0 ?        S    Jun01   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S<   Jun01   0:00 [cpuset]
root        14  0.0  0.0      0     0 ?        S<   Jun01   0:00 [khelper]
root        15  0.0  0.0      0     0 ?        S    Jun01   0:00 [kdevtmpfs]
root        16  0.0  0.0      0     0 ?        S<   Jun01   0:00 [netns]
root        18  0.0  0.0      0     0 ?        S    Jun01   0:00 [sync_supers]
root        19  0.0  0.0      0     0 ?        S    Jun01   0:00 [bdi-default]
root        20  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kintegrityd]
root        21  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kblockd]
root        22  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ata_sff]
root        23  0.0  0.0      0     0 ?        S    Jun01   0:00 [khubd]
root        24  0.0  0.0      0     0 ?        S<   Jun01   0:00 [md]
root        26  0.0  0.0      0     0 ?        S    Jun01   0:00 [khungtaskd]
root        27  0.0  0.0      0     0 ?        S    Jun01   0:00 [kswapd0]
root        28  0.0  0.0      0     0 ?        SN   Jun01   0:00 [ksmd]
root        29  0.0  0.0      0     0 ?        SN   Jun01   0:00 [khugepaged]
root        30  0.0  0.0      0     0 ?        S    Jun01   0:00 [fsnotify_mark]
root        31  0.0  0.0      0     0 ?        S    Jun01   0:00 [ecryptfs-kthr]
root        32  0.0  0.0      0     0 ?        S<   Jun01   0:00 [crypto]
root        40  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kthrotld]
root        60  0.0  0.0      0     0 ?        S<   Jun01   0:00 [devfreq_wq]
root       179  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_0]
root       180  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_1]
root       206  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_2]
root       207  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_3]
root       209  0.0  0.0      0     0 ?        S    Jun01   0:00 [kworker/u:4]
root       210  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_4]
root       211  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_5]
root       212  0.0  0.0      0     0 ?        S    Jun01   0:00 [kworker/u:5]
root       281  0.0  0.0      0     0 ?        S    Jun01   0:00 [jbd2/sda7-8]
root       282  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ext4-dio-unwr]
root       300  0.0  0.0      0     0 ?        S    Jun01   0:00 [flush-8:0]
root       303  0.0  0.0   5244  1340 ?        S    Jun01   0:00 mountall --daem
root       369  0.0  0.0   2832   608 ?        S    Jun01   0:00 upstart-udev-br
root       372  0.0  0.0   3320  1532 ?        Ss   Jun01   0:00 /sbin/udevd --d
root       546  0.0  0.0   3316  1096 ?        S    Jun01   0:00 /sbin/udevd --d
root       589  0.0  0.0   3320  1064 ?        S    Jun01   0:00 /sbin/udevd --d
root       609  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kpsmoused]
root       676  0.0  0.0      0     0 ?        S<   Jun01   0:00 [hd-audio0]
root       726  0.0  0.0   2844   364 ?        S    Jun01   0:00 upstart-socket-
root       765  0.0  0.0      0     0 ?        S<   Jun01   0:00 [hd-audio1]
root       824  0.0  0.0      0     0 ?        S    Jun01   0:00 [kjournald]
root       832  0.0  0.0      0     0 ?        S    Jun01   0:00 [jbd2/sda6-8]
root       834  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ext4-dio-unwr]
syslog     870  0.0  0.0  31060  1464 ?        Sl   Jun01   0:00 rsyslogd -c5
102        872  0.0  0.0   3972  1664 ?        Ss   Jun01   0:00 dbus-daemon --s
root       887  0.0  0.0   7220  2772 ?        Ss   Jun01   0:00 /usr/sbin/modem
root       888  0.0  0.0   4740  1644 ?        Ss   Jun01   0:00 /usr/sbin/bluet
root       903  0.0  0.1  31004  4748 ?        Ssl  Jun01   0:00 NetworkManager
root       912  0.0  0.0  25380  3856 ?        Sl   Jun01   0:00 /usr/lib/policy
root       930  0.0  0.0      0     0 ?        S<   Jun01   0:00 [krfcommd]
root       946  0.0  0.0  11072  3280 ?        Ss   Jun01   0:00 /usr/sbin/cupsd
root       960  0.0  0.0   7408  2648 ?        S    Jun01   0:00 /usr/sbin/pppd
root       988  0.0  0.0   4628   852 tty4     Ss+  Jun01   0:00 /sbin/getty -8
root       993  0.0  0.0   4628   852 tty5     Ss+  Jun01   0:00 /sbin/getty -8
root       999  0.0  0.0   4628   852 tty2     Ss+  Jun01   0:00 /sbin/getty -8
root      1000  0.0  0.0   4628   860 tty3     Ss+  Jun01   0:00 /sbin/getty -8
root      1001  0.0  0.0   4244  1016 ?        Ss   Jun01   0:00 kdm
root      1003  0.0  0.0   4628   852 tty6     Ss+  Jun01   0:00 /sbin/getty -8
whoopsie  1026  0.0  0.1  25908  4404 ?        Ssl  Jun01   0:00 whoopsie
root      1028  0.0  0.0   2172   696 ?        Ss   Jun01   0:00 acpid -c /etc/a
root      1030  0.0  0.0   3600   636 ?        Ss   Jun01   0:00 /usr/sbin/irqba
root      1031  0.0  0.0   2616   892 ?        Ss   Jun01   0:00 cron
daemon    1032  0.0  0.0   2468   348 ?        Ss   Jun01   0:00 atd
root      1035 10.4  1.4  80264 59828 tty7     Ss+  Jun01   9:27 /usr/bin/X :0 v
116       1069  0.0  0.4  20824 17100 ?        S    Jun01   0:03 /usr/sbin/tor -
root      1237  0.0  0.0   4628   848 tty1     Ss+  Jun01   0:00 /sbin/getty -8
root      1250  0.0  0.0   5296  2160 ?        S    Jun01   0:00 -:0
nobody    1265  0.0  0.0   5400  1132 ?        S    Jun01   0:00 /usr/sbin/dnsma
root      1320  0.0  0.0  30148  3312 ?        Sl   Jun01   0:00 /usr/sbin/conso
tet       1393  0.0  0.0   2232   560 ?        Ss   Jun01   0:00 /bin/sh /etc/xd
tet       1447  0.0  0.0   4076   208 ?        Ss   Jun01   0:00 /usr/bin/ssh-ag
tet       1450  0.0  0.0   3936   508 ?        S    Jun01   0:00 /usr/bin/dbus-l
tet       1451  0.0  0.0   6192  2384 ?        Ss   Jun01   0:00 //bin/dbus-daem
tet       1459  0.0  0.0   6564  2388 ?        S    Jun01   0:00 /usr/lib/xfce4/
tet       1463  0.0  0.0   5228   380 ?        Ss   Jun01   0:00 gpg-agent --dae
tet       1467  0.0  0.0   7520  2436 ?        S    Jun01   0:00 xscreensaver -n
tet       1469  0.0  0.1  49568  6980 ?        Sl   Jun01   0:00 xfce4-session
tet       1478  0.0  0.2  41876 10236 ?        Sl   Jun01   0:01 xfwm4 --replace
tet       1482  0.0  0.0  38488  3660 ?        S    Jun01   0:00 xfsettingsd --f
tet       1483  0.0  0.4 139348 17908 ?        Sl   Jun01   0:00 Thunar --sm-cli
tet       1487  0.0  0.0   8404  2200 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1489  0.0  0.0  34756  2544 ?        Sl   Jun01   0:00 /usr/lib/gvfs//
tet       1490  0.0  0.3 127756 13180 ?        Sl   Jun01   0:02 xfce4-panel --d
tet       1497  0.0  0.5 136156 24324 ?        Sl   Jun01   0:04 xfdesktop --dis
tet       1501  0.0  1.0 255708 41924 ?        Sl   Jun01   0:00 goldendict -ses
tet       1503  0.0  0.0   9392  2924 ?        S    Jun01   0:00 /usr/lib/i386-l
tet       1508  0.0  0.1  39504  7180 ?        Sl   Jun01   0:00 /usr/lib/i386-l
tet       1510  1.6  0.1  38808  7012 ?        Sl   Jun01   1:29 /usr/lib/xfce4-
tet       1512  0.0  0.2 124076 11504 ?        Sl   Jun01   0:00 /usr/lib/xfce4-
tet       1515  0.0  0.2  51996 10484 ?        Sl   Jun01   0:02 /usr/lib/i386-l
tet       1517  0.0  0.0   9992  3392 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1518  0.0  0.3 127228 13300 ?        Sl   Jun01   0:00 /usr/lib/i386-l
root      1522  0.0  0.0  25372  3616 ?        Sl   Jun01   0:00 /usr/lib/udisks
root      1523  0.0  0.0   6552   728 ?        S    Jun01   0:00 udisks-daemon: 
tet       1525  0.0  0.1  39688  8220 ?        Sl   Jun01   0:04 /usr/lib/i386-l
tet       1526  0.0  0.1  40940  7668 ?        Sl   Jun01   0:00 /usr/lib/i386-l
tet       1529  0.0  0.3 509424 13324 ?        Sl   Jun01   0:00 /usr/lib/xfce4-
tet       1531  0.0  0.4 143680 18480 ?        Sl   Jun01   0:00 synapse --start
tet       1535  0.0  0.5 211716 23400 ?        Sl   Jun01   0:00 /usr/bin/python
tet       1537  0.0  0.0   9208  2088 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1539  0.0  0.0  20484  2136 ?        Sl   Jun01   0:00 /usr/lib/gvfs/g
tet       1550  0.0  0.2 123924 10440 ?        Sl   Jun01   0:00 bluetooth-apple
tet       1594  0.0  0.0   8816  2912 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1602  0.0  0.1  37936  5252 ?        Sl   Jun01   0:00 /usr/lib/policy
tet       1638  3.2  0.1 174608  5804 ?        S<l  Jun01   2:54 /usr/bin/pulsea
rtkit     1640  0.0  0.0  21328  1208 ?        SNl  Jun01   0:00 /usr/lib/rtkit/
tet       1643  0.0  0.0  35884  3436 ?        Sl   Jun01   0:00 /usr/lib/deja-d
tet       1647  0.0  0.0  38708  3732 ?        Ss   Jun01   0:00 xfce4-power-man
tet       1650  0.0  0.4  60348 17968 ?        Sl   Jun01   0:00 /usr/bin/python
tet       1656  0.0  0.2 435128  9924 ?        Ssl  Jun01   0:01 xfce4-volumed
tet       1657  0.0  0.1  55328  6728 ?        Sl   Jun01   0:00 zeitgeist-datah
tet       1661  0.0  0.3 183008 13928 ?        Sl   Jun01   0:00 nm-applet
tet       1667  0.0  0.3 126536 13284 ?        Sl   Jun01   0:00 update-notifier
tet       1672  0.0  0.1  44084  4540 ?        Sl   Jun01   0:00 /usr/bin/zeitge
tet       1680  0.0  0.1  51964  8048 ?        Sl   Jun01   0:00 /usr/lib/zeitge
tet       1692  0.0  0.0   4224   284 ?        S    Jun01   0:00 /bin/cat
tet       1701 10.7  7.3 855556 301740 ?       Sl   Jun01   9:43 /usr/lib/firefo
tet       1727  0.0  0.0  14100  2484 ?        S    Jun01   0:00 /usr/lib/pulsea
tet       1798  0.0  0.0   8820  2320 ?        S    Jun01   0:00 /usr/bin/obex-d
tet       1800  0.0  0.6  83800 25272 ?        Sl   Jun01   0:00 /usr/bin/python
root      1809  0.0  0.0  28392  3624 ?        Sl   Jun01   0:00 /usr/lib/upower
tet       1939  0.0  0.0  35156  3032 ?        Sl   Jun01   0:00 /usr/lib/at-spi
tet       1967  0.0  0.0  46116  3756 ?        Sl   Jun01   0:00 /usr/bin/gnome-
tet       2010 46.7  2.7 407328 111784 ?       Rl   Jun01  42:17 /usr/lib/firefo
tet       2121  0.0  0.0   8244  1924 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       2128  0.0  0.5 146488 23208 ?        Sl   Jun01   0:01 gedit /home/tet
tet       2134  0.0  0.0  33644  2424 ?        Sl   Jun01   0:00 /usr/lib/dconf/
root      2142  0.0  0.0      0     0 ?        S    Jun01   0:01 [kworker/0:0]
tet       2159  0.0  0.5 133088 22272 ?        Sl   Jun01   0:01 xfce4-appfinder
tet       2162  1.2  1.0 186432 42696 ?        Sl   Jun01   0:28 ksysguard
tet       2168  0.3  0.0   2732  1172 ?        S    Jun01   0:08 ksysguardd
tet       2170  0.0  0.5 133088 22276 ?        Sl   Jun01   0:01 xfce4-appfinder
root      2250  0.0  0.0      0     0 ?        S    00:02   0:00 [kworker/1:2]
root      2260  0.0  0.0      0     0 ?        S    00:03   0:00 [kworker/0:2]
root      2265  0.0  0.0      0     0 ?        S    00:07   0:00 [kworker/1:1]
root      2283  0.1  0.0      0     0 ?        S    00:08   0:01 [kworker/0:1]
root      2297  0.0  0.0      0     0 ?        S    00:12   0:00 [kworker/1:3]
root      2322  0.0  0.0      0     0 ?        S    00:17   0:00 [kworker/1:0]
tet       2357  0.1  0.0  27456  3292 ?        Sl   00:20   0:00 /usr/lib/gvfs/g
tet       2366  0.0  0.0   8616  2488 ?        S    00:20   0:00 /usr/lib/gvfs/g
tet       2376  2.8  0.3 136380 14568 ?        Rl   00:20   0:00 gnome-terminal
tet       2380  0.0  0.0   2400   704 ?        S    00:20   0:00 gnome-pty-helpe
tet       2381  3.0  0.0   7716  4056 pts/0    Ss   00:20   0:00 bash
tet       2438  0.0  0.0   4944  1124 pts/0    R+   00:20   0:00 ps aux
```

---

### Post by dkdfsklj on 2013-06-01
> **QIII said:**
> dkdfsklj --

It may have seemed a small thing, but I have edited your post.  

From the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules"):



Thanks!

Sorry I'm not English speaking.

---

### Post by dkdfsklj on 2013-06-01
> **Old_Grey_Wolf said:**
> To show us running processes paste this command in the terminal and hit enter:
```
ps aux
```
Post the output of the command in a response to this thread. Please use the CODE TAGs, i.e., the # icon.

EDIT: I see that your posts are being edited for language. Stop it now before you get an infraction or worse.

Yes!

And that is my processes:
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3664  2036 ?        Ss   Jun01   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Jun01   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Jun01   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Jun01   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Jun01   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    Jun01   0:00 [migration/1]
root        10  0.0  0.0      0     0 ?        S    Jun01   0:00 [ksoftirqd/1]
root        12  0.0  0.0      0     0 ?        S    Jun01   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S<   Jun01   0:00 [cpuset]
root        14  0.0  0.0      0     0 ?        S<   Jun01   0:00 [khelper]
root        15  0.0  0.0      0     0 ?        S    Jun01   0:00 [kdevtmpfs]
root        16  0.0  0.0      0     0 ?        S<   Jun01   0:00 [netns]
root        18  0.0  0.0      0     0 ?        S    Jun01   0:00 [sync_supers]
root        19  0.0  0.0      0     0 ?        S    Jun01   0:00 [bdi-default]
root        20  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kintegrityd]
root        21  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kblockd]
root        22  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ata_sff]
root        23  0.0  0.0      0     0 ?        S    Jun01   0:00 [khubd]
root        24  0.0  0.0      0     0 ?        S<   Jun01   0:00 [md]
root        26  0.0  0.0      0     0 ?        S    Jun01   0:00 [khungtaskd]
root        27  0.0  0.0      0     0 ?        S    Jun01   0:00 [kswapd0]
root        28  0.0  0.0      0     0 ?        SN   Jun01   0:00 [ksmd]
root        29  0.0  0.0      0     0 ?        SN   Jun01   0:00 [khugepaged]
root        30  0.0  0.0      0     0 ?        S    Jun01   0:00 [fsnotify_mark]
root        31  0.0  0.0      0     0 ?        S    Jun01   0:00 [ecryptfs-kthr]
root        32  0.0  0.0      0     0 ?        S<   Jun01   0:00 [crypto]
root        40  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kthrotld]
root        60  0.0  0.0      0     0 ?        S<   Jun01   0:00 [devfreq_wq]
root       179  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_0]
root       180  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_1]
root       206  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_2]
root       207  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_3]
root       209  0.0  0.0      0     0 ?        S    Jun01   0:00 [kworker/u:4]
root       210  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_4]
root       211  0.0  0.0      0     0 ?        S    Jun01   0:00 [scsi_eh_5]
root       212  0.0  0.0      0     0 ?        S    Jun01   0:00 [kworker/u:5]
root       281  0.0  0.0      0     0 ?        S    Jun01   0:00 [jbd2/sda7-8]
root       282  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ext4-dio-unwr]
root       300  0.0  0.0      0     0 ?        S    Jun01   0:00 [flush-8:0]
root       303  0.0  0.0   5244  1340 ?        S    Jun01   0:00 mountall --daem
root       369  0.0  0.0   2832   608 ?        S    Jun01   0:00 upstart-udev-br
root       372  0.0  0.0   3320  1532 ?        Ss   Jun01   0:00 /sbin/udevd --d
root       546  0.0  0.0   3316  1096 ?        S    Jun01   0:00 /sbin/udevd --d
root       589  0.0  0.0   3320  1064 ?        S    Jun01   0:00 /sbin/udevd --d
root       609  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kpsmoused]
root       676  0.0  0.0      0     0 ?        S<   Jun01   0:00 [hd-audio0]
root       726  0.0  0.0   2844   364 ?        S    Jun01   0:00 upstart-socket-
root       765  0.0  0.0      0     0 ?        S<   Jun01   0:00 [hd-audio1]
root       824  0.0  0.0      0     0 ?        S    Jun01   0:00 [kjournald]
root       832  0.0  0.0      0     0 ?        S    Jun01   0:00 [jbd2/sda6-8]
root       834  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ext4-dio-unwr]
syslog     870  0.0  0.0  31060  1464 ?        Sl   Jun01   0:00 rsyslogd -c5
102        872  0.0  0.0   3972  1664 ?        Ss   Jun01   0:00 dbus-daemon --s
root       887  0.0  0.0   7220  2772 ?        Ss   Jun01   0:00 /usr/sbin/modem
root       888  0.0  0.0   4740  1644 ?        Ss   Jun01   0:00 /usr/sbin/bluet
root       903  0.0  0.1  31004  4748 ?        Ssl  Jun01   0:00 NetworkManager
root       912  0.0  0.0  25380  3856 ?        Sl   Jun01   0:00 /usr/lib/policy
root       930  0.0  0.0      0     0 ?        S<   Jun01   0:00 [krfcommd]
root       946  0.0  0.0  11072  3280 ?        Ss   Jun01   0:00 /usr/sbin/cupsd
root       960  0.0  0.0   7408  2648 ?        S    Jun01   0:00 /usr/sbin/pppd
root       988  0.0  0.0   4628   852 tty4     Ss+  Jun01   0:00 /sbin/getty -8
root       993  0.0  0.0   4628   852 tty5     Ss+  Jun01   0:00 /sbin/getty -8
root       999  0.0  0.0   4628   852 tty2     Ss+  Jun01   0:00 /sbin/getty -8
root      1000  0.0  0.0   4628   860 tty3     Ss+  Jun01   0:00 /sbin/getty -8
root      1001  0.0  0.0   4244  1016 ?        Ss   Jun01   0:00 kdm
root      1003  0.0  0.0   4628   852 tty6     Ss+  Jun01   0:00 /sbin/getty -8
whoopsie  1026  0.0  0.1  25908  4404 ?        Ssl  Jun01   0:00 whoopsie
root      1028  0.0  0.0   2172   696 ?        Ss   Jun01   0:00 acpid -c /etc/a
root      1030  0.0  0.0   3600   636 ?        Ss   Jun01   0:00 /usr/sbin/irqba
root      1031  0.0  0.0   2616   892 ?        Ss   Jun01   0:00 cron
daemon    1032  0.0  0.0   2468   348 ?        Ss   Jun01   0:00 atd
root      1035 10.4  1.4  80264 59828 tty7     Ss+  Jun01   9:27 /usr/bin/X :0 v
116       1069  0.0  0.4  20824 17100 ?        S    Jun01   0:03 /usr/sbin/tor -
root      1237  0.0  0.0   4628   848 tty1     Ss+  Jun01   0:00 /sbin/getty -8
root      1250  0.0  0.0   5296  2160 ?        S    Jun01   0:00 -:0
nobody    1265  0.0  0.0   5400  1132 ?        S    Jun01   0:00 /usr/sbin/dnsma
root      1320  0.0  0.0  30148  3312 ?        Sl   Jun01   0:00 /usr/sbin/conso
tet       1393  0.0  0.0   2232   560 ?        Ss   Jun01   0:00 /bin/sh /etc/xd
tet       1447  0.0  0.0   4076   208 ?        Ss   Jun01   0:00 /usr/bin/ssh-ag
tet       1450  0.0  0.0   3936   508 ?        S    Jun01   0:00 /usr/bin/dbus-l
tet       1451  0.0  0.0   6192  2384 ?        Ss   Jun01   0:00 //bin/dbus-daem
tet       1459  0.0  0.0   6564  2388 ?        S    Jun01   0:00 /usr/lib/xfce4/
tet       1463  0.0  0.0   5228   380 ?        Ss   Jun01   0:00 gpg-agent --dae
tet       1467  0.0  0.0   7520  2436 ?        S    Jun01   0:00 xscreensaver -n
tet       1469  0.0  0.1  49568  6980 ?        Sl   Jun01   0:00 xfce4-session
tet       1478  0.0  0.2  41876 10236 ?        Sl   Jun01   0:01 xfwm4 --replace
tet       1482  0.0  0.0  38488  3660 ?        S    Jun01   0:00 xfsettingsd --f
tet       1483  0.0  0.4 139348 17908 ?        Sl   Jun01   0:00 Thunar --sm-cli
tet       1487  0.0  0.0   8404  2200 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1489  0.0  0.0  34756  2544 ?        Sl   Jun01   0:00 /usr/lib/gvfs//
tet       1490  0.0  0.3 127756 13180 ?        Sl   Jun01   0:02 xfce4-panel --d
tet       1497  0.0  0.5 136156 24324 ?        Sl   Jun01   0:04 xfdesktop --dis
tet       1501  0.0  1.0 255708 41924 ?        Sl   Jun01   0:00 goldendict -ses
tet       1503  0.0  0.0   9392  2924 ?        S    Jun01   0:00 /usr/lib/i386-l
tet       1508  0.0  0.1  39504  7180 ?        Sl   Jun01   0:00 /usr/lib/i386-l
tet       1510  1.6  0.1  38808  7012 ?        Sl   Jun01   1:29 /usr/lib/xfce4-
tet       1512  0.0  0.2 124076 11504 ?        Sl   Jun01   0:00 /usr/lib/xfce4-
tet       1515  0.0  0.2  51996 10484 ?        Sl   Jun01   0:02 /usr/lib/i386-l
tet       1517  0.0  0.0   9992  3392 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1518  0.0  0.3 127228 13300 ?        Sl   Jun01   0:00 /usr/lib/i386-l
root      1522  0.0  0.0  25372  3616 ?        Sl   Jun01   0:00 /usr/lib/udisks
root      1523  0.0  0.0   6552   728 ?        S    Jun01   0:00 udisks-daemon: 
tet       1525  0.0  0.1  39688  8220 ?        Sl   Jun01   0:04 /usr/lib/i386-l
tet       1526  0.0  0.1  40940  7668 ?        Sl   Jun01   0:00 /usr/lib/i386-l
tet       1529  0.0  0.3 509424 13324 ?        Sl   Jun01   0:00 /usr/lib/xfce4-
tet       1531  0.0  0.4 143680 18480 ?        Sl   Jun01   0:00 synapse --start
tet       1535  0.0  0.5 211716 23400 ?        Sl   Jun01   0:00 /usr/bin/python
tet       1537  0.0  0.0   9208  2088 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1539  0.0  0.0  20484  2136 ?        Sl   Jun01   0:00 /usr/lib/gvfs/g
tet       1550  0.0  0.2 123924 10440 ?        Sl   Jun01   0:00 bluetooth-apple
tet       1594  0.0  0.0   8816  2912 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       1602  0.0  0.1  37936  5252 ?        Sl   Jun01   0:00 /usr/lib/policy
tet       1638  3.2  0.1 174608  5804 ?        S<l  Jun01   2:54 /usr/bin/pulsea
rtkit     1640  0.0  0.0  21328  1208 ?        SNl  Jun01   0:00 /usr/lib/rtkit/
tet       1643  0.0  0.0  35884  3436 ?        Sl   Jun01   0:00 /usr/lib/deja-d
tet       1647  0.0  0.0  38708  3732 ?        Ss   Jun01   0:00 xfce4-power-man
tet       1650  0.0  0.4  60348 17968 ?        Sl   Jun01   0:00 /usr/bin/python
tet       1656  0.0  0.2 435128  9924 ?        Ssl  Jun01   0:01 xfce4-volumed
tet       1657  0.0  0.1  55328  6728 ?        Sl   Jun01   0:00 zeitgeist-datah
tet       1661  0.0  0.3 183008 13928 ?        Sl   Jun01   0:00 nm-applet
tet       1667  0.0  0.3 126536 13284 ?        Sl   Jun01   0:00 update-notifier
tet       1672  0.0  0.1  44084  4540 ?        Sl   Jun01   0:00 /usr/bin/zeitge
tet       1680  0.0  0.1  51964  8048 ?        Sl   Jun01   0:00 /usr/lib/zeitge
tet       1692  0.0  0.0   4224   284 ?        S    Jun01   0:00 /bin/cat
tet       1701 10.7  7.3 855556 301740 ?       Sl   Jun01   9:43 /usr/lib/firefo
tet       1727  0.0  0.0  14100  2484 ?        S    Jun01   0:00 /usr/lib/pulsea
tet       1798  0.0  0.0   8820  2320 ?        S    Jun01   0:00 /usr/bin/obex-d
tet       1800  0.0  0.6  83800 25272 ?        Sl   Jun01   0:00 /usr/bin/python
root      1809  0.0  0.0  28392  3624 ?        Sl   Jun01   0:00 /usr/lib/upower
tet       1939  0.0  0.0  35156  3032 ?        Sl   Jun01   0:00 /usr/lib/at-spi
tet       1967  0.0  0.0  46116  3756 ?        Sl   Jun01   0:00 /usr/bin/gnome-
tet       2010 46.7  2.7 407328 111784 ?       Rl   Jun01  42:17 /usr/lib/firefo
tet       2121  0.0  0.0   8244  1924 ?        S    Jun01   0:00 /usr/lib/gvfs/g
tet       2128  0.0  0.5 146488 23208 ?        Sl   Jun01   0:01 gedit /home/tet
tet       2134  0.0  0.0  33644  2424 ?        Sl   Jun01   0:00 /usr/lib/dconf/
root      2142  0.0  0.0      0     0 ?        S    Jun01   0:01 [kworker/0:0]
tet       2159  0.0  0.5 133088 22272 ?        Sl   Jun01   0:01 xfce4-appfinder
tet       2162  1.2  1.0 186432 42696 ?        Sl   Jun01   0:28 ksysguard
tet       2168  0.3  0.0   2732  1172 ?        S    Jun01   0:08 ksysguardd
tet       2170  0.0  0.5 133088 22276 ?        Sl   Jun01   0:01 xfce4-appfinder
root      2250  0.0  0.0      0     0 ?        S    00:02   0:00 [kworker/1:2]
root      2260  0.0  0.0      0     0 ?        S    00:03   0:00 [kworker/0:2]
root      2265  0.0  0.0      0     0 ?        S    00:07   0:00 [kworker/1:1]
root      2283  0.1  0.0      0     0 ?        S    00:08   0:01 [kworker/0:1]
root      2297  0.0  0.0      0     0 ?        S    00:12   0:00 [kworker/1:3]
root      2322  0.0  0.0      0     0 ?        S    00:17   0:00 [kworker/1:0]
tet       2357  0.1  0.0  27456  3292 ?        Sl   00:20   0:00 /usr/lib/gvfs/g
tet       2366  0.0  0.0   8616  2488 ?        S    00:20   0:00 /usr/lib/gvfs/g
tet       2376  2.8  0.3 136380 14568 ?        Rl   00:20   0:00 gnome-terminal
tet       2380  0.0  0.0   2400   704 ?        S    00:20   0:00 gnome-pty-helpe
tet       2381  3.0  0.0   7716  4056 pts/0    Ss   00:20   0:00 bash
tet       2438  0.0  0.0   4944  1124 pts/0    R+   00:20   0:00 ps aux


```

---

### Post by Old_Grey_Wolf on 2013-06-01
Looking at that output of "ps aux", I don't see anything unusual. 

Are you having other symptoms?

---

### Post by cariboo on 2013-06-01
There is nothing in the output of the command Old_Grey_Wolf gave you that indicates that someone is spying on you. Again, what makes you think someone is spying on you?

**edit** Ninja'd by Old_Grey_Wolf :-D

---

### Post by dkdfsklj on 2013-06-01
> **Old_Grey_Wolf said:**
> Looking at that output of "ps aux", I don't see anything unusual. 

Are you having other symptoms?

Well, other are more psychological. Anyway thank you for help. Maybe I will remember something important later.
P.S. and please give some links about spying\antispying software... thanx

---

### Post by Old_Grey_Wolf on 2013-06-01
> **dkdfsklj said:**
> 
P.S. and please give some links about spying\antispying software... thanx

OK,

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

There is also a Security sub-forum at [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

