---
title: "[SOLVED] Does anyone know what this is?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by madmak on 2008-07-31
Hia guys i only started using ubuntu a couple of months ago and have been able to find the answers to any questions iv had by searching on this forum or google but iv noticed something strange on my system that i cant find an answer to.

I rebooted my pc about 20 mins ago and when it rebooted it was unable to start x server in gnome so i ran fsck and powerd off my computer and then switched it on again and it worked fine but before i ran fsck i got a message saying you have mail but the only mail client i use is through opera and opera was unable to start at that time because of the x server problem?

Iv also just installed firestarter a couple of mins ago and noticed theres a connection running at about 13 to 30 KB/s even when im not using anything. The connections source is 127.0.0.1 and the destination is 127.0.0.1 on port 31000. I know this is localhost but i havent got a clue what it is has anyone ever had anything like this before or know what it could be? The reason its annoying me is that i use my mobile phone as a modem so my normal speed is only about 50KB/s anyway and i seem to be uploading more data than im downloading.

---

### Post by saj0577 on 2008-07-31
Do you have more then one user on the computer as you can send email between users. Email is not just from one web address to another, you can send it from say your account to your partners account. Without it gonig through any external mail server.

Saj

---

### Post by madmak on 2008-07-31
> **saj0577 said:**
> Do you have more then one user on the computer as you can send email between users. Email is not just from one web address to another, you can send it from say your account to your partners account. Without it gonig through any external mail server.

Saj

No Saj im the only person who ever uses the computer so theres only my account on it. It just seemed a little bit strange when i seen the message and noticed the connection on firestarter after it.

---

### Post by saj0577 on 2008-07-31
Okay I dont know much about that I will read up and get back to you.

Saj

---

### Post by saj0577 on 2008-07-31
Well I know instantly from reading the OP again the network usage is from your own computer.

127.0.0.1 Is your computer that you are using.
Localhost

EDIT: IL keep updating this post with notes of my progress :)

Just type ```
mail
``` in terminal
Press the number to read it.
And type ```
quit
``` to exit.

It will say it has stored some in some directories:
Saved X messages in /home/username/mbox
Held X messages in /var/mail/username


On mine i have 6 from root all about cron jobs.

Saj

---

### Post by eightmillion on 2008-07-31
Do you run a program called R1Soft&#8217;s Continuous Data Protection? Also, could you paste the output of 'ps aux'?

> Iv also just installed firestarter a couple of mins ago and noticed theres a connection running at about 13 to 30 KB/s even when im not using anything. The connections source is 127.0.0.1 and the destination is 127.0.0.1 on port 31000. I know this is localhost but i havent got a clue what it is has anyone ever had anything like this before or know what it could be? The reason its annoying me is that i use my mobile phone as a modem so my normal speed is only about 50KB/s anyway and i seem to be uploading more data than im downloading.

If the source and destination is localhost, then it wouldn't ever touch your modem. You don't have to worry about it using bandwith.

---

### Post by saj0577 on 2008-07-31
Read my post and it should have all needed to solve your problem. 

[http://ubuntuforums.org/showpost.php?p=5497690&postcount=5](http://ubuntuforums.org/showpost.php?p=5497690&postcount=5)

Saj

---

### Post by annda on 2008-07-31
> **madmak said:**
> i got a message saying you have mail but the only mail client i use is through opera and opera was unable to start at that time because of the x server problem?

looks like a standard error message mailed to the owner of the culprit application (=you) by the application itself. you can ignore it.

---

### Post by madmak on 2008-07-31
> **saj0577 said:**
> Well I know instantly from reading the OP again the network usage is from your own computer.

127.0.0.1 Is your computer that you are using.
Localhost

EDIT: IL keep updating this post with notes of my progress :)

Just type ```
mail
``` in terminal
Press the number to read it.
And type ```
quit
``` to exit.

It will say it has stored some in some directories:
Saved X messages in /home/username/mbox
Held X messages in /var/mail/username


On mine i have 6 from root all about cron jobs.

Saj

Thanks Saj thats what the new mail must have been i had 14 new messages from root, i forgot to try using mail on the command line after i had fixed the x server lol. thanks again mate.

---

### Post by madmak on 2008-07-31
> **eightmillion said:**
> Do you run a program called R1Soft&#8217;s Continuous Data Protection? Also, could you paste the output of 'ps aux'?



If the source and destination is localhost, then it wouldn't ever touch your modem. You don't have to worry about it using bandwith.

I dont think im using R1Soft&#8217;s Continuous Data Protection unless it benn installed allong with something else this is the output of my ps aux

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   2844   520 ?        Ss   19:07   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   19:07   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   19:07   0:00 [migration/0]
root         4  0.1  0.0      0     0 ?        S<   19:07   0:09 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   19:07   0:00 [watchdog/0]
root         6  0.1  0.0      0     0 ?        S<   19:07   0:11 [events/0]
root         7  0.0  0.0      0     0 ?        S<   19:07   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   19:07   0:02 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   19:07   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   19:07   0:00 [kacpi_notify]
root       105  0.0  0.0      0     0 ?        S<   19:07   0:00 [kseriod]
root       137  0.0  0.0      0     0 ?        S    19:07   0:00 [pdflush]
root       138  0.1  0.0      0     0 ?        S<   19:07   0:09 [kswapd0]
root       181  0.0  0.0      0     0 ?        S<   19:07   0:00 [aio/0]
root      1436  0.0  0.0      0     0 ?        S<   19:07   0:00 [ata/0]
root      1440  0.0  0.0      0     0 ?        S<   19:07   0:00 [ata_aux]
root      1463  0.0  0.0      0     0 ?        S<   19:07   0:00 [ksuspend_usbd]
root      1469  0.0  0.0      0     0 ?        S<   19:07   0:00 [khubd]
root      1473  0.0  0.0      0     0 ?        S<   19:07   0:00 [scsi_eh_0]
root      1481  0.0  0.0      0     0 ?        S<   19:07   0:00 [scsi_eh_1]
root      2471  0.0  0.0      0     0 ?        S<   19:07   0:01 [kjournald]
root      2676  0.0  0.1   2416   352 ?        S<s  19:08   0:02 /sbin/udevd --daemon
root      3033  0.0  0.0      0     0 ?        S<   19:09   0:00 [kgameportd]
root      4333  0.0  0.1   1716   424 tty4     Ss+  19:09   0:00 /sbin/getty 38400 tty4
root      4335  0.0  0.1   1716   424 tty5     Ss+  19:09   0:00 /sbin/getty 38400 tty5
root      4339  0.0  0.1   1716   424 tty2     Ss+  19:09   0:00 /sbin/getty 38400 tty2
root      4342  0.0  0.1   1716   424 tty3     Ss+  19:09   0:00 /sbin/getty 38400 tty3
root      4346  0.0  0.1   1716   424 tty6     Ss+  19:09   0:00 /sbin/getty 38400 tty6
root      4509  0.0  0.2   2456   592 ?        Ss   19:09   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4536  0.0  0.0      0     0 ?        S<   19:09   0:00 [kondemand/0]
syslog    4616  0.0  0.2   1936   560 ?        Ss   19:09   0:00 /sbin/syslogd -u syslog
root      4671  0.0  0.1   1868   416 ?        S    19:09   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4673  0.0  0.1   3168   408 ?        Ss   19:09   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       4695  0.0  0.1   2844   456 ?        Ss   19:09   0:01 /usr/bin/dbus-daemon --system
root      4711  0.0  0.4   4696  1032 ?        Ss   19:09   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.p
root      4725  0.0  0.2   3504   736 ?        Ss   19:09   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/Networ
root      4738  0.0  0.2   4108   608 ?        Ss   19:09   0:00 /usr/bin/system-tools-backends
avahi     4758  0.0  0.2   2892   736 ?        Ss   19:09   0:00 avahi-daemon: running [mark-desktop.local]
avahi     4759  0.0  0.0   2756   204 ?        Ss   19:09   0:00 avahi-daemon: chroot helper
root      4799  0.0  0.3   5916   744 ?        Ss   19:09   0:00 /usr/sbin/cupsd
116       5054  0.0  0.1   5904   452 ?        Ss   19:09   0:00 /usr/sbin/exim4 -bd -q30m
root      5086  0.0  0.1   1808   356 ?        S<   19:09   0:00 /usr/bin/nasd -b
privoxy   5137  0.0  0.2  35760   592 ?        Ss   19:09   0:02 /usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy
root      5154  0.0  0.2   8080   580 ?        Ss   19:09   0:00 /usr/sbin/winbindd
root      5162  0.0  0.2   8080   520 ?        S    19:09   0:00 /usr/sbin/winbindd
root      5211  0.0  0.2   2020   532 ?        Ss   19:09   0:01 /usr/sbin/dhcdbd --system
111       5230  0.0  0.6   6176  1628 ?        Ss   19:09   0:02 /usr/sbin/hald
root      5233  0.0  0.4   7948  1140 ?        Ssl  19:09   0:00 /usr/sbin/console-kit-daemon
root      5295  0.0  0.3   3348   748 ?        S    19:09   0:00 hald-runner
111       5315  0.0  0.2   2200   588 ?        S    19:09   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5324  0.0  0.3   3416   800 ?        S    19:09   0:01 hald-addon-input: Listening on /dev/input/event1 /dev/input/event4 /dev/inpu
root      5334  0.0  0.3   3420   776 ?        S    19:09   0:00 hald-addon-storage: no polling on /dev/fd0 because it is explicitly disabled
root      5341  0.1  0.3   3420   876 ?        S    19:09   0:07 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5362  0.0  0.2   3168   672 ?        Ss   19:09   0:00 /usr/sbin/hcid -x -s
root      5369  0.0  0.0      0     0 ?        S<   19:09   0:00 [btaddconn]
root      5370  0.0  0.0      0     0 ?        S<   19:09   0:00 [btdelconn]
root      5383  0.0  0.2   3016   704 ?        S    19:09   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5384  0.0  0.0      0     0 ?        S<   19:09   0:00 [krfcommd]
root      5387  0.0  0.3   3080   800 ?        S    19:09   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5420  0.0  0.2  14060   676 ?        Ss   19:09   0:00 /usr/sbin/gdm
root      5421  0.0  0.5  14516  1340 ?        S    19:09   0:00 /usr/sbin/gdm
root      5426 15.2  6.5  34580 16292 tty7     Rs+  19:09  16:40 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daemon    5465  0.0  0.1   1980   284 ?        Ss   19:09   0:00 /usr/sbin/atd
root      5481  0.0  0.2   2100   684 ?        Ss   19:09   0:00 /usr/sbin/cron
mark      5621  0.2  0.2  10068   496 ?        SNl  19:09   0:19 /home/mark/Freenet/./bin/wrapper-linux-x86-32 /home/mark/Freenet/./wrapper.c
root      5642  0.0  0.1   1716   424 tty1     Ss+  19:09   0:00 /sbin/getty 38400 tty1
mark      5645 15.0 17.9 347980 44452 ?        SNl  19:09  16:26 java -Dnetworkaddress.cache.ttl=0 -Dnetworkaddress.cache.negative.ttl=0 -ena
mark      5677  0.0  1.1   7376  2944 ?        S    19:10   0:04 /usr/lib/libgconf2-4/gconfd-2 4
mark      5679  0.0  0.4  14340  1096 ?        S    19:10   0:00 /usr/bin/gnome-keyring-daemon -d --login
mark      5680  0.0  1.4  28884  3480 ?        Ssl  19:10   0:00 x-session-manager
mark      5799  0.0  1.0  23060  2616 ?        Ss   19:10   0:00 /usr/bin/seahorse-agent --execute x-session-manager
mark      5803  0.0  0.2   2696   728 ?        Ss   19:10   0:00 dbus-daemon --fork --print-address 24 --print-pid 26 --session
mark      5804  0.1  1.5  44504  3828 ?        Sl   19:10   0:09 gnome-settings-daemon
mark      5808  0.0  0.5  28496  1392 ?        Sl   19:10   0:04 /usr/bin/pulseaudio --log-target=syslog
mark      5813  0.0  0.4   5772  1232 ?        S    19:10   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
mark      5827  0.6  0.5  15356  1476 ?        Ss   19:10   0:40 gnome-screensaver
mark      5829  1.0  2.6  21288  6664 ?        S    19:10   1:06 /usr/bin/metacity --replace --sm-client-id default0
mark      5830  1.2  5.1  47336 12740 ?        S    19:10   1:24 gnome-panel --sm-client-id default1
mark      5832  0.5  7.4  88668 18460 ?        Sl   19:10   0:36 nautilus --no-default-window --sm-client-id default2
mark      5848  0.0  0.8  31860  2164 ?        Ssl  19:10   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-outp
mark      5858  0.0  0.6   5368  1528 ?        S    19:10   0:00 /usr/lib/gvfs/gvfsd
mark      5864  0.0  0.4  37376  1112 ?        Ssl  19:10   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/mark/.gvfs
mark      5871  0.3  2.7  25768  6868 ?        S    19:10   0:21 update-notifier
mark      5877  0.0  1.4  24268  3560 ?        S    19:10   0:01 python /usr/share/system-config-printer/applet.py
mark      5883  0.0  0.9  20692  2400 ?        Ss   19:10   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
mark      5884  0.0  1.2  23472  3104 ?        Ss   19:10   0:01 gnome-power-manager
mark      5888  0.0  0.5   5368  1364 ?        S    19:10   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
mark      5893  0.0  0.5  22032  1464 ?        S    19:10   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
mark      5906  0.0  1.7  22528  4412 ?        S    19:10   0:02 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_Tra
mark      5921  0.0  2.3  44192  5724 ?        Sl   19:10   0:02 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerAp
mark      5924  0.0  2.4  26256  6032 ?        S    19:10   0:02 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=
mark      6024  0.0  2.0  23472  4988 ?        S    19:11   0:05 /usr/lib/notification-daemon/notification-daemon
mark      8520 12.4 26.7 171016 66124 ?        Sl   19:28  11:18 /usr/lib/opera/9.51/opera
mark      9797  0.7  4.0  74908  9960 ?        Rl   20:00   0:27 gnome-terminal -x /home/Dialer.sh
mark      9799  0.0  0.3   2912   784 ?        S    20:00   0:00 gnome-pty-helper
mark      9800  0.0  0.1   1772   372 pts/0    Ss+  20:00   0:00 /bin/sh /home/Dialer.sh
mark      9801  0.3  0.3   9016   868 pts/0    S+   20:00   0:13 wvdial
root      9803  0.0  0.3   2908   756 pts/0    S    20:00   0:00 /usr/sbin/pppd 921600 modem crtscts defaultroute usehostname -detach user ge
proxy     9946  0.0  0.1   2164   280 ?        Ss   20:00   0:00 /usr/bin/polipo -c /etc/polipo/config pidFile=/var/run/polipo/polipo.pid dae
mark     10788  0.0  0.1   2860   428 ?        S    20:19   0:00 /usr/lib/opera/9.51/operaplugincleaner 8520
clamav   11167  0.6  0.2   3000   724 ?        Ss   20:24   0:14 /usr/bin/freshclam -d --quiet
clamav   12109  1.7  1.0  53288  2584 ?        Ss   20:36   0:23 /usr/sbin/clamd
root     12286  0.0  0.0      0     0 ?        S    20:41   0:00 [pdflush]
mark     12704  0.2  1.2   5660  3040 pts/1    Ss   20:52   0:00 bash
mark     12740  0.0  0.4   2644  1004 pts/1    R+   20:59   0:00 ps aux


```

---

### Post by eightmillion on 2008-07-31
I think it's ClamAV that's connecting on port 31000. Could you paste the output of 'netstat -a' to make sure?

---

### Post by madmak on 2008-07-31
> **eightmillion said:**
> I think it's ClamAV that's connecting on port 31000. Could you paste the output of 'netstat -a' to make sure?

Iv only just installed ClamAV after i noticed that connection mate heres the output of netstat -a
```
mark@mark-desktop:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:32000         *:*                     LISTEN     
tcp        0      0 *:8000                  *:*                     LISTEN     
tcp        0      0 localhost:8118          *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:smtp          *:*                     LISTEN     
tcp        0      0 localhost:8123          *:*                     LISTEN     
tcp        0      0 localhost:32000         localhost:31000         ESTABLISHED
tcp        0      0 10.208.110.6:51495      1.2.3.9:www             ESTABLISHED
tcp6       0      0 ip6-localhost:9481      [::]:*                  LISTEN     
tcp6       0      0 localhost:9481          [::]:*                  LISTEN     
tcp6       0      0 ip6-localhost:8888      [::]:*                  LISTEN     
tcp6       0      0 localhost:8888          [::]:*                  LISTEN     
tcp6       0      0 localhost:31000         localhost:32000         ESTABLISHED
udp        0      0 *:43982                 *:*                                
udp        0      0 *:mdns                  *:*                                
udp6       0      0 [::]:24796              [::]:*                             
udp6       0      0 [::]:65247              [::]:*                             
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     13017    /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     13970    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     13736    @/var/run/dbus-JIFptHK5JR
unix  2      [ ACC ]     STREAM     LISTENING     15415    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  2      [ ACC ]     STREAM     LISTENING     15428    /tmp/orbit-mark/linc-162b-0-ce0f0ec33bb7
unix  2      [ ACC ]     STREAM     LISTENING     12303    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     15657    /tmp/keyring-SpFzaR/socket
unix  2      [ ACC ]     STREAM     LISTENING     15659    /tmp/keyring-SpFzaR/ssh
unix  2      [ ACC ]     STREAM     LISTENING     15661    /tmp/keyring-SpFzaR/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     16274    /tmp/orbit-mark/linc-1630-0-7e6bc75b2f6d9
unix  2      [ ACC ]     STREAM     LISTENING     16305    /tmp/seahorse-LtOety/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     16352    /tmp/orbit-mark/linc-1630-0-31229c7c12962
unix  2      [ ACC ]     STREAM     LISTENING     16356    /tmp/.ICE-unix/5680
unix  2      [ ACC ]     STREAM     LISTENING     16417    /tmp/orbit-mark/linc-16ac-0-6c65fd65a7647
unix  2      [ ACC ]     STREAM     LISTENING     17428    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     17434    /tmp/pulse-mark/native
unix  2      [ ACC ]     STREAM     LISTENING     17473    /tmp/orbit-mark/linc-16b5-0-64e3cb2f5ee67
unix  2      [ ACC ]     STREAM     LISTENING     17604    /tmp/orbit-mark/linc-16bf-0-2dab925f26a69
unix  2      [ ACC ]     STREAM     LISTENING     17819    /tmp/orbit-mark/linc-16c6-0-6de3884c583d0
unix  2      [ ACC ]     STREAM     LISTENING     17861    /tmp/orbit-mark/linc-16c8-0-6de3884c7a5cf
unix  2      [ ACC ]     STREAM     LISTENING     17889    /tmp/orbit-mark/linc-16c5-0-73a91a335f9b
unix  2      [ ACC ]     STREAM     LISTENING     18304    /tmp/orbit-mark/linc-16d8-0-375a47a70fde
unix  2      [ ACC ]     STREAM     LISTENING     18344    /tmp/orbit-mark/linc-16ef-0-67d315dadfb8e
unix  2      [ ACC ]     STREAM     LISTENING     18345    /tmp/orbit-mark/linc-16f2-0-67d315dae0224
unix  2      [ ]         DGRAM                    6200     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     18364    /tmp/orbit-mark/linc-16f0-0-67d315d53e56a
unix  2      [ ACC ]     STREAM     LISTENING     18547    /tmp/orbit-mark/linc-1712-0-32098c64868be
unix  2      [ ACC ]     STREAM     LISTENING     18846    /tmp/orbit-mark/linc-1721-0-45137689bc5aa
unix  2      [ ACC ]     STREAM     LISTENING     18852    /tmp/orbit-mark/linc-1724-0-45137689cda86
unix  2      [ ACC ]     STREAM     LISTENING     19540    /tmp/orbit-mark/linc-1788-0-1d93827b93fbb
unix  2      [ ACC ]     STREAM     LISTENING     36381    /tmp/orbit-mark/linc-2645-0-9e46b086a325
unix  2      [ ACC ]     STREAM     LISTENING     12612    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     13785    @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     52069    /var/run/clamav/clamd.ctl
unix  2      [ ACC ]     STREAM     LISTENING     13930    /var/run/gdm_socket
unix  2      [ ]         DGRAM                    6345     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     12924    /var/run/nasd/audio0
unix  2      [ ACC ]     STREAM     LISTENING     12668    /var/run/cups/cups.sock
unix  2      [ ]         DGRAM                    13120    @/org/freedesktop/hal/udev_event
unix  12     [ ]         DGRAM                    12432    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     13734    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     13079    @/var/run/hald/dbus-WFRmpWozj1
unix  2      [ ACC ]     STREAM     LISTENING     13019    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     16370    @/tmp/dbus-GQAjfEKc7d
unix  2      [ ACC ]     STREAM     LISTENING     12521    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     13097    @/var/run/hald/dbus-AW6FESQZy9
unix  2      [ ]         DGRAM                    36436    
unix  3      [ ]         STREAM     CONNECTED     36434    
unix  3      [ ]         STREAM     CONNECTED     36433    
unix  3      [ ]         STREAM     CONNECTED     36395    
unix  3      [ ]         STREAM     CONNECTED     36394    
unix  3      [ ]         STREAM     CONNECTED     36393    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     36392    
unix  3      [ ]         STREAM     CONNECTED     36388    /tmp/orbit-mark/linc-2645-0-9e46b086a325
unix  3      [ ]         STREAM     CONNECTED     36387    
unix  3      [ ]         STREAM     CONNECTED     36386    /tmp/orbit-mark/linc-16d8-0-375a47a70fde
unix  3      [ ]         STREAM     CONNECTED     36385    
unix  3      [ ]         STREAM     CONNECTED     36384    /tmp/orbit-mark/linc-2645-0-9e46b086a325
unix  3      [ ]         STREAM     CONNECTED     36383    
unix  3      [ ]         STREAM     CONNECTED     36380    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     36379    
unix  3      [ ]         STREAM     CONNECTED     36377    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     36376    
unix  3      [ ]         STREAM     CONNECTED     36372    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     36371    
unix  3      [ ]         STREAM     CONNECTED     29251    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     29250    
unix  3      [ ]         STREAM     CONNECTED     29249    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     29248    
unix  3      [ ]         STREAM     CONNECTED     19545    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     19544    
unix  3      [ ]         STREAM     CONNECTED     19543    /tmp/orbit-mark/linc-1788-0-1d93827b93fbb
unix  3      [ ]         STREAM     CONNECTED     19542    
unix  3      [ ]         STREAM     CONNECTED     19539    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     19538    
unix  3      [ ]         STREAM     CONNECTED     19534    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19533    
unix  3      [ ]         STREAM     CONNECTED     19086    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19085    
unix  2      [ ]         STREAM     CONNECTED     19073    
unix  3      [ ]         STREAM     CONNECTED     19028    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19027    
unix  3      [ ]         STREAM     CONNECTED     19017    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19016    
unix  3      [ ]         STREAM     CONNECTED     19012    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     19011    
unix  3      [ ]         STREAM     CONNECTED     19013    /tmp/orbit-mark/linc-16c6-0-6de3884c583d0
unix  3      [ ]         STREAM     CONNECTED     19010    
unix  3      [ ]         STREAM     CONNECTED     19009    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19008    
unix  2      [ ]         DGRAM                    19007    
unix  3      [ ]         STREAM     CONNECTED     19006    /tmp/orbit-mark/linc-16c6-0-6de3884c583d0
unix  3      [ ]         STREAM     CONNECTED     19005    
unix  3      [ ]         STREAM     CONNECTED     19003    /tmp/orbit-mark/linc-1721-0-45137689bc5aa
unix  3      [ ]         STREAM     CONNECTED     19001    
unix  3      [ ]         STREAM     CONNECTED     19002    /tmp/orbit-mark/linc-1724-0-45137689cda86
unix  3      [ ]         STREAM     CONNECTED     19000    
unix  3      [ ]         STREAM     CONNECTED     18863    /tmp/orbit-mark/linc-1724-0-45137689cda86
unix  3      [ ]         STREAM     CONNECTED     18862    
unix  3      [ ]         STREAM     CONNECTED     18861    /tmp/orbit-mark/linc-16d8-0-375a47a70fde
unix  3      [ ]         STREAM     CONNECTED     18860    
unix  3      [ ]         STREAM     CONNECTED     18859    /tmp/orbit-mark/linc-1721-0-45137689bc5aa
unix  3      [ ]         STREAM     CONNECTED     18858    
unix  3      [ ]         STREAM     CONNECTED     18857    /tmp/orbit-mark/linc-16d8-0-375a47a70fde
unix  3      [ ]         STREAM     CONNECTED     18856    
unix  3      [ ]         STREAM     CONNECTED     18855    /tmp/orbit-mark/linc-1724-0-45137689cda86
unix  3      [ ]         STREAM     CONNECTED     18854    
unix  3      [ ]         STREAM     CONNECTED     18851    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     18850    
unix  3      [ ]         STREAM     CONNECTED     18849    /tmp/orbit-mark/linc-1721-0-45137689bc5aa
unix  3      [ ]         STREAM     CONNECTED     18848    
unix  3      [ ]         STREAM     CONNECTED     18843    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     18842    
unix  3      [ ]         STREAM     CONNECTED     18837    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18836    
unix  3      [ ]         STREAM     CONNECTED     18835    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18834    
unix  3      [ ]         STREAM     CONNECTED     18582    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18581    
unix  3      [ ]         STREAM     CONNECTED     18579    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18578    
unix  3      [ ]         STREAM     CONNECTED     18574    /tmp/orbit-mark/linc-16c6-0-6de3884c583d0
unix  3      [ ]         STREAM     CONNECTED     18573    
unix  3      [ ]         STREAM     CONNECTED     18572    /tmp/orbit-mark/linc-1712-0-32098c64868be
unix  3      [ ]         STREAM     CONNECTED     18571    
unix  3      [ ]         STREAM     CONNECTED     18569    @/dbus-vfs-daemon/socket-DbTXwuqX
unix  3      [ ]         STREAM     CONNECTED     18568    
unix  3      [ ]         STREAM     CONNECTED     18570    @/dbus-vfs-daemon/socket-NOnzfJdq
unix  3      [ ]         STREAM     CONNECTED     18567    
unix  3      [ ]         STREAM     CONNECTED     18564    @/dbus-vfs-daemon/socket-HIDdO3Xh
unix  3      [ ]         STREAM     CONNECTED     18563    
unix  3      [ ]         STREAM     CONNECTED     18562    @/dbus-vfs-daemon/socket-ZnOWftnI
unix  3      [ ]         STREAM     CONNECTED     18561    
unix  3      [ ]         STREAM     CONNECTED     18558    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18557    
unix  3      [ ]         STREAM     CONNECTED     18556    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18555    
unix  3      [ ]         STREAM     CONNECTED     18554    /tmp/orbit-mark/linc-1712-0-32098c64868be
unix  3      [ ]         STREAM     CONNECTED     18553    
unix  3      [ ]         STREAM     CONNECTED     18552    /tmp/orbit-mark/linc-16d8-0-375a47a70fde
unix  3      [ ]         STREAM     CONNECTED     18551    
unix  3      [ ]         STREAM     CONNECTED     18550    /tmp/orbit-mark/linc-1712-0-32098c64868be
unix  3      [ ]         STREAM     CONNECTED     18549    
unix  3      [ ]         STREAM     CONNECTED     18546    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     18545    
unix  3      [ ]         STREAM     CONNECTED     18541    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18540    
unix  3      [ ]         STREAM     CONNECTED     18539    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18538    
unix  3      [ ]         STREAM     CONNECTED     18537    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18536    
unix  3      [ ]         STREAM     CONNECTED     18497    @/dbus-vfs-daemon/socket-nCeLSF4Y
unix  3      [ ]         STREAM     CONNECTED     18496    
unix  3      [ ]         STREAM     CONNECTED     18495    @/dbus-vfs-daemon/socket-LmeIUbap
unix  3      [ ]         STREAM     CONNECTED     18494    
unix  3      [ ]         STREAM     CONNECTED     18486    @/dbus-vfs-daemon/socket-YkHAigXe
unix  3      [ ]         STREAM     CONNECTED     18485    
unix  3      [ ]         STREAM     CONNECTED     18487    @/dbus-vfs-daemon/socket-SRM2zeoD
unix  3      [ ]         STREAM     CONNECTED     18484    
unix  3      [ ]         STREAM     CONNECTED     18480    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18479    
unix  3      [ ]         STREAM     CONNECTED     18474    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18473    
unix  3      [ ]         STREAM     CONNECTED     18449    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18448    
unix  3      [ ]         STREAM     CONNECTED     18447    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18446    
unix  3      [ ]         STREAM     CONNECTED     18445    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18444    
unix  3      [ ]         STREAM     CONNECTED     18443    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18442    
unix  3      [ ]         STREAM     CONNECTED     18435    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18434    
unix  3      [ ]         STREAM     CONNECTED     18432    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18431    
unix  3      [ ]         STREAM     CONNECTED     18420    @/dbus-vfs-daemon/socket-trgc7SXL
unix  3      [ ]         STREAM     CONNECTED     18419    
unix  3      [ ]         STREAM     CONNECTED     18421    @/dbus-vfs-daemon/socket-rJkcLdZM
unix  3      [ ]         STREAM     CONNECTED     18418    
unix  3      [ ]         STREAM     CONNECTED     18411    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18410    
unix  3      [ ]         STREAM     CONNECTED     18391    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18390    
unix  3      [ ]         STREAM     CONNECTED     18389    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18388    
unix  3      [ ]         STREAM     CONNECTED     18386    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18385    
unix  3      [ ]         STREAM     CONNECTED     18384    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18383    
unix  3      [ ]         STREAM     CONNECTED     18380    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18379    
unix  3      [ ]         STREAM     CONNECTED     18378    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18377    
unix  3      [ ]         STREAM     CONNECTED     18376    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18375    
unix  2      [ ]         DGRAM                    18374    
unix  3      [ ]         STREAM     CONNECTED     18370    /tmp/orbit-mark/linc-16f0-0-67d315d53e56a
unix  3      [ ]         STREAM     CONNECTED     18366    
unix  3      [ ]         STREAM     CONNECTED     18362    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     18361    
unix  3      [ ]         STREAM     CONNECTED     18360    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18359    
unix  3      [ ]         STREAM     CONNECTED     18358    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18357    
unix  3      [ ]         STREAM     CONNECTED     18356    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     18355    
unix  3      [ ]         STREAM     CONNECTED     18353    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     18352    
unix  3      [ ]         STREAM     CONNECTED     18350    /tmp/orbit-mark/linc-16f2-0-67d315dae0224
unix  3      [ ]         STREAM     CONNECTED     18349    
unix  3      [ ]         STREAM     CONNECTED     18351    /tmp/orbit-mark/linc-16ef-0-67d315dadfb8e
unix  3      [ ]         STREAM     CONNECTED     18348    
unix  3      [ ]         STREAM     CONNECTED     18343    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     18341    
unix  3      [ ]         STREAM     CONNECTED     18342    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     18340    
unix  3      [ ]         STREAM     CONNECTED     18331    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     18330    
unix  3      [ ]         STREAM     CONNECTED     18326    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18325    
unix  3      [ ]         STREAM     CONNECTED     18324    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18323    
unix  3      [ ]         STREAM     CONNECTED     18321    /tmp/orbit-mark/linc-16c8-0-6de3884c7a5cf
unix  3      [ ]         STREAM     CONNECTED     18320    
unix  3      [ ]         STREAM     CONNECTED     18319    /tmp/orbit-mark/linc-16c6-0-6de3884c583d0
unix  3      [ ]         STREAM     CONNECTED     18318    
unix  3      [ ]         STREAM     CONNECTED     18314    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18313    
unix  3      [ ]         STREAM     CONNECTED     18312    /tmp/orbit-mark/linc-16d8-0-375a47a70fde
unix  3      [ ]         STREAM     CONNECTED     18310    
unix  3      [ ]         STREAM     CONNECTED     18311    /tmp/orbit-mark/linc-16d8-0-375a47a70fde
unix  3      [ ]         STREAM     CONNECTED     18309    
unix  3      [ ]         STREAM     CONNECTED     18244    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     18243    
unix  3      [ ]         STREAM     CONNECTED     17945    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     17944    
unix  3      [ ]         STREAM     CONNECTED     17937    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     17936    
unix  3      [ ]         STREAM     CONNECTED     17934    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     17933    
unix  3      [ ]         STREAM     CONNECTED     17897    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     17896    
unix  3      [ ]         STREAM     CONNECTED     17893    /tmp/orbit-mark/linc-16c5-0-73a91a335f9b
unix  3      [ ]         STREAM     CONNECTED     17891    
unix  3      [ ]         STREAM     CONNECTED     17888    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     17887    
unix  3      [ ]         STREAM     CONNECTED     17883    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     17882    
unix  3      [ ]         STREAM     CONNECTED     17878    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17877    
unix  3      [ ]         STREAM     CONNECTED     17864    /tmp/orbit-mark/linc-16c8-0-6de3884c7a5cf
unix  3      [ ]         STREAM     CONNECTED     17863    
unix  3      [ ]         STREAM     CONNECTED     17860    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     17859    
unix  3      [ ]         STREAM     CONNECTED     17827    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     17826    
unix  3      [ ]         STREAM     CONNECTED     17822    /tmp/orbit-mark/linc-16c6-0-6de3884c583d0
unix  3      [ ]         STREAM     CONNECTED     17821    
unix  3      [ ]         STREAM     CONNECTED     17818    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     17817    
unix  3      [ ]         STREAM     CONNECTED     17810    /tmp/.ICE-unix/5680
unix  3      [ ]         STREAM     CONNECTED     17809    
unix  3      [ ]         STREAM     CONNECTED     17808    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17807    
unix  3      [ ]         STREAM     CONNECTED     17764    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17763    
unix  3      [ ]         STREAM     CONNECTED     17755    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17754    
unix  3      [ ]         STREAM     CONNECTED     17611    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17610    
unix  3      [ ]         STREAM     CONNECTED     17609    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     17608    
unix  3      [ ]         STREAM     CONNECTED     17607    /tmp/orbit-mark/linc-16bf-0-2dab925f26a69
unix  3      [ ]         STREAM     CONNECTED     17606    
unix  3      [ ]         STREAM     CONNECTED     17603    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     17602    
unix  3      [ ]         STREAM     CONNECTED     17598    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17597    
unix  3      [ ]         STREAM     CONNECTED     17478    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17477    
unix  3      [ ]         STREAM     CONNECTED     17476    /tmp/orbit-mark/linc-16b5-0-64e3cb2f5ee67
unix  3      [ ]         STREAM     CONNECTED     17475    
unix  3      [ ]         STREAM     CONNECTED     17472    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     17471    
unix  3      [ ]         STREAM     CONNECTED     17482    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17432    
unix  3      [ ]         STREAM     CONNECTED     17201    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17200    
unix  3      [ ]         STREAM     CONNECTED     16978    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16977    
unix  3      [ ]         STREAM     CONNECTED     16420    /tmp/orbit-mark/linc-16ac-0-6c65fd65a7647
unix  3      [ ]         STREAM     CONNECTED     16419    
unix  3      [ ]         STREAM     CONNECTED     16416    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     16415    
unix  3      [ ]         STREAM     CONNECTED     16411    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     16410    
unix  3      [ ]         STREAM     CONNECTED     16409    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16408    
unix  3      [ ]         STREAM     CONNECTED     16374    @/tmp/dbus-GQAjfEKc7d
unix  3      [ ]         STREAM     CONNECTED     16373    
unix  3      [ ]         STREAM     CONNECTED     16372    
unix  3      [ ]         STREAM     CONNECTED     16371    
unix  3      [ ]         STREAM     CONNECTED     16355    /tmp/orbit-mark/linc-1630-0-31229c7c12962
unix  3      [ ]         STREAM     CONNECTED     16354    
unix  3      [ ]         STREAM     CONNECTED     16351    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     16350    
unix  3      [ ]         STREAM     CONNECTED     16311    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16310    
unix  3      [ ]         STREAM     CONNECTED     16277    /tmp/orbit-mark/linc-1630-0-7e6bc75b2f6d9
unix  3      [ ]         STREAM     CONNECTED     16276    
unix  3      [ ]         STREAM     CONNECTED     16273    /tmp/orbit-mark/linc-162d-0-38ebeb9c22ca2
unix  3      [ ]         STREAM     CONNECTED     16272    
unix  3      [ ]         STREAM     CONNECTED     16233    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16232    
unix  3      [ ]         STREAM     CONNECTED     15673    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15672    
unix  3      [ ]         STREAM     CONNECTED     15665    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15664    
unix  3      [ ]         STREAM     CONNECTED     14577    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14576    
unix  3      [ ]         STREAM     CONNECTED     13981    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     13980    
unix  4      [ ]         STREAM     CONNECTED     14579    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13979    
unix  3      [ ]         STREAM     CONNECTED     13784    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13783    
unix  2      [ ]         DGRAM                    13782    
unix  3      [ ]         STREAM     CONNECTED     13760    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13759    
unix  2      [ ]         DGRAM                    13758    
unix  3      [ ]         STREAM     CONNECTED     13720    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13719    
unix  2      [ ]         DGRAM                    13709    
unix  3      [ ]         STREAM     CONNECTED     13679    @/var/run/hald/dbus-WFRmpWozj1
unix  3      [ ]         STREAM     CONNECTED     13678    
unix  3      [ ]         STREAM     CONNECTED     13666    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13665    
unix  3      [ ]         STREAM     CONNECTED     13571    @/var/run/hald/dbus-WFRmpWozj1
unix  3      [ ]         STREAM     CONNECTED     13570    
unix  3      [ ]         STREAM     CONNECTED     13569    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13568    
unix  3      [ ]         STREAM     CONNECTED     13450    @/var/run/hald/dbus-WFRmpWozj1
unix  3      [ ]         STREAM     CONNECTED     13449    
unix  3      [ ]         STREAM     CONNECTED     13347    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     13346    
unix  3      [ ]         STREAM     CONNECTED     13328    @/var/run/hald/dbus-WFRmpWozj1
unix  3      [ ]         STREAM     CONNECTED     13327    
unix  3      [ ]         STREAM     CONNECTED     13115    @/var/run/hald/dbus-AW6FESQZy9
unix  3      [ ]         STREAM     CONNECTED     13114    
unix  3      [ ]         STREAM     CONNECTED     13095    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13094    
unix  3      [ ]         STREAM     CONNECTED     13081    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13080    
unix  3      [ ]         STREAM     CONNECTED     13055    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13054    
unix  2      [ ]         DGRAM                    13053    
unix  3      [ ]         STREAM     CONNECTED     13022    
unix  3      [ ]         STREAM     CONNECTED     13021    
unix  3      [ ]         STREAM     CONNECTED     12615    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12614    
unix  3      [ ]         STREAM     CONNECTED     12609    
unix  3      [ ]         STREAM     CONNECTED     12608    
unix  2      [ ]         DGRAM                    12606    
unix  3      [ ]         STREAM     CONNECTED     12585    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12584    
unix  3      [ ]         STREAM     CONNECTED     12576    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12575    
unix  3      [ ]         STREAM     CONNECTED     12546    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12545    
unix  2      [ ]         DGRAM                    12541    
unix  3      [ ]         STREAM     CONNECTED     12524    
unix  3      [ ]         STREAM     CONNECTED     12523    
unix  2      [ ]         DGRAM                    12500 

```

---

### Post by eightmillion on 2008-07-31
Ok, that didn't help. Could you run these commands please and post the outputs?

> lsof -Pnl +M -i4 | grep 31000

> lsof -Pnl +M -i4 | grep 32000

---

### Post by madmak on 2008-07-31
> **eightmillion said:**
> Ok, that didn't help. Could you run these commands please and post the outputs?

It was freenet that was running in the background mate, when i ran

lsof -Pnl +M -i4 | grep 32000

i got

```
wrapper-l 5621     1000    7u  IPv4  14685       TCP 127.0.0.1:32000->127.0.0.1:31000 (ESTABLISHED)
java      5645     1000    4u  IPv4  14200       TCP 127.0.0.1:32000 (LISTEN)
```

and it made me think what java apps could be running then i rememberd i had installed freenet ages ago lol i didnt realise that it starts up when i switch the pc on.

Thanks very much for your help and time eightmillion i forgot i had even installed freenet ](*,)

Thanks again mate

---

