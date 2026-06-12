---
title: "Ubuntu 14.04: very slow response from a 64 bit fresh install on 4 core server"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by ubtkrak on 2014-08-11
Hello,

This is my very first Linux experience. I did a fresh install of Ubuntu 14.40 desktop version (64 bit) on the Dell quad-core (2.3 Ghz) AMD64 server with 8 GB of memory. The graphics card is NVIDIA CK8-04 Pro (System details says "Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits")).

With just the Ubuntu installed, the GUI response was laggy but not slow enough to stop me from working. The response when using the terminal was good. But, after I installed the Oracle 12c database, even though the database has not been started, the performance of the machine has deteriorated a lot. I have click on the title bar of a window and wait for some time before the focus can be switched to that window. Even in the terminal, I type the commands and wait for some time for the typed letters to appear. I cannot use the system like this.

From the image below you can see high CPU usage with only the OS and screen shot app running. The memory usage is less than 1/4th.
[http://imgur.com/gRKJYra](http://imgur.com/gRKJYra)

The following link shows the processes running:
[http://imgur.com/Ma21tQ6](http://imgur.com/Ma21tQ6)

I'm really surprised that Linux can be this slow that too on a quad-core server box with 8 GB of memory!!!

Any pointers on how to improve the performance will be of great help.

Thanks in advance for the time taken to respond to this post.

---

### Post by whitesmith on 2014-08-11
Hello. Utilization at this level is indicative of a serious problem. Try```
top -bn1
```and post the results for us to see.

---

### Post by ubtkrak on 2014-08-11
Thanks whitesmith for the quick response. Please find below the output from the "top" cmd. The format of columns is messed up below. Sorry about that. The web site doesn't take tab as input.
```

tusr@PowerEdge-T105:~$ top -bn1
top - 16:24:44 up  5:13,  3 users,  load average: 0.30, 0.14, 0.16
Tasks: 187 total,   2 running, 185 sleeping,   0 stopped,   0 zombie
%Cpu(s): 11.6 us,  2.4 sy,  0.0 ni, 85.8 id,  0.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8176124 total,  2301408 used,  5874716 free,   113192 buffers
KiB Swap:  7811068 total,        0 used,  7811068 free.   859180 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 5122 tusr      20   0 1851312 403740  59648 S 125.4  4.9  15:09.49 compiz
 4408 root      20   0  542948 222760  35820 S  18.8  2.7   2:09.43 Xorg
 4857 tusr      20   0  450472   7364   3560 S   6.3  0.1   0:02.29 ibus-daemon
 6130 tusr      20   0   29012   1412   1036 R   6.3  0.0   0:00.01 top
    1 root      20   0   33864   3100   1408 S   0.0  0.0   0:01.88 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.07 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+
    7 root      20   0       0      0      0 S   0.0  0.0   0:20.30 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:02.94 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:02.30 rcuos/1
   10 root      20   0       0      0      0 S   0.0  0.0   0:01.83 rcuos/2
   11 root      20   0       0      0      0 S   0.0  0.0   0:10.26 rcuos/3
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.12 migration/0
   18 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/0
   19 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/1
   20 root      rt   0       0      0      0 S   0.0  0.0   0:00.42 migration/1
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/1
   22 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0
   23 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+
   24 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/2
   25 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 migration/2
   26 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/2
   28 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:+
   29 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/3
   30 root      rt   0       0      0      0 S   0.0  0.0   0:00.13 migration/3
   31 root      20   0       0      0      0 S   0.0  0.0   0:00.03 ksoftirqd/3
   33 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:+
   34 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   35 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   36 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   37 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   38 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   39 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   40 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u9+
   41 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   42 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   43 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khubd
   44 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
   45 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
   46 root      20   0       0      0      0 S   0.0  0.0   0:04.43 kworker/0:1
   47 root      20   0       0      0      0 S   0.0  0.0   0:33.36 kworker/1:1
   48 root      20   0       0      0      0 S   0.0  0.0   0:34.36 kworker/2:1
   49 root      20   0       0      0      0 S   0.0  0.0   1:20.36 kworker/3:1
   50 root      20   0       0      0      0 S   0.0  0.0   0:00.01 khungtaskd
   51 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kswapd0
   52 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   53 root      39  19       0      0      0 S   0.0  0.0   0:01.13 khugepaged
   54 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_m+
   55 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-k+
   56 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   68 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
   88 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   89 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_ma+
  140 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  141 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  144 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_2
  145 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_3
  148 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
  149 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/2:2
  163 root      20   0       0      0      0 S   0.0  0.0   0:00.10 jbd2/sda1-8
  164 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-c+
  287 root      20   0   19476    652    452 S   0.0  0.0   0:00.16 upstart-ud+
  292 root      20   0   51692   1852    972 S   0.0  0.0   0:00.07 systemd-ud+
  350 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 edac-poller
  358 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kvm-irqfd-+
  359 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ttm_swap
  436 root      20   0   15260    408    192 S   0.0  0.0   0:00.07 upstart-so+
  529 root       0 -20       0      0      0 S   0.0  0.0   0:00.21 kworker/u9+
  560 root      20   0       0      0      0 S   0.0  0.0   0:00.41 jbd2/sda6-8
  561 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-c+
  630 message+  20   0   40440   2644    976 S   0.0  0.0   0:01.08 dbus-daemon
  669 root      20   0  330236   4324   3188 S   0.0  0.1   0:00.02 ModemManag+
  673 root      20   0   19292   1444   1180 S   0.0  0.0   0:00.00 bluetoothd
  700 root      10 -10       0      0      0 S   0.0  0.0   0:00.00 krfcommd
  744 root      20   0   15276    652    392 S   0.0  0.0   0:00.03 upstart-fi+
  768 syslog    20   0  255844   1160    780 S   0.0  0.0   0:00.06 rsyslogd
  778 root      20   0   43544   1872   1464 S   0.0  0.0   0:00.09 systemd-lo+
  825 avahi     20   0   32352   1392   1124 S   0.0  0.0   0:00.04 avahi-daem+
  833 avahi     20   0   32224    464    212 S   0.0  0.0   0:00.00 avahi-daem+
  882 root      20   0   20016    932    768 S   0.0  0.0   0:00.00 getty
  886 root      20   0   20016    924    768 S   0.0  0.0   0:00.00 getty
  893 root      20   0   20016    928    768 S   0.0  0.0   0:00.00 getty
  894 root      20   0   20016    928    768 S   0.0  0.0   0:00.00 getty
  897 root      20   0   20016    928    768 S   0.0  0.0   0:00.00 getty
  904 root      20   0  356708   6860   5120 S   0.0  0.1   0:00.59 NetworkMan+
  943 root      20   0   61364   3004   2328 S   0.0  0.0   0:00.00 sshd
  968 kernoops  20   0   37144   1016    692 S   0.0  0.0   0:00.36 kerneloops
  971 root      20   0  292640   4508   3564 S   0.0  0.1   0:00.08 lightdm
  973 root      20   0    4368    680    508 S   0.0  0.0   0:00.10 acpid
  982 root      20   0   19188    792    564 S   0.0  0.0   0:01.57 irqbalance
  983 root      20   0   23656   1020    764 S   0.0  0.0   0:00.03 cron
  984 root      20   0   75352   3352   2456 S   0.0  0.0   0:00.03 cups-brows+
 1038 root      20   0  303076   7980   3720 S   0.0  0.1   0:01.32 polkitd
 1063 root      20   0  302344   5072   3912 S   0.0  0.1   0:00.64 accounts-d+
 1095 root      20   0   20016    920    768 S   0.0  0.0   0:00.00 getty
 1103 whoopsie  20   0  363388   5204   3812 S   0.0  0.1   0:00.01 whoopsie
 1152 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
 1195 root      20   0   10232   3648   1356 S   0.0  0.0   0:00.00 dhclient
 1265 root      20   0  304888   4440   3520 S   0.0  0.1   0:00.12 upowerd
 1499 rtkit     21   1  168916   1284   1060 S   0.0  0.0   0:00.13 rtkit-daem+
 1567 nobody    20   0   35224   1508   1248 S   0.0  0.0   0:00.18 dnsmasq
 1777 ntp       20   0   33504   2104   1500 S   0.0  0.0   0:00.79 ntpd
 1811 root      20   0   76856   3752   2640 S   0.0  0.0   0:00.01 cupsd
 1816 lp        20   0   63156   1956   1452 S   0.0  0.0   0:00.00 dbus
 2098 tusr       9 -11  294260   4872   3176 S   0.0  0.1   0:00.10 pulseaudio
 2147 colord    20   0  310980   6308   4804 S   0.0  0.1   0:00.18 colord
 2317 root      20   0  451872   6732   4216 S   0.0  0.1   0:08.19 udisksd
 2720 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:2
 3119 root      20   0       0      0      0 R   0.0  0.0   0:10.00 kworker/0:2
 4105 root      20   0  192856  20472   7028 S   0.0  0.3   0:00.34 python3
 4509 root      20   0  170492   3804   2944 S   0.0  0.0   0:00.04 lightdm
 4732 tusr      20   0  249008   4932   3968 S   0.0  0.1   0:00.03 gnome-keyr+
 4734 tusr      20   0   40200   2552   1532 S   0.0  0.0   0:00.20 init
 4803 tusr      20   0   10616    312      0 S   0.0  0.0   0:00.00 ssh-agent
 4810 tusr      20   0   41376   2768    868 S   0.0  0.0   0:00.71 dbus-daemon
 4818 tusr      20   0   22300   1156    980 S   0.0  0.0   0:00.01 upstart-ev+
 4820 tusr      20   0   78200   4440   3880 S   0.0  0.1   0:00.04 window-sta+
 4830 tusr      20   0  559124  12984   8312 S   0.0  0.2   0:00.81 bamfdaemon
 4834 tusr      20   0   30784    452    184 S   0.0  0.0   0:00.00 upstart-fi+
 4836 tusr      20   0  367688   4408   3656 S   0.0  0.1   0:00.01 at-spi-bus+
 4838 tusr      20   0   22376    688    396 S   0.0  0.0   0:00.10 upstart-db+
 4840 tusr      20   0   22308    420    204 S   0.0  0.0   0:00.02 upstart-db+
 4844 tusr      20   0   39380   2040   1432 S   0.0  0.0   0:00.04 dbus-daemon
 4847 tusr      20   0  124912   3256   2680 S   0.0  0.0   0:00.04 at-spi2-re+
 4853 tusr      20   0  196640   5128   2484 S   0.0  0.1   0:00.04 gvfsd
 4863 tusr      20   0  360428   3904   3120 S   0.0  0.0   0:00.01 gvfsd-fuse
 4875 tusr      20   0  295768   6272   3484 S   0.0  0.1   0:00.01 ibus-dconf
 4877 tusr      20   0  489276  16060  11008 S   0.0  0.2   0:00.91 ibus-ui-gt+
 4884 tusr      20   0  396412   8044   6208 S   0.0  0.1   0:00.02 ibus-x11
 4888 tusr      20   0  749564  18832  12252 S   0.0  0.2   0:00.46 unity-sett+
 4895 tusr      20   0  715508  25732  17552 S   0.0  0.3   0:00.32 hud-service
 4903 tusr      20   0  863532  11880   8180 S   0.0  0.1   0:00.23 gnome-sess+
 4917 tusr      20   0  728884  19112  11940 S   0.0  0.2   0:01.11 unity-pane+
 4971 tusr      20   0  604740  13828   8552 S   0.0  0.2   0:00.18 indicator-+
 4972 tusr      20   0  365536   4368   3452 S   0.0  0.1   0:00.08 indicator-+
 4975 tusr      20   0  293748   3992   3280 S   0.0  0.0   0:00.01 indicator-+
 4981 tusr      20   0  295644   4316   3496 S   0.0  0.1   0:00.01 indicator-+
 4983 tusr      20   0  968788  13804   6676 S   0.0  0.2   0:00.23 indicator-+
 4986 tusr      20   0  569432   6604   4860 S   0.0  0.1   0:00.14 indicator-+
 4996 tusr      20   0  530072  12424   8580 S   0.0  0.2   0:00.10 indicator-+
 5001 tusr      20   0  906388   4772   3624 S   0.0  0.1   0:00.14 indicator-+
 5017 tusr      20   0  286748   7008   3880 S   0.0  0.1   0:00.03 indicator-+
 5019 tusr      20   0  350144  10808   7620 S   0.0  0.1   0:00.11 notify-osd
 5030 tusr      20   0  219944   4072   3368 S   0.0  0.0   0:00.57 ibus-engin+
 5042 tusr      20   0  910408  13292   8416 S   0.0  0.2   0:00.07 evolution-+
 5113 tusr      20   0  178304   2672   2096 S   0.0  0.0   0:00.05 dconf-serv+
 5129 tusr      20   0  826000  44616   8452 S   0.0  0.5   0:00.18 evolution-+
 5136 tusr      20   0  924960  33512  24868 S   0.0  0.4   0:01.22 nautilus
 5139 tusr      20   0  341304  10176   7184 S   0.0  0.1   0:00.07 polkit-gno+
 5140 tusr      20   0  410720  10148   7172 S   0.0  0.1   0:00.10 unity-fall+
 5143 tusr      20   0  675948  20772  13144 S   0.0  0.3   0:00.21 nm-applet
 5233 tusr      20   0  311444   5844   3984 S   0.0  0.1   0:00.10 gvfs-udisk+
 5257 tusr      20   0  285956   3296   2636 S   0.0  0.0   0:00.01 gvfs-afc-v+
 5268 tusr      20   0  200276   2744   2212 S   0.0  0.0   0:00.01 gvfs-mtp-v+
 5279 tusr      20   0  212444   5084   2384 S   0.0  0.1   0:00.01 gvfs-gphot+
 5285 tusr      20   0   58252   3616   2016 S   0.0  0.0   0:00.03 gconfd-2
 5327 tusr      20   0  374196   4348   3516 S   0.0  0.1   0:00.04 gvfsd-trash
 5339 tusr      20   0  270376   4824   2264 S   0.0  0.1   0:00.01 gvfsd-burn
 5355 tusr      20   0  659608  21144  13212 S   0.0  0.3   0:01.85 gnome-term+
 5361 tusr      20   0   14824    800    640 S   0.0  0.0   0:00.00 gnome-pty-+
 5362 tusr      20   0   26960   3868   1672 S   0.0  0.0   0:00.07 bash
 5374 tusr      20   0  457360  12080   8808 S   0.0  0.1   0:00.08 telepathy-+
 5382 tusr      20   0  336572   8076   6496 S   0.0  0.1   0:00.06 mission-co+
 5465 tusr      20   0  495532   9784   5856 S   0.0  0.1   0:00.14 zeitgeist-+
 5470 tusr      20   0  363792   5544   4312 S   0.0  0.1   0:00.12 zeitgeist-+
 5476 tusr      20   0  257692  11160   7556 S   0.0  0.1   0:00.27 zeitgeist-+
 5486 tusr      20   0   11412    360    280 S   0.0  0.0   0:00.00 cat
 5496 tusr      20   0 1227848 305748  58628 S   0.0  3.7   2:34.33 firefox
 5521 tusr      20   0  287224   5836   3092 S   0.0  0.1   0:00.00 unity-weba+
 5591 tusr      20   0  506392  11664   8392 S   0.0  0.1   0:00.10 update-not+
 5610 tusr      20   0  385268   4720   3768 S   0.0  0.1   0:00.05 deja-dup-m+
 5649 tusr      20   0  251640   6224   5036 S   0.0  0.1   0:00.02 geoclue-ma+
 5653 tusr      20   0  336584   9556   5996 S   0.0  0.1   0:00.04 ubuntu-geo+
 5714 tusr      20   0  586032  13020   8000 S   0.0  0.2   0:00.57 unity-scop+
 5724 tusr      20   0  667640  20496  10000 S   0.0  0.3   0:00.66 unity-scop+
 5726 tusr      20   0 1135120  11316   6728 S   0.0  0.1   0:00.30 unity-file+
 5764 tusr      20   0 2785008  72404  43992 S   0.0  0.9   0:03.38 unity-cont+
 5793 root      20   0       0      0      0 S   0.0  0.0   0:00.28 kworker/u8+
 5975 tusr      20   0   26960   3864   1672 S   0.0  0.0   0:00.07 bash
 6064 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u8+
 6102 tusr      20   0  939672  28400  17720 S   0.0  0.3   0:02.76 gedit

```

I, also, executed the "lshw" command & the output is as below:

~$: sudo lshw -c display
[sudo] password for xxx: 
  *-display               
       description: VGA compatible controller
       product: ES1000
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:18 memory:d8000000-dfffffff ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff

---

### Post by ptn107 on 2014-08-11
Looks like compiz is going nuts.

---

### Post by whitesmith on 2014-08-11
Yes, your desktop looks like the culprit. There are several paths that you can follow. First of all let's try the tried-and-true Restart Trick. There may be something screwy tucked away in some component that will be corrected by restarting. Before doing that, try these maintenance commands (their order is important!):```
apt-get update
```and then:```
apt-get upgrade
```and finally:```
apt-get check
```Now you can restart the machine. Tell me what happens. Were there improvements in execution time or not?

[edit] All 3 commands must be run as root.

---

### Post by Impavidus on 2014-08-11
The next thing to try is the graphics driver, but don't try downloading the driver from the nvidia website and installing it manually. There are easier ways.

If you want to preserve formatting of your terminal output on the forum, put it between [noparse]```
code tags
```[/noparse]. You can modify your long post.

---

### Post by nerdtron on 2014-08-11
It is most likely the display driver. I believe llvmpipe means software rendering mode so it taxes the CPU. Why install GUI on a server hardware?

Anyway have you tried changing to a proprietary nvidia driver? System Settings > Software & Updates > Additional Drivers

---

### Post by ubtkrak on 2014-08-11
I did executed the 3 commands in the following order:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get check

It did go through some updates & upgrades.

After the restart, the response is still very sluggish. The top command shows about 80% CPU usage by "compiz". The "Xorg" is showing about 30+ % CPU usage. In the terminal window, after typing the command, I still have to wait for the typed letters to appear. If I open more windows, I'm sure the CPU usage will go up.

Like mentioned below, it looks like software rendering mode is being used.

---

### Post by ubtkrak on 2014-08-11
> **Impavidus said:**
> The next thing to try is the graphics driver, but don't try downloading the driver from the nvidia website and installing it manually. There are easier ways.
Thanks for the response. So, which are the other ways of installing the nVidia graphics driver?

> **Impavidus said:**
> If you want to preserve formatting of your terminal output on the forum, put it between [noparse]```
code tags
```[/noparse]. You can modify your long post.
Yes, the code tags did the preservation of the format. Thanks again for the tip.

---

### Post by ubtkrak on 2014-08-11
> **nerdtron said:**
> Why install GUI on a server hardware? 
The reason for the GUI is because this is my very first Linux experience. I will be working on application development and wanted to do it on Linux. My friend had this server hardware lying around, unused and he has been nice enough to give the server for my use. So, new HDD has been installed and all the software is being installed fresh. Just using the command lines will take a lot more effort on my part.

> **nerdtron said:**
> Anyway have you tried changing to a proprietary nvidia driver? System Settings > Software & Updates > Additional Drivers
When I go to "Software & updates -> Additional Drivers ", I see the following message:
"No additional drivers available."

---

### Post by Arkanglas on 2014-08-12
I looked at your post because I'm about to build another machine with an nVidia vid card.

I hate to be the bearer of bad news, but the reason why you have miserable performance might be as simple as the card is no longer actively supported by either nVidia or the Linux community.  In the realm of PCs, that card is an outright fossil - dating from at least 10 years ago.  Just out of curiosity, I looked for the driver at the nVidia website and they don't even have an appropriate catalyst package for it.  Granted, I ran through the site and didn't stop to do a detailed search, so I could be mistaken.  But still, even from the aspect of  hardware considerations a card that old on a 64-bit machine with the latest linux distro installed on it will really hold your system back.  I didn't look at the latest supported hardware list for Ubuntu, but I'd be willing to say that you won't find your vid card listed there.  If this is true, it would explain a lot, I would think.

By no longer supported, I mean that there probably was a driver for your particular card at some point in time.  But with the advances made in both software (linux kernels, windows managers, and so on) and hardware, the card just isn't relevant to the linux world anymore and so its drivers were put in the archives with all of the previous editions of linux, which are no longer supported.  So you might find a driver for it in a repository or archive somewhere, but then you'd probably have to recompile it for your kernel, and then plug the mod in, then tweak it to perform correctly with your x-server.  I think we'd all agree that this course of action would be more trouble than its worth.

To be honest, you'd be better off spending a little coin and getting a newer, supported vid card that will work in your mobo.  Barring that, keep following the this thread because the others are trying to steer you in the right direction.

Hope it works out for ya!  :KS

---

### Post by coffeecat on 2014-08-12
@ubttrak, there appears to be an inconsistency between two of your posts. In post #1 you say:

> **ubtkrak said:**
> The graphics card is NVIDIA CK8-04 Pro (System details says "Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits")).

In post #3 you give this output for lshw:

> **ubtkrak said:**
> ```

~$: sudo lshw -c display
[sudo] password for xxx: 
  *-display               
       description: VGA compatible controller
       product: ES1000
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:18 memory:d8000000-dfffffff ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
```

Nvidia or AMD? Which are you using? I'm not familiar with the AMD ES1000, but googling suggest this could be an onboard graphics device. The output of lshw tells us it is using the open source radeon driver. 

Is your nvidia card not enabled in your BIOS, or did you leave out some of the lshw output?

---

### Post by Arkanglas on 2014-08-12
Just out of curiosity, I searched for your vid card in supported hardware.  CK8-04 returns nothing, while CK804 returns a small and precise list of hardware, none of which is a video card.


[ATTACH=CONFIG]255413[/ATTACH]


So it would seem that your card isn't supported anymore.[-(

There's also what Coffee Cat wrote in the reply above.  A conflict will slow things to a crawl as well.

---

### Post by Jonathan Precise on 2014-08-12
llvmpipe looks like the culprit. Try a lighter version, like Xubuntu (xfce), which is made for older PCs/graphics cards where the rendering is done by the CPU.

---

### Post by ubtkrak on 2014-08-12
> **coffeecat said:**
> @ubttrak, there appears to be an inconsistency between two of your posts. In post #1 you say:



In post #3 you give this output for lshw:



Nvidia or AMD? Which are you using? I'm not familiar with the AMD ES1000, but googling suggest this could be an onboard graphics device. The output of lshw tells us it is using the open source radeon driver. 

Is your nvidia card not enabled in your BIOS, or did you leave out some of the lshw output?
Sorry for the confusion I've caused about the hardware. Other than main hardware components like cpu, memory.... I'm not familiar with the other internal components like controllers etc. The Dell spec sheet for this m/c (please see the screen shot below) says that the chipset is "nVidia CK-08 Pro". So I assumed that is the graphics card chipset.

[ATTACH=CONFIG]255419[/ATTACH]

The output from the "lshw" command that I posted is complete i.e. I didn't leave out any.

Please find below the output from the "lspci":
```

PowerEdge-T105:~$ lspci
00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a4)
00:07.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev f2)
00:0b.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:08.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] ES1000 (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express

```

So, what graphics card is being used? Is it the embedded AMD ES1000? Thanks for your response.

---

### Post by ubtkrak on 2014-08-12
> **Arkanglas said:**
> Just out of curiosity, I searched for your vid card in supported hardware.  CK8-04 returns nothing, while CK804 returns a small and precise list of hardware, none of which is a video card.





So it would seem that your card isn't supported anymore.[-(

There's also what Coffee Cat wrote in the reply above.  A conflict will slow things to a crawl as well.

Thank you very much for looking up the information. I appreciate it. I have replied to coffeecat's posting above with more information about the computer's hardware. Since the spec sheet said that the chipset is nVidia, I assumed that is the GPU.

So, is the graphics card AMD ES1000?

---

### Post by ubtkrak on 2014-08-12
> **Jonathan Precise said:**
> llvmpipe looks like the culprit. Try a lighter version, like Xubuntu (xfce), which is made for older PCs/graphics cards where the rendering is done by the CPU.

Thanks for your response. Which is better xfce or Mint? I had tried the live version of the Mint 17 (Cinnamon) before I ended up installing ubuntu. Mint GUI was much faster & smoother than Ubuntu.

---

### Post by nerdtron on 2014-08-12
I think your graphics card is AMD ES1000. The NVIDIA bits maybe are part of the motherboard.

Oh and since you like a GUI, try Xubuntu or Lubuntu as they don't require 3D graphics, plus they are lightweight which is good if you are going to use this as a server.

---

### Post by coffeecat on 2014-08-12
> **ubtkrak said:**
> The Dell spec sheet for this m/c (please see the screen shot below) says that the chipset is "nVidia CK-08 Pro". So I assumed that is the graphics card chipset.

The spec sheet and the output of lspci are saying the same thing. I've not seen a nvidia/AMD hybrid like this before, but it seems that the nvidia chipset includes such things as your USB controller and IDE interface, but that the motherboard graphics is the AMD device.

---

### Post by ubtkrak on 2014-08-12
> **coffeecat said:**
> The spec sheet and the output of lspci are saying the same thing. I've not seen a nvidia/AMD hybrid like this before, but it seems that the nvidia chipset includes such things as your USB controller and IDE interface, but that the motherboard graphics is the AMD device.

Found some more information about the graphics card in my server. As mentioned by you and other posters above, the graphics card is a legacy one, ATI ES1000 which was introduced back in 2005. It is also known as Radeon 7000. Going by the following site (link below), it says the following:

[I]**Supported, but Hardware is Too Old for Unity**

These cards will not run Ubuntu's Unity desktop with 3D acceleration.  They will still run Unity, but the CPU will be used for basic drawing  and performance may suffer. If you have one of these cards, a lighter  desktop (such as xfce or lxde, found in Xubuntu and Lubuntu  respectively) is recommended.
[/I] :
RV100                    Radeon 7000(VE), M6, RN50/_ES1000 (2D only)_
:

More info can be found at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


I understand that open source X.Org driver can be used for this card. The following X.org website says:
*"Driver for ATI/AMD Radeon based video chips, everything from Radeon 7000 (R100) to Radeon HD 7000 (Southern Islands) series.*"

[http://www.x.org/wiki/radeon/](http://www.x.org/wiki/radeon/)

Since, ATI ES1000 can only support 2D, as mentioned by **Jonathan Precise** the only proper choices I have is either Xubuntu or Lubuntu.

I had put considerable effort & time in installing Ubuntu 14.04, oracle 12c and other software on this machine. But, I had not done 
my homework correctly before starting the installation. I had not realized that the graphics card could be such a big issue in Linux. 
I have been using MS Windows and never experienced graphics card problem for the GUI even for the servers.

Anyway, I think I have to bite the bullet and start all over again.

So, my question to everybody is, is there anything that I need to take care of or make sure that it exists before I jump into Xubuntu?

Thanks so much for all your help. I really appreciate it.

---

### Post by QIII on 2014-08-12
Hello!

You can avoid a reinstallation by adding another DE (Desktop Environment) and using that.  You'll only pay for that with a small amount of disk space used.

As far as the trouble with your card, you can thank AMD/ATI for non-support.  They write the drivers, not Microsoft or any distro provider.

If the open source driver does not work well, remember that the developers are trying to peer into a black box to see what they can get out of it.

---

### Post by ubtkrak on 2014-08-12
> **QIII said:**
> Hello!

You can avoid a reinstallation by adding another DE (Desktop Environment) and using that.  You'll only pay for that with a small amount of disk space used.
Thank you for your suggestion. If this is going to work, that is what I want to do. I have about 7GB of disk space for the software installation. In my /home partition, I have more than 600 GB. Can you please suggest what DE options I have? Also, if possible, can you please provide pointers to how to go about installing these DE? All I need is a basic GUI to manage things on the computer. I don't need any fancy stuff.

> **QIII said:**
> As far as the trouble with your card, you can thank AMD/ATI for non-support.  They write the drivers, not Microsoft or any distro provider.

If the open source driver does not work well, remember that the developers are trying to peer into a black box to see what they can get out of it.
Yes, you are right. I do understand that. Users like me are grateful for the open source developers. Because of them, we are able to use a lot of things for free. And for AMD/ATI, it is all about revenue/making money. That is how businesses work. I accept that :)

---

### Post by coffeecat on 2014-08-12
I see from your spec sheet that your motherboard has PCIe slots. If you want to be running the Unity desktop, it wouldn't cost much to purchase a suitable graphics card. You don't need anything expensive. Unity needs more graphics oomph than that on-board AMD device can provide, but not that much oomph. For instance, I am using a modest AMD Radeon HD 6450 PCIe card with the same open source radeon driver as is driving your GPU. Unity is just fine - no lag, no problem.

---

