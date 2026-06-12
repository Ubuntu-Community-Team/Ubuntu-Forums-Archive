---
title: "[SOLVED] Synaptic Package manager question"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by gal_amy on 2008-07-30
Everytime I open the package manager, I get this command, which I run from the command line of the terminal 

**E: dpkg was interrupted, you must manually run: dpkg --configure -a to correct the problem.**

this is what the terminal tells me  dpkg: requested operation requires superuser privilege

I'm the only user so I'm lost as to what it wants.

---

### Post by tuxxy on 2008-07-30
add a 

```
sudo 
```

to the start of the command

---

### Post by Shazaam on 2008-07-30
You need to add sudo in front of the command....
```
sudo dpkg --configure -a
```

---

### Post by bodhi.zazen on 2008-07-30
Like this ...
```
sudo dpkg --configure -a
```

---

### Post by SunnyRabbiera on 2008-07-30
this is a common issue, but easy enough to resolve.

---

### Post by gal_amy on 2008-07-30
> **bodhi.zazen said:**
> Like this ...
```
sudo dpkg --configure -a
```

Thank you very much.  This is what I got back when I ran the command:

 Local security certificates must be replaced                            &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; A security certificate which was automatically created for your local   &#9474; 
  &#9474; system needs to be replaced due to a flaw which renders it insecure.    &#9474; 
  &#9474; This will be done automatically.                                        &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; If you don't know anything about this, you can safely ignore this       &#9474; 
  &#9474; message.                                                                &#9474; 
  &#9474;

---

### Post by gal_amy on 2008-07-30
> **tuxxy said:**
> add a 

```
sudo 
```

to the start of the command
[B]

Thank you so much.  I will try that now[/B]

---

### Post by SunnyRabbiera on 2008-07-30
Hmm, well did you by chance add a extra repository or something like that?

---

### Post by gal_amy on 2008-07-30
> **SunnyRabbiera said:**
> Hmm, well did you by chance add a extra repository or something like that?

No, I just installed the program yesterday.  This is my first attempt at installation, other than the wireless driver.

I just received this error message:

[B]Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.[/B]

I didn't have any thing running at all, so not sure what this means.

---

### Post by Shazaam on 2008-07-30
Either Synaptic is open or the auto updater is probably running in the background checking for updates. Close Synaptic and try the code in terminal again.

---

### Post by tuxxy on 2008-07-30
You can use the following command to terminate any of the processes
```

killall <appname>
```

---

### Post by bodhi.zazen on 2008-07-31
> **gal_amy said:**
> Thank you very much.  This is what I got back when I ran the command:

 Local security certificates must be replaced                            &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; A security certificate which was automatically created for your local   &#9474; 
  &#9474; system needs to be replaced due to a flaw which renders it insecure.    &#9474; 
  &#9474; This will be done automatically.                                        &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; If you don't know anything about this, you can safely ignore this       &#9474; 
  &#9474; message.                                                                &#9474; 
  &#9474;

That message is OK, if I recall correctly it has to do with the ssl security flaw.

the last line should be a clue :

> If you don't know anything about this, you can safely ignore this message:lolflag:

---

### Post by bodhi.zazen on 2008-07-31
> **gal_amy said:**
> No, I just installed the program yesterday.  This is my first attempt at installation, other than the wireless driver.

I just received this error message:

[B]Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.[/B]

I didn't have any thing running at all, so not sure what this means.

As others indicated "there can be only one".

You can not run synaptic, apt-get, aptitude, ADD/Remove packages, etc at the same time, otherwise you get that error message.

---

### Post by gal_amy on 2008-07-31
> **Shazaam said:**
> Either Synaptic is open or the auto updater is probably running in the background checking for updates. Close Synaptic and try the code in terminal again.

I tried the code again and it tells me that something is loaded.

I tried killfile apt-get
and killfile aptitude

but it says nothing is running.

How can I close the auto updater?

Thank you,
Amy

There was a circle on the upper right next to my name.  I closed that icon, but it still doesn't seem to want to load.

I also tried gksudo synaptic and get the same error message
I tried sudo apt-get update && sudo apt-get upgrademan

tells me something is running.

Anyhelp would be appreciated.

I didn't have any problems at all when running the live CD.  the synaptic package manager worked great

---

### Post by rockerphil on 2008-07-31
to take a look at all the processes running in the background run this:

ps -A

that'll list everything running in the background, and you can kill any that you don't need using:

killall <appname>

or you can use:

sudo kill <processnumber>

hope this helps,

Phil

----------------
Now playing: [Nirvana - Smells Like Teens Spirit](http://www.foxytunes.com/artist/nirvana/track/smells+like+teens+spirit)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by gal_amy on 2008-07-31
> **rockerphil said:**
> to take a look at all the processes running in the background run this:

ps -A

that'll list everything running in the background, and you can kill any that you don't need using:

killall <appname>

or you can use:

sudo kill <processnumber>

hope this helps,

Phil

----------------
Now playing: [Nirvana - Smells Like Teens Spirit](http://www.foxytunes.com/artist/nirvana/track/smells+like+teens+spirit)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)


WOW!  THere is a ton of stuff:

amy@amy-laptop:~$ ps -A
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
  127 ?        00:00:00 kseriod
  165 ?        00:00:00 pdflush
  166 ?        00:00:00 pdflush
  167 ?        00:00:00 kswapd0
  208 ?        00:00:00 aio/0
 1469 ?        00:00:00 ksuspend_usbd
 1472 ?        00:00:00 khubd
 1496 ?        00:00:00 ata/0
 1502 ?        00:00:00 ata_aux
 1509 ?        00:00:00 khpsbpkt
 1747 ?        00:00:00 knodemgrd_0
 1751 ?        00:00:00 scsi_eh_0
 1753 ?        00:00:01 scsi_eh_1
 2469 ?        00:00:00 scsi_eh_2
 2472 ?        00:00:00 usb-storage
 2496 ?        00:00:16 mount.ntfs
 2517 ?        00:00:00 loop0
 2530 ?        00:00:00 kjournald
 2735 ?        00:00:00 udevd
 3041 ?        00:00:00 tifm
 3056 ?        00:00:00 kmmcd
 3083 ?        00:00:00 pccardd
 3087 ?        00:00:00 kpsmoused
 3282 ?        00:00:44 b43
 4598 tty4     00:00:00 getty
 4601 tty5     00:00:00 getty
 4607 tty2     00:00:00 getty
 4611 tty3     00:00:00 getty
 4613 tty6     00:00:00 getty
 4781 ?        00:00:00 acpid
 4823 ?        00:00:00 kondemand/0
 4884 ?        00:00:00 syslogd
 4937 ?        00:00:00 dd
 4939 ?        00:00:00 klogd
 4961 ?        00:00:01 dbus-daemon
 4977 ?        00:00:01 NetworkManager
 4991 ?        00:00:00 NetworkManagerD
 5004 ?        00:00:00 system-tools-ba
 5031 ?        00:00:00 avahi-daemon
 5032 ?        00:00:00 avahi-daemon
 5059 ?        00:00:00 atieventsd
 5085 ?        00:00:00 cupsd
 5154 ?        00:00:00 dhcdbd
 5173 ?        00:00:01 hald
 5176 ?        00:00:00 console-kit-dae
 5177 ?        00:00:00 hald-runner
 5257 ?        00:00:00 hald-addon-inpu
 5259 ?        00:00:00 hald-addon-cpuf
 5260 ?        00:00:00 hald-addon-acpi
 5288 ?        00:00:00 hald-addon-stor
 5292 ?        00:00:01 hald-addon-stor
 5311 ?        00:00:00 ipolldevd
 5328 ?        00:00:00 hcid
 5346 ?        00:00:00 btaddconn
 5347 ?        00:00:00 btdelconn
 5356 ?        00:00:00 bluetoothd-serv
 5362 ?        00:00:00 krfcommd
 5392 ?        00:00:00 bluetoothd-serv
 5452 ?        00:00:00 gdm
 5456 ?        00:00:00 gdm
 5460 tty7     00:03:48 Xorg
 5559 ?        00:00:00 atd
 5573 ?        00:00:00 cron
 5654 tty1     00:00:00 getty
 5666 tty7     00:00:00 Xorg
 5712 ?        00:00:00 avahi-autoipd
 5713 ?        00:00:00 avahi-autoipd
 5716 ?        00:00:01 gconfd-2
 5718 ?        00:00:00 gnome-keyring-d
 5720 ?        00:00:00 x-session-manag
 5812 ?        00:00:00 seahorse-agent
 5816 ?        00:00:00 dbus-daemon
 5817 ?        00:00:03 gnome-settings-
 5831 ?        00:00:03 pulseaudio
 5834 ?        00:00:00 gconf-helper
 5847 ?        00:00:05 gnome-screensav
 5848 ?        00:00:00 compiz
 5854 ?        00:00:13 gnome-panel
 5857 ?        00:00:05 nautilus
 5870 ?        00:00:00 bonobo-activati
 5893 ?        00:00:00 gvfsd
 5903 ?        00:00:00 gvfs-fuse-daemo
 5936 ?        00:00:17 compiz.real
 5937 ?        00:00:00 bluetooth-apple
 5940 ?        00:00:00 update-notifier
 5947 ?        00:00:00 tracker-applet
 5950 ?        00:00:00 trackerd
 5954 ?        00:00:03 nm-applet
 5955 ?        00:00:00 python
 5957 ?        00:00:00 gnome-volume-ma
 5958 ?        00:00:00 gnome-power-man
 5960 ?        00:00:00 gvfsd-burn
 6000 ?        00:00:00 gvfsd-trash
 6003 ?        00:00:00 trashapplet
 6013 ?        00:00:00 evolution-data-
 6030 ?        00:00:00 sh
 6031 ?        00:00:00 compiz-decorato
 6033 ?        00:00:06 gtk-window-deco
 6049 ?        00:00:00 wpa_supplicant
 6078 ?        00:00:00 mixer_applet2
 6082 ?        00:00:00 fast-user-switc
 6083 ?        00:00:00 dhclient
 6330 ?        00:00:00 dpkg
 6331 ?        00:00:00 frontend
 6337 ?        00:00:00 ssl-cert.postin
 6354 ?        01:23:49 whiptail
 7946 ?        00:00:00 dbus-daemon
 7947 ?        00:00:00 dbus-launch
 8206 ?        00:00:00 gvfsd-smb-brows
 8697 ?        00:00:00 evolution-alarm
 9357 ?        00:00:09 firefox
 9414 ?        00:00:00 gnome-terminal
 9416 ?        00:00:00 gnome-pty-helpe
 9417 pts/1    00:00:00 bash
 9434 pts/1    00:00:00 ps
amy@amy-laptop:
[B]
Where do I start?[/B]

---

### Post by gal_amy on 2008-07-31
> **rockerphil said:**
> to take a look at all the processes running in the background run this:

ps -A

that'll list everything running in the background, and you can kill any that you don't need using:

killall <appname>

or you can use:

sudo kill <processnumber>

hope this helps,

Phil

----------------
Now playing: [Nirvana - Smells Like Teens Spirit](http://www.foxytunes.com/artist/nirvana/track/smells+like+teens+spirit)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)


WOW!  THere is a ton of stuff:

amy@amy-laptop:~$ ps -A
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
  127 ?        00:00:00 kseriod
  165 ?        00:00:00 pdflush
  166 ?        00:00:00 pdflush
  167 ?        00:00:00 kswapd0
  208 ?        00:00:00 aio/0
 1469 ?        00:00:00 ksuspend_usbd
 1472 ?        00:00:00 khubd
 1496 ?        00:00:00 ata/0
 1502 ?        00:00:00 ata_aux
 1509 ?        00:00:00 khpsbpkt
 1747 ?        00:00:00 knodemgrd_0
 1751 ?        00:00:00 scsi_eh_0
 1753 ?        00:00:01 scsi_eh_1
 2469 ?        00:00:00 scsi_eh_2
 2472 ?        00:00:00 usb-storage
 2496 ?        00:00:16 mount.ntfs
 2517 ?        00:00:00 loop0
 2530 ?        00:00:00 kjournald
 2735 ?        00:00:00 udevd
 3041 ?        00:00:00 tifm
 3056 ?        00:00:00 kmmcd
 3083 ?        00:00:00 pccardd
 3087 ?        00:00:00 kpsmoused
 3282 ?        00:00:44 b43
 4598 tty4     00:00:00 getty
 4601 tty5     00:00:00 getty
 4607 tty2     00:00:00 getty
 4611 tty3     00:00:00 getty
 4613 tty6     00:00:00 getty
 4781 ?        00:00:00 acpid
 4823 ?        00:00:00 kondemand/0
 4884 ?        00:00:00 syslogd
 4937 ?        00:00:00 dd
 4939 ?        00:00:00 klogd
 4961 ?        00:00:01 dbus-daemon
 4977 ?        00:00:01 NetworkManager
 4991 ?        00:00:00 NetworkManagerD
 5004 ?        00:00:00 system-tools-ba
 5031 ?        00:00:00 avahi-daemon
 5032 ?        00:00:00 avahi-daemon
 5059 ?        00:00:00 atieventsd
 5085 ?        00:00:00 cupsd
 5154 ?        00:00:00 dhcdbd
 5173 ?        00:00:01 hald
 5176 ?        00:00:00 console-kit-dae
 5177 ?        00:00:00 hald-runner
 5257 ?        00:00:00 hald-addon-inpu
 5259 ?        00:00:00 hald-addon-cpuf
 5260 ?        00:00:00 hald-addon-acpi
 5288 ?        00:00:00 hald-addon-stor
 5292 ?        00:00:01 hald-addon-stor
 5311 ?        00:00:00 ipolldevd
 5328 ?        00:00:00 hcid
 5346 ?        00:00:00 btaddconn
 5347 ?        00:00:00 btdelconn
 5356 ?        00:00:00 bluetoothd-serv
 5362 ?        00:00:00 krfcommd
 5392 ?        00:00:00 bluetoothd-serv
 5452 ?        00:00:00 gdm
 5456 ?        00:00:00 gdm
 5460 tty7     00:03:48 Xorg
 5559 ?        00:00:00 atd
 5573 ?        00:00:00 cron
 5654 tty1     00:00:00 getty
 5666 tty7     00:00:00 Xorg
 5712 ?        00:00:00 avahi-autoipd
 5713 ?        00:00:00 avahi-autoipd
 5716 ?        00:00:01 gconfd-2
 5718 ?        00:00:00 gnome-keyring-d
 5720 ?        00:00:00 x-session-manag
 5812 ?        00:00:00 seahorse-agent
 5816 ?        00:00:00 dbus-daemon
 5817 ?        00:00:03 gnome-settings-
 5831 ?        00:00:03 pulseaudio
 5834 ?        00:00:00 gconf-helper
 5847 ?        00:00:05 gnome-screensav
 5848 ?        00:00:00 compiz
 5854 ?        00:00:13 gnome-panel
 5857 ?        00:00:05 nautilus
 5870 ?        00:00:00 bonobo-activati
 5893 ?        00:00:00 gvfsd
 5903 ?        00:00:00 gvfs-fuse-daemo
 5936 ?        00:00:17 compiz.real
 5937 ?        00:00:00 bluetooth-apple
 5940 ?        00:00:00 update-notifier
 5947 ?        00:00:00 tracker-applet
 5950 ?        00:00:00 trackerd
 5954 ?        00:00:03 nm-applet
 5955 ?        00:00:00 python
 5957 ?        00:00:00 gnome-volume-ma
 5958 ?        00:00:00 gnome-power-man
 5960 ?        00:00:00 gvfsd-burn
 6000 ?        00:00:00 gvfsd-trash
 6003 ?        00:00:00 trashapplet
 6013 ?        00:00:00 evolution-data-
 6030 ?        00:00:00 sh
 6031 ?        00:00:00 compiz-decorato
 6033 ?        00:00:06 gtk-window-deco
 6049 ?        00:00:00 wpa_supplicant
 6078 ?        00:00:00 mixer_applet2
 6082 ?        00:00:00 fast-user-switc
 6083 ?        00:00:00 dhclient
 6330 ?        00:00:00 dpkg
 6331 ?        00:00:00 frontend
 6337 ?        00:00:00 ssl-cert.postin
 6354 ?        01:23:49 whiptail
 7946 ?        00:00:00 dbus-daemon
 7947 ?        00:00:00 dbus-launch
 8206 ?        00:00:00 gvfsd-smb-brows
 8697 ?        00:00:00 evolution-alarm
 9357 ?        00:00:09 firefox
 9414 ?        00:00:00 gnome-terminal
 9416 ?        00:00:00 gnome-pty-helpe
 9417 pts/1    00:00:00 bash
 9434 pts/1    00:00:00 ps
amy@amy-laptop:
[B]
Where do I start?  I tried killall update-notifier, but that didn't help[/B]

---

### Post by bodhi.zazen on 2008-07-31
Looks like the problem is dpkg

> 6330 ?        00:00:00 dpkg

So ....

```
sudo kill -9 6330
```

---

### Post by rockerphil on 2008-07-31
yup, i'd start there, that seems to be stopping you from running the dpkg command, so i'd run this:

sudo killall dpkg

hope it helps, 

Phil

---

### Post by gal_amy on 2008-07-31
> **bodhi.zazen said:**
> Looks like the problem is dpkg



So ....

```
sudo kill -9 6330
```


a[B]my@amy-laptop:~$ sudo kill -9 6330
[sudo] password for amy: 
amy@amy-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
 

Still won't work.  Why is so much loaded?  Looks almost like a Windows bloat.  Is this normal for first time users?  Did I do something wrong in the install?  I tried the live cd and I see that nothing is loaded, so of course the package manager works.  [/B]

---

### Post by gal_amy on 2008-07-31
> **Shazaam said:**
> You need to add sudo in front of the command....
```
sudo dpkg --configure -a
```

**Thanks --- trying again.  So is this something I'll have to do every log on?**

---

### Post by a0u on 2008-07-31
> **gal_amy said:**
> **Thanks --- trying again.  So is this something I'll have to do every log on?**

You only need to run
```
sudo dpkg --configure -a
```
if an update or installation becomes interrupted, and a package is left improperly configured.  Normally this shouldn't happen.

---

### Post by bodhi.zazen on 2008-07-31
> **gal_amy said:**
> a[B]my@amy-laptop:~$ sudo kill -9 6330
[sudo] password for amy: 
amy@amy-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
 

Still won't work.  Why is so much loaded?  Looks almost like a Windows bloat.  Is this normal for first time users?  Did I do something wrong in the install?  I tried the live cd and I see that nothing is loaded, so of course the package manager works.  [/B]

It takes a little time to learn a new OS is all.

> **gal_amy said:**
> **Thanks --- trying again.  So is this something I'll have to do every log on?**

No, not at all. This particular problem is uncommon, the problem with dpkg is rare. Did you interrupt the installation of a package ?

Also, no need to post in **BOLD**

---

### Post by gal_amy on 2008-07-31
> **a0u said:**
> You only need to run
```
sudo dpkg --configure -a
```
if an update or installation becomes interrupted, and a package is left improperly configured.  Normally this shouldn't happen.

**THANKS to Everyone.  I hope someone benefits from this thread.  :)**

---

