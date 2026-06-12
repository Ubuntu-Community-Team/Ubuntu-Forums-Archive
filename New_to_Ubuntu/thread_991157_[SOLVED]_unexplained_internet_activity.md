---
title: "[SOLVED] unexplained internet activity"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by jakupl on 2008-11-23
I opened up the systems monitor and discovered that my Internet is being used for something. I had closed Firefox and such. Is that normal? and how can I see what it is?

output from ps -A

```
jakup@bobby:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:01 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  131 ?        00:00:00 cqueue
  135 ?        00:00:00 kseriod
  176 ?        00:00:00 pdflush
  177 ?        00:00:00 pdflush
  178 ?        00:00:00 kswapd0
  220 ?        00:00:00 aio/0
 1142 ?        00:00:00 ksuspend_usbd
 1145 ?        00:00:00 khubd
 1170 ?        00:00:02 ata/0
 1175 ?        00:00:00 ata_aux
 1877 ?        00:00:00 scsi_eh_0
 1878 ?        00:00:04 scsi_eh_1
 2056 ?        00:00:01 kjournald
 2244 ?        00:00:00 udevd
 2398 ?        00:00:00 led_workqueue
 2461 ?        00:00:00 kmmcd
 2465 ?        00:00:00 kpsmoused
 2484 ?        00:00:00 pccardd
 2579 ?        00:00:03 b43
 4297 tty4     00:00:00 getty
 4298 tty5     00:00:00 getty
 4305 tty2     00:00:00 getty
 4306 tty3     00:00:00 getty
 4307 tty6     00:00:00 getty
 4479 ?        00:00:00 acpid
 4509 ?        00:00:00 kondemand/0
 4589 ?        00:00:00 syslogd
 4638 ?        00:00:00 dd
 4640 ?        00:00:00 klogd
 4661 ?        00:00:04 dbus-daemon
 4681 ?        00:00:00 avahi-daemon
 4682 ?        00:00:00 avahi-daemon
 4708 ?        00:00:15 atieventsd
 4735 ?        00:00:00 cupsd
 4889 ?        00:00:00 hald
 4892 ?        00:00:00 console-kit-dae
 4955 ?        00:00:00 hald-runner
 4975 ?        00:00:00 hald-addon-inpu
 4986 ?        00:00:00 hald-addon-acpi
 4995 ?        00:00:05 hald-addon-stor
 5035 ?        00:00:00 bluetoothd
 5040 ?        00:00:00 btaddconn
 5042 ?        00:00:00 btdelconn
 5054 ?        00:00:00 krfcommd
 5086 ?        00:00:04 NetworkManager
 5090 ?        00:00:01 wpa_supplicant
 5093 ?        00:00:00 nm-system-setti
 5110 ?        00:00:00 gdm
 5116 ?        00:00:00 gdm
 5129 tty7     00:02:58 Xorg
 5132 ?        00:00:00 system-tools-ba
 5167 ?        00:00:00 atd
 5195 ?        00:00:00 cron
 5268 tty1     00:00:00 getty
 5324 ?        00:00:00 ipolldevd
 5778 ?        00:00:00 gnome-keyring-d
 5789 ?        00:00:00 x-session-manag
 5931 ?        00:00:00 dbus-launch
 5950 ?        00:00:00 dbus-daemon
 5953 ?        00:00:01 pulseaudio
 5956 ?        00:00:00 gconf-helper
 5958 ?        00:00:01 gconfd-2
 5982 ?        00:00:00 seahorse-agent
 6022 ?        00:00:00 gvfsd
 6025 ?        00:00:00 gnome-keyring-d
 6027 ?        00:00:02 gnome-settings-
 6030 ?        00:00:27 metacity
 6056 ?        00:00:00 gvfs-fuse-daemo
 6111 ?        00:00:12 gnome-panel
 6114 ?        00:00:01 nautilus
 6117 ?        00:00:00 bonobo-activati
 6164 ?        00:00:10 gnome-screensav
 6189 ?        00:00:00 gvfs-hal-volume
 6192 ?        00:00:00 gvfs-gphoto2-vo
 6213 ?        00:00:00 gvfsd-burn
 6217 ?        00:00:00 trashapplet
 6219 ?        00:00:00 gvfsd-trash
 6245 ?        00:00:00 charpick_applet
 6248 ?        00:00:00 fast-user-switc
 6251 ?        00:00:00 mixer_applet2
 6334 ?        00:00:00 tracker-applet
 6339 ?        00:00:00 evolution-alarm
 6356 ?        00:00:00 trackerd
 6361 ?        00:00:00 python
 6367 ?        00:00:01 nm-applet
 6386 ?        00:00:00 bluetooth-apple
 6387 ?        00:00:00 update-notifier
 6389 ?        00:00:00 gnome-power-man
 6438 ?        00:00:00 evolution-data-
 6468 ?        00:00:00 evolution-excha
 7505 ?        00:00:01 notification-da
13727 ?        00:00:00 gnome-terminal
13729 ?        00:00:00 gnome-pty-helpe
13730 pts/0    00:00:00 bash
13837 pts/0    00:00:00 ps
31608 ?        00:00:00 dhclient
```

---

### Post by dracayr on 2008-11-23
maybe evolution?

dracayr

---

### Post by Sealbhach on 2008-11-23
You could install etherape
```

sudo apt-get install etherape
```

Select run as root from the Applications/Internet menu. It will show you graphically what your computer is connected to.



.

---

### Post by amauk on 2008-11-23
iptraf is also really useful

---

### Post by jakupl on 2008-11-23
wowie that's interesting, a LOT of stuff is going on.

I live in a dormitory where we probably have a shared connection. But this is how it looks like when I am doing nothing at all.

should I be worried?

EDIT: dracayr, That is the best signature ever :)

---

### Post by ajgreeny on 2008-11-23
Are all these different kollegiegaarden.dk numbered entries for different local network users?  If so it may simply be those, who are inside the router of your system, rather than external contacts outside your network.  Provided you have any sharing limited, all should be OK.

---

### Post by rhcm123 on 2008-11-23
it could also be synaptic downloading packages for update

---

### Post by Old_Grey_Wolf on 2008-11-23
They all appear to be internal to the dormitory's network. IP address in the range of 224.0.0.0 through 239.255.255.255 are reserved for internal network use, and the like. The 169.x.x.x IP address is a windows machine having network connection issues.

---

