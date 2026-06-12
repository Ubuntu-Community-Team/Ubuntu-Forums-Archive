---
title: "disk led blinks &gt;3 times per second!"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by pcardoso on 2008-09-25
Dear all, yesterday a used gparted to resize my ubuntu partition. Today, after booting every thing worked fine except that the disk led doesn't stop blinking: about 3/4 times per second! I've seen some post but none seems to address this exact problem (except perhaps for [http://ubuntuforums.org/archive/index.php/t-369759.html](http://ubuntuforums.org/archive/index.php/t-369759.html)). Any ideas? 

below is the list of running processes


regards,
PCardoso

PS: I also removed some software bluetooth related (?)
[SIZE="2"]
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2844  1692 ?        Ss   08:14   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   08:14   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   08:14   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   08:14   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   08:14   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   08:14   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   08:14   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   08:14   0:00 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   08:14   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   08:14   0:00 [kacpi_notify]
root       121  0.0  0.0      0     0 ?        S<   08:14   0:00 [kseriod]
root       158  0.0  0.0      0     0 ?        S    08:14   0:00 [pdflush]
root       159  0.0  0.0      0     0 ?        S    08:14   0:00 [pdflush]
root       160  0.0  0.0      0     0 ?        S<   08:14   0:00 [kswapd0]
root       201  0.0  0.0      0     0 ?        S<   08:14   0:00 [aio/0]
root      1463  0.0  0.0      0     0 ?        S<   08:14   0:00 [ksuspend_usbd]
root      1466  0.0  0.0      0     0 ?        S<   08:14   0:00 [khubd]
root      1492  0.0  0.0      0     0 ?        S<   08:14   0:00 [ata/0]
root      1498  0.0  0.0      0     0 ?        S<   08:14   0:00 [ata_aux]
root      1927  0.0  0.0      0     0 ?        S<   08:14   0:00 [scsi_eh_0]
root      1929  0.0  0.0      0     0 ?        S<   08:14   0:00 [scsi_eh_1]
root      2430  2.3  0.0      0     0 ?        S<   08:14   0:49 [kjournald]
root      2634  0.0  0.0   2420   968 ?        S<s  08:14   0:00 /sbin/udevd --daemon
root      2937  0.0  0.0      0     0 ?        S<   08:15   0:00 [kpsmoused]
root      3468  0.0  0.0      0     0 ?        S<   08:15   0:00 [rt73usb]
root      4478  0.0  0.0   1716   508 tty4     Ss+  08:15   0:00 /sbin/getty 38400 tty4
root      4479  0.0  0.0   1716   504 tty5     Ss+  08:15   0:00 /sbin/getty 38400 tty5
root      4483  0.0  0.0   1716   508 tty2     Ss+  08:15   0:00 /sbin/getty 38400 tty2
root      4484  0.0  0.0   1716   508 tty3     Ss+  08:15   0:00 /sbin/getty 38400 tty3
root      4486  0.0  0.0   1716   508 tty6     Ss+  08:15   0:00 /sbin/getty 38400 tty6
root      4654  0.0  0.1   2456  1356 ?        Ss   08:15   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4694  0.0  0.0      0     0 ?        S<   08:15   0:00 [kondemand/0]
syslog    4783  0.0  0.0   1936   640 ?        Ss   08:15   0:00 /sbin/syslogd -u syslog
107       4870  0.0  0.1   2852  1340 ?        Ss   08:15   0:00 /usr/bin/dbus-daemon --system
root      4895  0.0  0.2  21088  2224 ?        Ssl  08:15   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4909  0.0  0.1   3536  1308 ?        Ss   08:15   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4926  0.0  0.1   4380  1896 ?        Ss   08:15   0:00 /usr/bin/system-tools-backends
avahi     4963  0.0  0.1   2760  1428 ?        Ss   08:15   0:00 avahi-daemon: running [pcardoso-desktop.local]
avahi     4964  0.0  0.0   2760   464 ?        Ss   08:15   0:00 avahi-daemon: chroot helper
root      5172  0.0  0.0   2908   788 ?        Ss   08:15   0:00 /usr/sbin/netdaemon
root      5259  0.0  0.1   8084  1288 ?        Ss   08:15   0:00 /usr/sbin/winbindd
root      5294  0.0  0.1   8084  1060 ?        S    08:15   0:00 /usr/sbin/winbindd
root      5326  0.0  0.0   2020   900 ?        Ss   08:15   0:00 /usr/sbin/dhcdbd --system
110       5348  0.0  0.3   6344  3748 ?        Ss   08:15   0:00 /usr/sbin/hald
root      5351  0.0  0.2   7884  2380 ?        Ssl  08:15   0:00 /usr/sbin/console-kit-daemon
root      5414  0.0  0.1   3352  1180 ?        S    08:15   0:00 hald-runner
root      5431  0.0  0.1   3416  1156 ?        S    08:15   0:00 hald-addon-input: Listening on /dev/input/event6 /dev/input/event5 /dev/input/event2 /dev/input/event3
110       5434  0.0  0.0   2204   908 ?        S    08:15   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5460  0.0  0.1   3420  1124 ?        S    08:15   0:00 hald-addon-storage: no polling on /dev/fd0 because it is explicitly disabled
root      5470  0.0  0.1   3420  1140 ?        S    08:15   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
mythtv    5514  0.8  1.7  83060 18084 ?        Ssl  08:15   0:18 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
root      5560  0.0  0.1  14288  1672 ?        Ss   08:15   0:00 /usr/sbin/gdm
root      5563  0.0  0.3  14764  3180 ?        S    08:15   0:00 /usr/sbin/gdm
root      5567  3.4  3.9  48320 40856 tty7     SLs+ 08:15   1:10 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5603  0.0  0.2   6092  2416 ?        Ss   08:15   0:01 /usr/sbin/cupsd
daemon    5640  0.0  0.0   1984   420 ?        Ss   08:15   0:00 /usr/sbin/atd
root      5654  0.0  0.0   2104   888 ?        Ss   08:15   0:00 /usr/sbin/cron
root      5754  0.0  0.0   1716   508 tty1     Ss+  08:15   0:00 /sbin/getty 38400 tty1
pcardoso  5771  0.0  0.4   8108  5012 ?        S    08:15   0:01 /usr/lib/libgconf2-4/gconfd-2 4
pcardoso  5773  0.0  0.2  14488  2236 ?        S    08:15   0:00 /usr/bin/gnome-keyring-daemon -d --login
pcardoso  5774  0.0  1.4  40916 14620 ?        Ssl  08:15   0:00 x-session-manager
pcardoso  5905  0.0  0.6  23528  6880 ?        Ss   08:15   0:00 /usr/bin/seahorse-agent --execute x-session-manager
pcardoso  5913  0.0  0.1   2832  1288 ?        Ss   08:15   0:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
pcardoso  5914  0.0  1.4  45132 15448 ?        Sl   08:15   0:01 gnome-settings-daemon
pcardoso  5918  0.0  0.5  28688  6016 ?        Sl   08:15   0:00 /usr/bin/pulseaudio --log-target=syslog
pcardoso  5921  0.0  0.2   5776  2260 ?        S    08:15   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
pcardoso  5930  0.1  0.2  15592  2624 ?        Ss   08:15   0:02 gnome-screensaver
pcardoso  5935  0.0  0.0   1772   532 ?        S    08:15   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
pcardoso  5937  0.3  3.1  63604 32328 ?        S    08:15   0:07 gnome-panel --sm-client-id default1
pcardoso  5940  0.0  2.3  78068 24628 ?        Sl   08:15   0:00 nautilus --no-default-window --sm-client-id default2
pcardoso  5954  0.0  0.3  40384  3340 ?        Ssl  08:15   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
pcardoso  5969  0.0  0.2   5432  2144 ?        S    08:15   0:00 /usr/lib/gvfs/gvfsd
pcardoso  6000  2.3  2.8  56884 29340 ?        RL   08:15   0:49 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 core ccp
pcardoso  6004  0.0  1.4  32484 14776 ?        S    08:15   0:00 update-notifier
pcardoso  6007  0.0  0.5  15760  5812 ?        S    08:15   0:00 tracker-applet
pcardoso  6008  0.0  1.0  62776 10512 ?        Sl   08:15   0:00 /usr/lib/evolution/2.22/evolution-alarm-notify
pcardoso  6010  0.0  1.0  30800 10436 ?        SNl  08:15   0:00 trackerd
pcardoso  6014  0.0  0.1  29048  1900 ?        Ssl  08:15   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/pcardoso/.gvfs
pcardoso  6019  0.0  0.4  21072  4768 ?        Ss   08:15   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
pcardoso  6022  0.0  1.1  36252 12416 ?        S    08:15   0:01 nm-applet --sm-disable
pcardoso  6023  0.0  1.1  24476 12340 ?        S    08:15   0:00 python /usr/share/system-config-printer/applet.py
pcardoso  6024  0.1  0.8  41868  8880 ?        Rl   08:15   0:02 gnome-cups-icon --sm-client-id default3
pcardoso  6025  0.0  0.7  23984  8092 ?        Ss   08:15   0:00 gnome-power-manager
pcardoso  6040  0.0  0.9  39380 10056 ?        Sl   08:15   0:00 /usr/lib/evolution/2.22/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=23
root      6044  0.0  0.1   3880  1500 ?        S    08:15   0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global
pcardoso  6057  0.0  0.6  59968  6720 ?        Sl   08:15   0:00 /usr/lib/evolution/evolution-data-server-2.22 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=24
pcardoso  6059  0.0  0.2   5484  2200 ?        S    08:15   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
pcardoso  6063  0.0  0.2  22188  2804 ?        S    08:15   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
dhcp      6085  0.0  0.1   2440  1192 ?        S    08:15   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.wlan0.pid -q -e dhc_dbus=31 -d wlan0
pcardoso  6134  0.0  1.0  29932 11036 ?        S    08:15   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=25
pcardoso  6137  0.0  0.0   1772   484 ?        Ss   08:15   0:00 /bin/sh -c /usr/bin/compiz-decorator
pcardoso  6138  0.0  0.0   1772   504 ?        S    08:15   0:00 /bin/sh /usr/bin/compiz-decorator
pcardoso  6140  0.0  1.1  21524 12204 ?        S    08:15   0:01 /usr/bin/gtk-window-decorator
pcardoso  6163  0.0  1.4  33128 14564 ?        S    08:16   0:00 /usr/lib/gnome-applets/stickynotes_applet --oaf-activate-iid=OAFIID:GNOME_StickyNotesApplet_Factory --oaf-ior-fd=27
pcardoso  6166  0.0  1.4  41220 15020 ?        S    08:16   0:00 /usr/lib/gnome-applets/drivemount_applet2 --oaf-activate-iid=OAFIID:GNOME_DriveMountApplet_Factory --oaf-ior-fd=32
pcardoso  6169  0.0  3.8  78448 39984 ?        Sl   08:16   0:01 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factory --oaf-ior-fd=35
pcardoso  6173  0.0  1.5  51116 15920 ?        Sl   08:16   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=29
pcardoso  6175  0.0  1.3  32976 14376 ?        S    08:16   0:01 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-activate-iid=OAFIID:GNOME_NetstatusApplet_Factory --oaf-ior-fd=43
ntp       6274  0.0  0.1   4136  1232 ?        Ss   08:16   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 113:128 -g
pcardoso  6282  0.0  0.3   8760  3560 ?        S    08:16   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
pcardoso  6292  0.0  0.0      0     0 ?        Z    08:16   0:00 [sh] <defunct>
pcardoso  6308  0.0  1.9  73160 19964 ?        Sl   08:16   0:01 gnome-terminal
pcardoso  6311  0.0  0.0   2912   856 ?        S    08:16   0:00 gnome-pty-helper
pcardoso  6312  0.0  0.3   5836  3252 pts/0    Rs   08:16   0:00 bash
root      6345  0.0  1.0  13136 11208 ?        S    08:16   0:00 /usr/bin/perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
pcardoso  6365  0.0  1.3  29616 13668 ?        S    08:16   0:00 /usr/lib/notification-daemon/notification-daemon
pcardoso  7021  5.9  9.8 222672 102332 ?       Sl   08:19   1:49 /usr/lib/firefox-3.0.2/firefox
pcardoso  7378  0.0  0.5  15124  5572 ?        S    08:31   0:00 gksu /usr/bin/gparted
root      7379  0.0  1.5  39176 16424 ?        Ss   08:31   0:00 /usr/bin/gparted
pcardoso  7471  0.0  0.0   1772   516 ?        S    08:37   0:00 /bin/sh /usr/bin/thunderbird
pcardoso  7484  0.0  0.0   1772   524 ?        S    08:37   0:00 /bin/sh /usr/lib/thunderbird/run-mozilla.sh /usr/lib/thunderbird/thunderbird-bin
pcardoso  7488  0.3  3.8 142924 40160 ?        Sl   08:37   0:02 /usr/lib/thunderbird/thunderbird-bin
pcardoso  7664  0.0  0.0   2644  1004 pts/0    R+   08:49   0:00 ps aux
[/SIZE]

---

### Post by nowshining on 2008-09-25
more than likely it's normal :) the hard drive gets accessed and read to many many times a second when the computer and esp.. the OS is running..

---

### Post by tonybaqain on 2008-09-25
for your PC's sake, reboot it into single mode ( known as recovery mode from grub menu )

follow these steps :

[LIST]
[*]mount -orw,remount /
[*]**fsck -ycvf /** if this fails, try this
[*] [LIST]
[*]mount
[*]you'll find something like /dev/sdxx on / type ext3 .....
[*]the /dev/sdxx will be the drive you want to check
[/LIST]
[*] use fsck with the drive you found **fsck -cfvy /dev/sdxx**
[/LIST]

run the fsck command until there are no more errors appearing, and then reboot into normal mode.

have fun :)

--------------------------------------
if this works for you, please don't forget to mark this thread as [SOLVED] from the thread configuration up-in-the-page.

---

### Post by nowshining on 2008-09-25
> **tonybaqain said:**
> for your PC's sake, reboot it into single mode ( known as recovery mode from grub menu )

follow these steps :

[LIST]
[*]mount -orw,remount /
[*]**fsck -ycvf /** if this fails, try this
[*] [LIST]
[*]mount
[*]you'll find something like /dev/sdxx on / type ext3 .....
[*]the /dev/sdxx will be the drive you want to check
[/LIST]
[*] use fsck with the drive you found **fsck -cfvy /dev/sdxx**
[/LIST]

run the fsck command until there are no more errors appearing, and then reboot into normal mode.

have fun :)

--------------------------------------
if this works for you, please don't forget to mark this thread as [SOLVED] from the thread configuration up-in-the-page.

no need to reboot, just type exit at the prompt at which it should now resume normal operation..

---

### Post by pcardoso on 2008-09-25
> **tonybaqain said:**
> for your PC's sake, reboot it into single mode ( known as recovery mode from grub menu )

follow these steps :

[LIST]
[*]mount -orw,remount /
[*]**fsck -ycvf /** if this fails, try this
[*] [LIST]
[*]mount
[*]you'll find something like /dev/sdxx on / type ext3 .....
[*]the /dev/sdxx will be the drive you want to check
[/LIST]
[*] use fsck with the drive you found **fsck -cfvy /dev/sdxx**
[/LIST]

run the fsck command until there are no more errors appearing, and then reboot into normal mode.

have fun :)

--------------------------------------
if this works for you, please don't forget to mark this thread as [SOLVED] from the thread configuration up-in-the-page.


Thanks for the tip but it keeps doing exactly the same thing... No erroo messages.
Could any one give some more ideas? I think it will eventually blow the disk...

regards,
PC

---

### Post by unutbu on 2008-09-25
You might want to look at this thread: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

Since this problem just started after using GParted, it is quite likely the above thread is not the solution. However, the OP of the thread, vor, seems quite knowledgable and may be able to help you out more.

---

### Post by pcardoso on 2008-09-26
I'm, probably, so stupid!!!
 
Before I went to gparted I was having space problems so I removed some software and some folders from my home directory. Yesterday, after trying your suggestion I went to see my list of process and remove some possible extra services/programs. After removing mythtv it stopped! I'm not sure but perhaps it was "looking" for some of the deleted folders! Anyhow, it's solved. Thanks again for answers. 

Regards,
PC.

---

