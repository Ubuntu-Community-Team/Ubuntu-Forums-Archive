---
title: "Need Updating HELP!!!!!!!!!!!"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by fignig on 2008-11-01
there is a problem when i'm trying to update through the update manager. i've already upgraded to the intrepid ibex, but it says 

Unable to get exclusive lock:
this usually means that another package manager application is already runnning, please close that app first.

but no other app of that kind is running. what kinda bug is this?

---

### Post by frank002 on 2008-11-01
Make sure you do not have Synaptic running in the background

---

### Post by taurus on 2008-11-01
Close that update manager window.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by fignig on 2008-11-01
> **frank002 said:**
> Make sure you do not have Synaptic running in the background

i think i know when synaptic is running...i never even opened it in the first place....

---

### Post by fignig on 2008-11-01
my ps -A

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   49 ?        00:00:00 kintegrityd/0
   50 ?        00:00:00 kintegrityd/1
   52 ?        00:00:00 kblockd/0
   53 ?        00:00:00 kblockd/1
   55 ?        00:00:00 kacpid
   56 ?        00:00:00 kacpi_notify
  161 ?        00:00:00 cqueue
  165 ?        00:00:00 kseriod
  215 ?        00:00:00 pdflush
  216 ?        00:00:00 pdflush
  217 ?        00:00:01 kswapd0
  263 ?        00:00:00 aio/0
  264 ?        00:00:00 aio/1
 1240 ?        00:00:00 ksuspend_usbd
 1241 ?        00:00:00 khubd
 1273 ?        00:00:00 ata/0
 1275 ?        00:00:01 ata/1
 1276 ?        00:00:00 ata_aux
 1298 ?        00:00:00 khpsbpkt
 1925 ?        00:00:00 scsi_eh_0
 1927 ?        00:00:00 scsi_eh_1
 2037 ?        00:00:00 scsi_eh_2
 2038 ?        00:00:00 scsi_eh_3
 2064 ?        00:00:00 knodemgrd_0
 2066 ?        00:00:00 scsi_eh_4
 2068 ?        00:00:01 scsi_eh_5
 2260 ?        00:00:02 kjournald
 2438 ?        00:00:00 udevd
 4654 tty4     00:00:00 getty
 4655 tty5     00:00:00 getty
 4658 tty2     00:00:00 getty
 4659 tty3     00:00:00 getty
 4662 tty6     00:00:00 getty
 4842 ?        00:00:00 acpid
 4894 ?        00:00:00 kondemand/0
 4896 ?        00:00:00 kondemand/1
 4970 ?        00:00:00 syslogd
 5023 ?        00:00:00 dd
 5025 ?        00:00:00 klogd
 5048 ?        00:00:00 dbus-daemon
 5070 ?        00:00:00 avahi-daemon
 5071 ?        00:00:00 avahi-daemon
 5105 ?        00:00:00 cupsd
 5259 ?        00:00:00 hddtemp
 5294 ?        00:00:00 nullmailer-send
 5354 ?        00:00:00 winbindd
 5362 ?        00:00:00 winbindd
 5381 ?        00:00:00 hald
 5384 ?        00:00:00 console-kit-dae
 5385 ?        00:00:00 hald-runner
 5466 ?        00:00:00 hald-addon-inpu
 5478 ?        00:00:00 hald-addon-acpi
 5483 ?        00:00:01 hald-addon-stor
 5486 ?        00:00:01 hald-addon-stor
 5524 ?        00:00:00 bluetoothd
 5530 ?        00:00:00 btaddconn
 5532 ?        00:00:00 btdelconn
 5552 ?        00:00:00 krfcommd
 5586 ?        00:00:00 NetworkManager
 5596 ?        00:00:00 wpa_supplicant
 5600 ?        00:00:00 nm-system-setti
 5624 ?        00:00:00 gdm
 5648 ?        00:00:00 system-tools-ba
 5685 ?        00:00:00 atd
 5713 ?        00:00:00 cron
 5787 tty1     00:00:00 getty
 5790 ?        00:00:00 dhclient
 8800 ?        00:00:01 apt-get
 9308 ?        00:00:00 gdm
 9332 tty9     00:02:51 Xorg
 9366 ?        00:00:00 gnome-keyring-d
 9376 ?        00:00:00 x-session-manag
 9471 ?        00:00:00 dbus-launch
 9472 ?        00:00:00 dbus-daemon
 9475 ?        00:00:46 pulseaudio
 9478 ?        00:00:00 gconf-helper
 9480 ?        00:00:01 gconfd-2
 9486 ?        00:00:00 seahorse-agent
 9489 ?        00:00:00 gvfsd
 9495 ?        00:00:00 gvfs-fuse-daemo
 9501 ?        00:00:00 gnome-keyring-d
 9504 ?        00:00:02 gnome-settings-
 9505 ?        00:00:00 compiz
 9568 ?        00:02:09 compiz.real
 9573 ?        00:00:04 gnome-screensav
 9574 ?        00:00:00 sh
 9575 ?        00:00:02 emerald
 9576 ?        00:00:07 gnome-panel
 9578 ?        00:00:02 nautilus
 9580 ?        00:00:00 bonobo-activati
 9588 ?        00:00:00 gvfs-hal-volume
 9590 ?        00:00:00 gvfsd-burn
 9592 ?        00:00:00 gvfs-gphoto2-vo
 9595 ?        00:00:00 gvfsd-trash
 9603 ?        00:00:02 sensors-applet
 9609 ?        00:00:00 trashapplet
 9611 ?        00:00:00 mixer_applet2
 9613 ?        00:00:05 multiload-apple
 9623 ?        00:00:00 gnome-inhibit-a
 9630 ?        00:00:01 update-notifier
 9631 ?        00:00:00 python
 9632 ?        00:00:00 tracker-applet
 9633 ?        00:00:00 bluetooth-apple
 9636 ?        00:00:00 trackerd
 9646 ?        00:00:00 python
 9647 ?        00:00:00 nm-applet
 9650 ?        00:00:03 python
 9651 ?        00:00:00 evolution-alarm
 9652 ?        00:00:00 python
 9654 ?        00:00:00 gnome-power-man
 9663 ?        00:00:00 evolution-excha
 9669 ?        00:00:00 evolution-data-
 9672 ?        00:00:00 notification-da
 9711 ?        00:00:00 python
 9745 ?        00:00:03 conky
 9747 ?        00:00:02 pidgin
 9779 ?        00:00:59 firefox
 9992 ?        00:01:54 amarokapp
 9996 ?        00:00:00 kdeinit
 9999 ?        00:00:00 dcopserver
10002 ?        00:00:00 klauncher
10004 ?        00:00:00 kded
10013 ?        00:00:00 kio_http
10020 ?        00:00:00 ruby
10021 ?        00:00:00 ruby
10027 ?        00:00:00 kio_file
10462 ?        00:00:00 sh
10463 ?        00:00:00 gnome-terminal
10466 ?        00:00:00 gnome-pty-helpe
10467 pts/1    00:00:00 bash
10498 pts/2    00:00:00 dpkg
10505 pts/2    00:00:00 dpkg-deb
10506 pts/2    00:00:00 dpkg-deb
10507 pts/2    00:00:00 dpkg-deb
10508 pts/1    00:00:00 ps

---

### Post by taurus on 2008-11-01
> **fignig said:**
> my ps -A

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   49 ?        00:00:00 kintegrityd/0
   50 ?        00:00:00 kintegrityd/1
   52 ?        00:00:00 kblockd/0
   53 ?        00:00:00 kblockd/1
   55 ?        00:00:00 kacpid
   56 ?        00:00:00 kacpi_notify
  161 ?        00:00:00 cqueue
  165 ?        00:00:00 kseriod
  215 ?        00:00:00 pdflush
  216 ?        00:00:00 pdflush
  217 ?        00:00:01 kswapd0
  263 ?        00:00:00 aio/0
  264 ?        00:00:00 aio/1
 1240 ?        00:00:00 ksuspend_usbd
 1241 ?        00:00:00 khubd
 1273 ?        00:00:00 ata/0
 1275 ?        00:00:01 ata/1
 1276 ?        00:00:00 ata_aux
 1298 ?        00:00:00 khpsbpkt
 1925 ?        00:00:00 scsi_eh_0
 1927 ?        00:00:00 scsi_eh_1
 2037 ?        00:00:00 scsi_eh_2
 2038 ?        00:00:00 scsi_eh_3
 2064 ?        00:00:00 knodemgrd_0
 2066 ?        00:00:00 scsi_eh_4
 2068 ?        00:00:01 scsi_eh_5
 2260 ?        00:00:02 kjournald
 2438 ?        00:00:00 udevd
 4654 tty4     00:00:00 getty
 4655 tty5     00:00:00 getty
 4658 tty2     00:00:00 getty
 4659 tty3     00:00:00 getty
 4662 tty6     00:00:00 getty
 4842 ?        00:00:00 acpid
 4894 ?        00:00:00 kondemand/0
 4896 ?        00:00:00 kondemand/1
 4970 ?        00:00:00 syslogd
 5023 ?        00:00:00 dd
 5025 ?        00:00:00 klogd
 5048 ?        00:00:00 dbus-daemon
 5070 ?        00:00:00 avahi-daemon
 5071 ?        00:00:00 avahi-daemon
 5105 ?        00:00:00 cupsd
 5259 ?        00:00:00 hddtemp
 5294 ?        00:00:00 nullmailer-send
 5354 ?        00:00:00 winbindd
 5362 ?        00:00:00 winbindd
 5381 ?        00:00:00 hald
 5384 ?        00:00:00 console-kit-dae
 5385 ?        00:00:00 hald-runner
 5466 ?        00:00:00 hald-addon-inpu
 5478 ?        00:00:00 hald-addon-acpi
 5483 ?        00:00:01 hald-addon-stor
 5486 ?        00:00:01 hald-addon-stor
 5524 ?        00:00:00 bluetoothd
 5530 ?        00:00:00 btaddconn
 5532 ?        00:00:00 btdelconn
 5552 ?        00:00:00 krfcommd
 5586 ?        00:00:00 NetworkManager
 5596 ?        00:00:00 wpa_supplicant
 5600 ?        00:00:00 nm-system-setti
 5624 ?        00:00:00 gdm
 5648 ?        00:00:00 system-tools-ba
 5685 ?        00:00:00 atd
 5713 ?        00:00:00 cron
 5787 tty1     00:00:00 getty
 5790 ?        00:00:00 dhclient
 **[COLOR="Blue"]8800 ?        00:00:01 apt-get[/COLOR]**
 9308 ?        00:00:00 gdm
 9332 tty9     00:02:51 Xorg
 9366 ?        00:00:00 gnome-keyring-d
 9376 ?        00:00:00 x-session-manag
 9471 ?        00:00:00 dbus-launch
 9472 ?        00:00:00 dbus-daemon
 9475 ?        00:00:46 pulseaudio
 9478 ?        00:00:00 gconf-helper
 9480 ?        00:00:01 gconfd-2
 9486 ?        00:00:00 seahorse-agent
 9489 ?        00:00:00 gvfsd
 9495 ?        00:00:00 gvfs-fuse-daemo
 9501 ?        00:00:00 gnome-keyring-d
 9504 ?        00:00:02 gnome-settings-
 9505 ?        00:00:00 compiz
 9568 ?        00:02:09 compiz.real
 9573 ?        00:00:04 gnome-screensav
 9574 ?        00:00:00 sh
 9575 ?        00:00:02 emerald
 9576 ?        00:00:07 gnome-panel
 9578 ?        00:00:02 nautilus
 9580 ?        00:00:00 bonobo-activati
 9588 ?        00:00:00 gvfs-hal-volume
 9590 ?        00:00:00 gvfsd-burn
 9592 ?        00:00:00 gvfs-gphoto2-vo
 9595 ?        00:00:00 gvfsd-trash
 9603 ?        00:00:02 sensors-applet
 9609 ?        00:00:00 trashapplet
 9611 ?        00:00:00 mixer_applet2
 9613 ?        00:00:05 multiload-apple
 9623 ?        00:00:00 gnome-inhibit-a
 9630 ?        00:00:01 update-notifier
 9631 ?        00:00:00 python
 9632 ?        00:00:00 tracker-applet
 9633 ?        00:00:00 bluetooth-apple
 9636 ?        00:00:00 trackerd
 9646 ?        00:00:00 python
 9647 ?        00:00:00 nm-applet
 9650 ?        00:00:03 python
 9651 ?        00:00:00 evolution-alarm
 9652 ?        00:00:00 python
 9654 ?        00:00:00 gnome-power-man
 9663 ?        00:00:00 evolution-excha
 9669 ?        00:00:00 evolution-data-
 9672 ?        00:00:00 notification-da
 9711 ?        00:00:00 python
 9745 ?        00:00:03 conky
 9747 ?        00:00:02 pidgin
 9779 ?        00:00:59 firefox
 9992 ?        00:01:54 amarokapp
 9996 ?        00:00:00 kdeinit
 9999 ?        00:00:00 dcopserver
10002 ?        00:00:00 klauncher
10004 ?        00:00:00 kded
10013 ?        00:00:00 kio_http
10020 ?        00:00:00 ruby
10021 ?        00:00:00 ruby
10027 ?        00:00:00 kio_file
10462 ?        00:00:00 sh
10463 ?        00:00:00 gnome-terminal
10466 ?        00:00:00 gnome-pty-helpe
10467 pts/1    00:00:00 bash
10498 pts/2    00:00:00 dpkg
10505 pts/2    00:00:00 dpkg-deb
10506 pts/2    00:00:00 dpkg-deb
10507 pts/2    00:00:00 dpkg-deb
10508 pts/1    00:00:00 ps

You already have apt-get running!

---

### Post by cariboo on 2008-11-01
Check in the following directories to see if there was a lock file that didn't get deleted last time you closed synaptic:

```
/var/cache/apt/archives/
/var/lib/dpkg/
/var/lib/apt/lists/
```

Jim

---

### Post by CatKiller on 2008-11-01
> **fignig said:**
> my ps -A

```
  PID TTY          TIME CMD
10498 pts/2    00:00:00 dpkg[COLOR="Blue"]
10505 pts/2    00:00:00 dpkg-deb
10506 pts/2    00:00:00 dpkg-deb
10507 pts/2    00:00:00 dpkg-deb[/COLOR]
10508 pts/1    00:00:00 ps
```

...and dpkg.

```
sudo killall apt-get
sudo killall dpkg
sudo killall dpkg-deb
``` should end all those process.

---

### Post by fignig on 2008-11-02
how are these running when i'm not using any installation/upgrading program...

---

### Post by taurus on 2008-11-02
Maybe you have a cron job running in the background to check for updates.

---

### Post by fignig on 2008-11-02
> **taurus said:**
> Maybe you have a cron job running in the background to check for updates.

wtf is a cron job? and how to i check to see if i have it running? what do i look for?

---

