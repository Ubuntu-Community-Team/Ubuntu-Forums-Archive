---
title: "Beating my head on my desk..."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by apartfromthedirt on 2008-06-23
I've just made the crossing of the straits of despair, the abyss of using (or should I say getting "used by") windows to ubuntu. Like the feel, everything works right away, except my sound card (creative lab Audigy). Been following the forums on how to install the driver needed. 

Now I'm beating my head rapid fashion against my desk hoping something good will come from it, but as we all know, it won't. So I'm looking to understand how to find a running process(s), which by shutting  down a shell to early has caused so much pain, And now can't complete an install. 

Error messages:

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable


Any suggestions for fixing this??

---

### Post by ad_267 on 2008-06-23
Do you have synaptic package manager open or another "apt-get" or "aptitude" command running? You can only have one package manager open at once.

You can use "ps -e" to list processes and get the process id then "kill -9 id_number" to kill the process.

---

### Post by tamoneya on 2008-06-23
the process is probably no longer existant but left a file lock on a file you are trying to use.  Take a look in /var/cache/debconf for a file name lock or something similar.  Then use rm to remove it with sudo if necessary.

---

### Post by apartfromthedirt on 2008-06-23
Ran the ps-e and came back with this:

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   41 ?        00:00:00 kblockd/0
   44 ?        00:00:00 kacpid
   45 ?        00:00:00 kacpi_notify
  132 ?        00:00:00 kseriod
  167 ?        00:00:00 pdflush
  168 ?        00:00:00 pdflush
  169 ?        00:00:00 kswapd0
  210 ?        00:00:00 aio/0
 1477 ?        00:00:00 ksuspend_usbd
 1480 ?        00:00:00 khubd
 1503 ?        00:00:00 khpsbpkt
 1526 ?        00:00:03 ata/0
 1531 ?        00:00:00 ata_aux
 2244 ?        00:00:00 knodemgrd_0
 2249 ?        00:00:00 scsi_eh_0
 2253 ?        00:00:00 scsi_eh_1
 2355 ?        00:00:00 scsi_eh_2
 2358 ?        00:00:09 scsi_eh_3
 2647 ?        00:00:01 kjournald
 2849 ?        00:00:00 udevd
 3143 ?        00:00:00 kgameportd
 4632 tty4     00:00:00 getty
 4633 tty5     00:00:00 getty
 4637 tty2     00:00:00 getty
 4638 tty3     00:00:00 getty
 4640 tty6     00:00:00 getty
 4808 ?        00:00:00 acpid
 4858 ?        00:00:00 kondemand/0
 4921 ?        00:00:00 syslogd
 4978 ?        00:00:00 dd
 4980 ?        00:00:00 klogd
 5002 ?        00:00:00 dbus-daemon
 5018 ?        00:00:00 NetworkManager
 5032 ?        00:00:00 NetworkManagerD
 5045 ?        00:00:00 system-tools-ba
 5065 ?        00:00:00 avahi-daemon
 5066 ?        00:00:00 avahi-daemon
 5104 ?        00:00:00 cupsd
 5178 ?        00:00:01 dhcdbd
 5197 ?        00:00:00 hald
 5200 ?        00:00:00 console-kit-dae
 5262 ?        00:00:00 hald-runner
 5283 ?        00:00:00 hald-addon-acpi
 5301 ?        00:00:00 hald-addon-inpu
 5311 ?        00:00:00 hald-addon-stor
 5320 ?        00:00:01 hald-addon-stor
 5323 ?        00:00:01 hald-addon-stor
 5365 ?        00:00:00 hcid
 5371 ?        00:00:00 btaddconn
 5372 ?        00:00:00 btdelconn
 5381 ?        00:00:00 bluetoothd-serv
 5382 ?        00:00:00 bluetoothd-serv
 5387 ?        00:00:00 krfcommd
 5448 ?        00:00:00 gdm
 5449 ?        00:00:00 gdm
 5455 tty7     00:17:15 Xorg
 5461 ?        00:00:00 dhclient
 5518 ?        00:00:00 atd
 5532 ?        00:00:00 cron
 5612 tty1     00:00:00 getty
 5711 ?        00:00:03 gconfd-2
 5713 ?        00:00:00 gnome-keyring-d
 5714 ?        00:00:00 x-session-manag
 5767 ?        00:00:00 seahorse-agent
 5771 ?        00:00:00 dbus-daemon
 5772 ?        00:00:04 gnome-settings-
 5796 ?        00:00:00 compiz
 5798 ?        00:00:33 gnome-panel
 5799 ?        00:00:19 gnome-screensav
 5800 ?        00:00:07 nautilus
 5809 ?        00:00:00 bonobo-activati
 5828 ?        00:00:00 gvfsd
 5842 ?        00:00:00 gvfs-fuse-daemo
 5869 ?        00:00:58 compiz.real
 5870 ?        00:00:00 bluetooth-apple
 5873 ?        00:00:01 update-notifier
 5876 ?        00:00:00 tracker-applet
 5877 ?        00:00:00 evolution-alarm
 5881 ?        00:00:00 trackerd
 5886 ?        00:00:00 python
 5887 ?        00:00:12 nm-applet
 5889 ?        00:00:00 gnome-volume-ma
 5890 ?        00:00:00 gnome-power-man
 5898 ?        00:00:00 gvfsd-burn
 5904 ?        00:00:00 trashapplet
 5907 ?        00:00:00 gvfsd-trash
 5919 ?        00:00:00 evolution-data-
 5925 ?        00:00:00 mixer_applet2
 5928 ?        00:00:00 fast-user-switc
 5945 ?        00:00:00 sh
 5946 ?        00:00:00 compiz-decorato
 5948 ?        00:00:18 gtk-window-deco
 5985 ?        00:23:50 firefox
 6429 ?        00:00:00 dpkg-reconfigur
 6436 ?        00:00:00 alsa-source.con
 6443 ?        01:42:26 whiptail
 6549 ?        00:00:00 gnome-vfs-daemo
 6748 ?        00:00:00 gpilotd
 6880 ?        00:00:01 notification-da
 6953 ?        00:00:02 mount.ntfs-3g
 7178 ?        00:00:00 gnome-terminal
 7180 ?        00:00:00 gnome-pty-helpe
 7181 pts/1    00:00:00 bash
 7198 pts/1    00:00:00 ps


Don't really understand which one is the one I'm looking for?

---

### Post by tamoneya on 2008-06-23
i dont see anything related to debconf in there.  Try my recommendation.  If you are confused at all post the output of ```
ls /var/cache/debconf
```

---

### Post by apartfromthedirt on 2008-06-23
config.dat  config.dat-old  passwords.dat  templates.dat  templates.dat-old

---

### Post by LeoSolaris on 2008-06-23
I have had something like this happen before. If I am reading you right, it means your package is half installed.

try: ```
 sudo dpkg --configure -a
```It will look for all of the half completed installs and redo them.

This is from the man page for [dpkg]("http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/dpkg.8.gz#lbAG"):
> ** dpkg --configure ***package* ... | **-a** | **--pending** Reconfigure an unpacked package.  If **-a** or **--pending** is given instead of *package*, all unpacked but unconfigured packages are configured.  Configuring consists of the following steps: 
 
 **1.** Unpack the configuration files, and at the same time back up the old configuration files, so that they can be restored if something goes wrong. 
 
 **2.** Run *postinst* script, if provided by the package.

---

### Post by apartfromthedirt on 2008-06-23
Thanks for all the help, but still no sound. Ran through the comprehensive sound problem thread. Can't imagine whats keeping it from working, it worked perfectly with xp, but since the install of Ubuntu, nothing.

---

