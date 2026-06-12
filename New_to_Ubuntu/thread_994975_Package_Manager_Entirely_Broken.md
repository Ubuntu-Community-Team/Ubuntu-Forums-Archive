---
title: "Package Manager Entirely Broken"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by daniel.j on 2008-11-27
I have finally succeeded installing Ubuntu and running it off the hard drive instead of the livecd but the package manager seems to be broken.

I get this error:

Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

trying to do any of these commands:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove

This is a problem.

Thanks in advance for the help.

---

### Post by halitech on 2008-11-27
open a terminal and post the results of```
cat /etc/apt/sources.list
```

---

### Post by daniel.j on 2008-11-27
In its entirety:

danielj@lovemachine:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
danielj@lovemachine:~$

---

### Post by halitech on 2008-11-27
ok, so no obviously issues with the sources file. dumb question but are you connected to the internet with this machine?

also, how are you trying to do the update? (ie. what are you typing in or clicking on)

---

### Post by llamakc on 2008-11-27
OP: what are the permissions of the file

/var/lib/apt/lists/lock ?

Should be:

```

-rw-r----- 1 root root 0 2008-10-17 21:31 lock

```

You can find this information in a Terminal with:

```

ls -l /var/lib/apt/lists/lock

```

---

### Post by daniel.j on 2008-11-27
Permissions for the /var/lib/apt/lists/lock file are as follows:

danielj@lovemachine:~$ ls -l /var/lib/apt/lists/lock
-rw-r----- 1 root root 0 2008-11-26 17:53 /var/lib/apt/lists/lock
danielj@lovemachine:~$

---

### Post by llamakc on 2008-11-27
Is there another package manager running?

```

ps aux

```

```

ps aux | grep dpkg

```

---

### Post by daniel.j on 2008-11-27
I am connected to the internet and I've tried to type in all these commands:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove

I've also tried accessing the package manager from the right click menu on the notification icon next to the networking icon in the taskbar.

I've also tried the add/remove programs app and that gives me this error message:
> 
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by daniel.j on 2008-11-27
Code Results for ps aux:

> USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2844  1688 ?        Ss   10:24   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   10:24   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   10:24   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   10:24   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   10:24   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   10:24   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   10:24   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   10:24   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   10:24   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   10:24   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   10:24   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   10:24   0:00 [kblockd/0]
root        47  0.0  0.0      0     0 ?        S<   10:24   0:00 [kblockd/1]
root        50  0.0  0.0      0     0 ?        S<   10:24   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   10:24   0:00 [kacpi_notify]
root       170  0.0  0.0      0     0 ?        S<   10:24   0:00 [kseriod]
root       212  0.0  0.0      0     0 ?        S    10:24   0:00 [pdflush]
root       213  0.0  0.0      0     0 ?        S    10:24   0:00 [pdflush]
root       214  0.0  0.0      0     0 ?        S<   10:24   0:00 [kswapd0]
root       255  0.0  0.0      0     0 ?        S<   10:24   0:00 [aio/0]
root       256  0.0  0.0      0     0 ?        S<   10:24   0:00 [aio/1]
root      1599  0.0  0.0      0     0 ?        S<   10:24   0:00 [ksuspend_usbd]
root      1600  0.0  0.0      0     0 ?        S<   10:24   0:00 [khubd]
root      1642  0.0  0.0      0     0 ?        S<   10:24   0:00 [ata/0]
root      1643  0.0  0.0      0     0 ?        S<   10:24   0:00 [ata/1]
root      1644  0.0  0.0      0     0 ?        S<   10:24   0:00 [ata_aux]
root      1653  0.0  0.0      0     0 ?        S<   10:24   0:00 [khpsbpkt]
root      2364  0.0  0.0      0     0 ?        S<   10:24   0:00 [scsi_eh_0]
root      2366  0.0  0.0      0     0 ?        S<   10:24   0:00 [scsi_eh_1]
root      2392  0.0  0.0      0     0 ?        S<   10:24   0:00 [scsi_eh_2]
root      2394  0.0  0.0      0     0 ?        S<   10:24   0:00 [usb-storage]
root      2417  0.0  0.0      0     0 ?        S<   10:24   0:00 [scsi_eh_3]
root      2418  0.0  0.0      0     0 ?        S<   10:24   0:00 [scsi_eh_4]
root      2443  0.0  0.0      0     0 ?        S<   10:24   0:00 [knodemgrd_0]
root      2448  0.0  0.0      0     0 ?        S<   10:24   0:00 [scsi_eh_5]
root      2450  0.0  0.0      0     0 ?        S<   10:24   0:00 [scsi_eh_6]
root      2584  0.0  0.0      0     0 ?        S<   10:24   0:00 [kjournald]
root      2788  0.0  0.0   2408   956 ?        S<s  10:24   0:00 /sbin/udevd --daemon
root      3145  0.0  0.0      0     0 ?        S<   10:24   0:00 [kpsmoused]
root      4640  0.0  0.0   1716   512 tty4     Ss+  10:24   0:00 /sbin/getty 38400 tty4
root      4641  0.0  0.0   1716   512 tty5     Ss+  10:24   0:00 /sbin/getty 38400 tty5
root      4643  0.0  0.0   1716   508 tty2     Ss+  10:24   0:00 /sbin/getty 38400 tty2
root      4646  0.0  0.0   1716   504 tty3     Ss+  10:24   0:00 /sbin/getty 38400 tty3
root      4647  0.0  0.0   1716   508 tty6     Ss+  10:24   0:00 /sbin/getty 38400 tty6
root      4827  0.0  0.0   2456  1356 ?        Ss   10:24   0:00 /usr/sbin/acpid -c /etc/acpi
root      4855  0.0  0.0      0     0 ?        S<   10:24   0:00 [kondemand/0]
root      4856  0.0  0.0      0     0 ?        S<   10:24   0:00 [kondemand/1]
syslog    4940  0.0  0.0   1936   648 ?        Ss   10:24   0:00 /sbin/syslogd -u syslog
root      4994  0.0  0.0   1872   536 ?        S    10:24   0:00 /bin/dd bs 1 if /proc/kmsg o
klog      4996  0.0  0.1   3300  2100 ?        Ss   10:24   0:00 /sbin/klogd -P /var/run/klog
108       5018  0.0  0.0   2880  1348 ?        Ss   10:24   0:00 /usr/bin/dbus-daemon --syste
root      5034  0.0  0.1  12892  2100 ?        Ssl  10:24   0:00 /usr/sbin/NetworkManager --p
root      5048  0.0  0.0   3536  1332 ?        Ss   10:24   0:00 /usr/sbin/NetworkManagerDisp
root      5061  0.0  0.0   4112  1112 ?        Ss   10:24   0:00 /usr/bin/system-tools-backen
avahi     5081  0.0  0.0   2760  1416 ?        Ss   10:24   0:00 avahi-daemon: running [lovem
avahi     5082  0.0  0.0   2760   468 ?        Ss   10:24   0:00 avahi-daemon: chroot helper
root      5124  0.0  0.1   5920  2264 ?        Ss   10:24   0:00 /usr/sbin/cupsd
root      5190  0.0  0.0   2020   904 ?        Ss   10:24   0:00 /usr/sbin/dhcdbd --system
111       5209  0.0  0.2   6304  4320 ?        Ss   10:24   0:00 /usr/sbin/hald
root      5212  0.0  0.1   7884  2360 ?        Ssl  10:24   0:00 /usr/sbin/console-kit-daemon
root      5274  0.0  0.0   3352  1192 ?        S    10:24   0:00 hald-runner
root      5296  0.0  0.0   3428  1244 ?        S    10:24   0:00 /usr/lib/hal/hald-addon-cpuf
111       5297  0.0  0.0   2204   904 ?        S    10:24   0:00 hald-addon-acpi: listening o
root      5301  0.0  0.0   3416  1160 ?        S    10:24   0:00 hald-addon-input: Listening 
root      5315  0.0  0.0   3420  1152 ?        S    10:24   0:00 hald-addon-storage: polling 
root      5317  0.0  0.0   3420  1156 ?        S    10:24   0:00 hald-addon-storage: polling 
root      5319  0.0  0.0   3420  1148 ?        S    10:24   0:00 hald-addon-storage: polling 
root      5321  0.0  0.0   3420  1152 ?        S    10:24   0:00 hald-addon-storage: polling 
root      5324  0.0  0.0   3420  1156 ?        S    10:24   0:00 hald-addon-storage: polling 
root      5347  0.0  0.0   3172  1264 ?        Ss   10:24   0:00 /usr/sbin/hcid -x -s
root      5353  0.0  0.0      0     0 ?        S<   10:24   0:00 [btaddconn]
root      5354  0.0  0.0      0     0 ?        S<   10:24   0:00 [btdelconn]
root      5365  0.0  0.0   3084  1296 ?        S    10:24   0:00 /usr/lib/bluetooth/bluetooth
root      5366  0.0  0.0   3020  1108 ?        S    10:24   0:00 /usr/lib/bluetooth/bluetooth
root      5374  0.0  0.0      0     0 ?        S<   10:24   0:00 [krfcommd]
root      5412  0.0  0.0  14060  1604 ?        Ss   10:24   0:00 /usr/sbin/gdm
root      5415  0.0  0.1  14516  2996 ?        S    10:24   0:00 /usr/sbin/gdm
root      5419  1.7  1.0  27176 20240 tty7     Ss+  10:24   1:11 /usr/bin/X :0 -br -audit 0 -
daemon    5484  0.0  0.0   1984   416 ?        Ss   10:24   0:00 /usr/sbin/atd
root      5498  0.0  0.0   2104   892 ?        Ss   10:24   0:00 /usr/sbin/cron
root      5578  0.0  0.0   1716   512 tty1     Ss+  10:24   0:00 /sbin/getty 38400 tty1
dhcp      5581  0.0  0.0   2440  1180 ?        S    10:24   0:00 /sbin/dhclient -1 -lf /var/l
danielj   5671  0.0  0.2   7220  4284 ?        S    10:24   0:01 /usr/lib/libgconf2-4/gconfd-
danielj   5673  0.0  0.1  14340  2040 ?        S    10:24   0:00 /usr/bin/gnome-keyring-daemo
danielj   5674  0.0  0.3  28872  7500 ?        Ssl  10:24   0:00 x-session-manager
danielj   5785  0.0  0.3  23048  6768 ?        Ss   10:25   0:00 /usr/bin/seahorse-agent --ex
danielj   5789  0.0  0.0   2696  1116 ?        Ss   10:25   0:00 dbus-daemon --fork --print-a
danielj   5790  0.0  0.4  39600  9896 ?        Sl   10:25   0:00 gnome-settings-daemon
danielj   5798  0.1  0.2  28480  5756 ?        Sl   10:25   0:05 /usr/bin/pulseaudio --log-ta
danielj   5806  0.0  0.1   5776  2248 ?        S    10:25   0:00 /usr/lib/pulseaudio/pulse/gc
danielj   5815  0.1  0.2  15208  4652 ?        Ss   10:25   0:04 gnome-screensaver
danielj   5816  0.1  0.6  20704 12160 ?        S    10:25   0:04 /usr/bin/metacity --replace
danielj   5822  0.1  1.0  37960 21640 ?        S    10:25   0:04 gnome-panel --sm-client-id d
danielj   5823  0.0  1.1  50104 22956 ?        S    10:25   0:00 nautilus --no-default-window
danielj   5846  0.0  0.1  32892  3176 ?        Ssl  10:25   0:00 /usr/lib/bonobo-activation/b
danielj   5849  0.0  0.1   5372  2080 ?        S    10:25   0:00 /usr/lib/gvfs/gvfsd
danielj   5855  0.0  0.0  29048  1876 ?        Ssl  10:25   0:00 /usr/lib/gvfs//gvfs-fuse-dae
danielj   5859  0.0  0.2  14604  5728 ?        S    10:25   0:00 bluetooth-applet --singleton
danielj   5862  0.0  0.7  26980 14508 ?        S    10:25   0:00 update-notifier
danielj   5867  0.0  0.2  15216  5524 ?        S    10:25   0:00 tracker-applet
danielj   5869  0.0  0.4  28660  9540 ?        Sl   10:25   0:00 /usr/lib/evolution/2.22/evol
danielj   5871  0.0  0.5  31508 10388 ?        SNl  10:25   0:00 trackerd
danielj   5876  0.0  0.2  20672  4604 ?        Ss   10:25   0:00 /usr/lib/gnome-volume-manage
danielj   5877  0.0  0.6  24268 12156 ?        S    10:25   0:00 python /usr/share/system-con
danielj   5878  0.0  0.7  27996 14980 ?        S    10:25   0:01 nm-applet --sm-disable
danielj   5880  0.0  0.3  23068  7372 ?        Ss   10:25   0:00 gnome-power-manager
danielj   5890  0.0  0.5  23316 10184 ?        S    10:25   0:00 /usr/lib/gnome-applets/trash
danielj   5892  0.0  0.1   5372  2128 ?        S    10:25   0:00 /usr/lib/gvfs/gvfsd-burn --s
danielj   5899  0.0  0.1  13840  2520 ?        S    10:25   0:00 /usr/lib/gvfs/gvfsd-trash --
danielj   5909  0.0  0.7  44360 14724 ?        Sl   10:25   0:00 /usr/lib/gnome-applets/mixer
danielj   5913  0.0  0.6  26032 13200 ?        S    10:25   0:00 /usr/lib/fast-user-switch-ap
danielj   5949  4.6  4.8 190032 96744 ?        Sl   10:26   2:57 /usr/lib/firefox-3.0/firefox
danielj   6065  7.1  1.0  74416 20296 ?        Sl   11:30   0:00 gnome-terminal
danielj   6067  0.0  0.0   2912   856 ?        S    11:30   0:00 gnome-pty-helper
danielj   6068  2.2  0.1   5628  3040 pts/0    Ss   11:30   0:00 bash
danielj   6085  0.0  0.0   2644  1004 pts/0    R+   11:30   0:00 ps aux


Code results for ps aux | grep dpkg

> danielj   6087  0.0  0.0   3004   768 pts/0    R+   11:31   0:00 grep dpkg

---

### Post by llamakc on 2008-11-27
Try running Synaptic. You reach that in the menu via:

System > Administration > Synaptic Package Manager

IF that starts up, Go to Settings > Repositories

Click on "Download from:" and choose "other". Next, click "Select Best Server". When it has chosen the 'best server' for you, select it. Close out of the 'Settings' dialog and reload.

See if you can now 'mark all upgrades' and 'apply'.

---

### Post by daniel.j on 2008-11-27
This is the result of trying to run Synaptic:

E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by llamakc on 2008-11-27
Is your disk or partition full?

```

df -h

```

"The open() failed" error is typically fixed with

```

sudo dpkg --configure -a

```

Try re-running that.

---

### Post by daniel.j on 2008-11-27
No disk/partition is filled above the 4% mark.

I ran the command and the red icon changed to gray. It now states that 'a package manager is working' but when I try to run Synaptic I get this error still:

> E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
**E: _cache->open() failed, please report.**

---

### Post by llamakc on 2008-11-27
Only one package manager may run at a time. If the icon is still 'gray' you must wait until it disappears or shows an 'updates available' status. You can not run Synaptic while "Update Manager" is running.

I would wait until it is no longer 'working' and then I would open a Terminal and run:

```

sudo aptitude update

```

And see if that completes successfully.

How "new" of an install is this? What else did you install (if any) after getting Ubuntu installed to disk?

---

### Post by daniel.j on 2008-11-27
I'm fairly certain there is only one 'manager' running.

I ran the code and it fetched a bunch of packages but I got this after all that fetching:

> Fetched 997kB in 12s (81.4kB/s)                                                 
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache

Is there a way I can check system processes to see if there is something running that might be causing this?

> How "new" of an install is this? What else did you install (if any) after getting Ubuntu installed to disk? 

Brand new. I abandoned Windows and let Ubuntu delete my whole *unrecoverable* hard drive! 

I have not been able to install anything else :( No package manager or add/remove programs.

---

### Post by llamakc on 2008-11-27
Was the install process interrupted at any point? 

This is most likely my last suggestion. Sorry I have not been able to help you fix this (yet).

```

sudo rm /var/cache/apt/*.bin

```

And then:

```

sudo aptitude update

```

The first one REMOVES the package cache, which is obviously corrupted. Typically you should NOT take forum recommendations to remove any files from your system. I can vouch that this method does work (on a working system), as I just tried it on my own machine.

The second command reloads from your sources.list file.

Good luck! I'm hoping this one does it for you.

---

### Post by handydan918 on 2008-11-27
Quoth danielj...

> I abandoned Windows and let Ubuntu delete my whole *unrecoverable* hard drive!



So I begin to suspect a possible hard drive issue? might want to eliminate it as a possibility at least...

---

### Post by kenworth on 2008-11-27
I have same problem. Locating 'best server' did not work.

---

### Post by daniel.j on 2008-11-27
It was only unrecoverable because I freaked out and deleted it all without *really* trying to retrieve the data. I just gave up in exasperation. 

I'm beginning to think there might be a problem with it though.

I'm gonna try a fresh install tonight and I will let everybody know what happens tomorrow.

As always, thanks for the help!

---

### Post by mkvnmtr on 2008-11-27
I don't see where you listed the specs of your machine or which distro you are using. It might help to know. If it is 8.10 and a reinstall doesn't change things it might be a bug and 8.04 will do better until you find out a workaround.

---

### Post by daniel.j on 2008-11-27
Hp Pavillion

AMD 64 Dual Core
250 GB Ram
2,048 MB Memory
Nvidia Graphics Card

Ubuntu 8.04

---

### Post by ByteJuggler on 2008-11-27
I'd suggest you download the diagnostic CD ISO for your hard disk from it's manufacturers website and use it to do a full test include destructive surface scan of the hard drive, to ensure you don't have hidden hardware problems causing your issues.  What brand drive is it?

---

### Post by Mr. Picklesworth on 2008-11-27
Do you encounter errors for any administrative tasks outside of package management?

To diagnose this problem, it could be helpful to manually inspect some directories used by the system.

Let's try the output of:
ls -l /var/cache/apt
ls -l /var/cache/apt/archives/

And does running dpkg directly work?

---

### Post by daniel.j on 2008-11-28
I tried to reinstall and now it won't install at all!

I'm gonna try to burn the diagnostic cd for the hard drive after I go buy some blank cd's today. (I ran out burning different versions of Linux but none of them will install properly)

I'm also gonna try to use one of those "ultimate boot" cd's and see if one them will do the trick.

---

### Post by ByteJuggler on 2008-11-28
> **daniel.j said:**
> II'm gonna try to burn the diagnostic cd for the hard drive after I go buy some blank cd's today. (I ran out burning different versions of Linux but none of them will install properly)

This is almost certainly pointing to some sort of hardware issue...

---

