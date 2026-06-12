---
title: "[SOLVED] Why am I useing so much RAM?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Samerious on 2008-11-21
Look at this it says 710 is used? I don't know im only running firefox a folder and a terminal atm...

---

### Post by Wisp558 on 2008-11-21
What is the output of


ps -A

---

### Post by Samerious on 2008-11-21
PID TTY          TIME 

 8742 pts/0    00:00:00 ps

---

### Post by Wisp558 on 2008-11-21
...what?

Did you capitalize the "a"?

---

### Post by bikeboy on 2008-11-21
The middle line is a more relevant representation, so 329 mb used is how I'd be looking at it. I'll try to find the link where there's a detailed explanation.

---

### Post by Samerious on 2008-11-21
samerious@samerious-desktop:~$ ps -A
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
   46 ?        00:00:00 kblockd/0
   47 ?        00:00:00 kblockd/1
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  125 ?        00:00:00 kseriod
  159 ?        00:00:00 pdflush
  160 ?        00:00:00 pdflush
  161 ?        00:00:01 kswapd0
  202 ?        00:00:00 aio/0
  203 ?        00:00:00 aio/1
 1381 ?        00:00:00 ksuspend_usbd
 1382 ?        00:00:00 khubd
 1497 ?        00:00:01 ata/0
 1508 ?        00:00:00 ata/1
 1511 ?        00:00:00 ata_aux
 1534 ?        00:00:00 scsi_eh_0
 1543 ?        00:00:03 scsi_eh_1
 2276 ?        00:00:00 scsi_eh_2
 2277 ?        00:00:00 scsi_eh_3
 2493 ?        00:00:00 kjournald
 2774 ?        00:00:00 udevd
 4466 tty4     00:00:00 getty
 4467 tty5     00:00:00 getty
 4469 tty2     00:00:00 getty
 4471 tty3     00:00:00 getty
 4473 tty6     00:00:00 getty
 4654 ?        00:00:00 acpid
 4682 ?        00:00:00 kondemand/0
 4683 ?        00:00:00 kondemand/1
 4779 ?        00:00:00 syslogd
 4835 ?        00:00:00 dd
 4837 ?        00:00:00 klogd
 4859 ?        00:00:01 dbus-daemon
 4875 ?        00:00:00 NetworkManager
 4889 ?        00:00:00 NetworkManagerD
 4902 ?        00:00:00 system-tools-ba
 4922 ?        00:00:00 avahi-daemon
 4923 ?        00:00:00 avahi-daemon
 4964 ?        00:00:00 cupsd
 5038 ?        00:00:00 dhcdbd
 5057 ?        00:00:01 hald
 5060 ?        00:00:00 console-kit-dae
 5122 ?        00:00:00 hald-runner
 5146 ?        00:00:00 hald-addon-acpi
 5150 ?        00:00:00 hald-addon-inpu
 5159 ?        00:00:00 hald-addon-stor
 5166 ?        00:00:01 hald-addon-stor
 5169 ?        00:00:02 hald-addon-stor
 5196 ?        00:00:00 hcid
 5223 ?        00:00:00 btaddconn
 5224 ?        00:00:00 btdelconn
 5234 ?        00:00:00 bluetoothd-serv
 5235 ?        00:00:00 bluetoothd-serv
 5244 ?        00:00:00 krfcommd
 5278 ?        00:00:00 dhclient
 5287 ?        00:00:00 gdm
 5290 ?        00:00:00 gdm
 5293 tty7     00:10:39 Xorg
 5346 ?        00:00:00 atd
 5360 ?        00:00:00 cron
 5504 tty1     00:00:00 getty
 5762 ?        00:00:04 gconfd-2
 5764 ?        00:00:00 gnome-keyring-d
 5765 ?        00:00:00 x-session-manag
 5884 ?        00:00:00 seahorse-agent
 5888 ?        00:00:00 dbus-daemon
 5889 ?        00:00:05 gnome-settings-
 5893 ?        00:00:03 pulseaudio
 5900 ?        00:00:00 gconf-helper
 5909 ?        00:00:28 gnome-screensav
 5915 ?        00:00:36 gnome-panel
 5917 ?        00:00:39 nautilus
 5926 ?        00:00:00 bonobo-activati
 5946 ?        00:00:00 gvfsd
 5955 ?        00:00:00 gvfs-fuse-daemo
 5991 ?        00:00:00 bluetooth-apple
 5996 ?        00:00:00 update-notifier
 6000 ?        00:00:00 evolution-alarm
 6001 ?        00:00:00 tracker-applet
 6003 ?        00:00:00 trackerd
 6007 ?        00:00:07 nm-applet
 6008 ?        00:00:00 gnome-volume-ma
 6009 ?        00:00:00 python
 6011 ?        00:00:00 gnome-power-man
 6015 ?        00:00:00 gvfsd-burn
 6021 ?        00:00:02 trashapplet
 6026 ?        00:00:00 evolution-excha
 6034 ?        00:00:02 gvfsd-trash
 6064 ?        00:00:00 evolution-data-
 6069 ?        00:00:00 mixer_applet2
 6073 ?        00:00:00 fast-user-switc
 6079 ?        00:00:00 sh
 6080 ?        00:00:00 compiz-decorato
 6082 ?        00:00:08 gtk-window-deco
 6184 ?        00:00:03 notification-da
 6220 ?        00:48:02 firefox
 6863 ?        00:00:34 metacity
 8459 ?        00:00:03 gnome-terminal
 8462 ?        00:00:00 gnome-pty-helpe
 8463 pts/0    00:00:00 bash
 8804 pts/0    00:00:00 ps

---

### Post by cardinals_fan on 2008-11-21
Please surround your terminal output with code tags (the # sign in the upper right of the reply box).

Open a terminal and type the following command:```
free -m
```Post the output here.

---

### Post by Wisp558 on 2008-11-21
I knew we were working on the WC3 problem, so I wanted to make sure there were no lingering wine threads...


could you post what most of the 700 MB of ram are being used by by looking in System>Administration>System Monitor

Also, it could just be that it's a normal amount of RAM. You DO have compiz running, and it's a lot less than most Vista Pcs... 

I'm not that helpful beyond much more... I'm still a semi-noob when it comes to Linux.

---

### Post by bikeboy on 2008-11-21
This link will explain it - [http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems#Q:_Why_is_Linux_using_up_all_my_memory.3F](http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems#Q:_Why_is_Linux_using_up_all_my_memory.3F)

---

### Post by Samerious on 2008-11-21
Alright 
free -m gets me...
> 
             total       used       free     shared    buffers     cached
Mem:           867        725        141          0         12        373
-/+ buffers/cache:        339        528
Swap:         1655        133       1521



---

### Post by cardinals_fan on 2008-11-21
```
total used free shared buffers cached
Mem: 867 725 141 0 12 373
-/+ buffers/cache: 339 528
Swap: 1655 133 1521
```
The line you want is -/+ buffers/cache.  Linux 'uses' almost all of your RAM for caching, but frees it up if it's needed.  That line lists the memory that is actually in use.  In your case, it lists **339 MB**.  That sound right?

---

### Post by Wisp558 on 2008-11-21
Yeah, basically, Linux uses your spare RAM, and fills it with system utilities to make it function better when not under load. That's it. There will probably (if I understand correctly)  be a point where the utilities will be siphoned off into swap (HDD) and your actual programs will use the RAM.

---

### Post by Samerious on 2008-11-21
O ok. Thanks all.

---

### Post by Samerious on 2008-11-22
OK New problems!
One. I can't get my virtual Desktop it resize to the size I want it to.
Two.The graphics are a little bit bugged on WC III .. Just some discoloration . This seeems to happen on WoW too.
Posted in a wrong spot... Sorry

---

### Post by Ryadt on 2008-11-22
Please start a new thread for new questions and mark this one as solved.

---

