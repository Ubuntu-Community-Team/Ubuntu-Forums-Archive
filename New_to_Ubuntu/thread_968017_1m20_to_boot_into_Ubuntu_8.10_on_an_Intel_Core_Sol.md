---
title: "1m20 to boot into Ubuntu 8.10 on an Intel Core Solo... does that sound right to you?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by the8thstar on 2008-11-02
I did a fresh install of 8.10 and I have been surprised to see a significant increase in boot time. 8.04 used to boot in 45s and now it's 1m20s!!! (almost 100% increase).

I have used some tricks well known (profile, services, etc) to no avail. Is there some hardware fault anywhere or a problem with network detection/connection that' slowing down the system?

Your help will be very appreciated! Thanks!

---

### Post by unutbu on 2008-11-02
Perhaps try booting with the boot option 'quiet splash' removed. (See [http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4)
on how to add/remove boot option temporarily).

See if the computer pauses at a certain line.
Then tell us what you see.

If the above has been tried and nothing jumps out as clearly being the problem, then you could try installing the bootchart package. bootchart will generate a chart of all the processes that get run at boot time, and how long each process took.

---

### Post by the8thstar on 2008-11-02
Okay, thanks! I followed your advice and since nothing smashing showed up on the screen when I removed "quiet splash" from grub, I installed bootchart (results are posted in /var/log/bootchart).

I was surprised with the results as you will see in the screenshots: Bootchart actually hacks down my startup time to only 26s! (scr1) **[COLOR="Blue"]How is that possible? When does it stop its counting? before or after Gnome is up and working?[/COLOR]**

When I brought back "quiet splash" into grub, th startup time bumps up to 28s (scr2). Out of curiosity I tried the "profile" option, but in the end nothing changed - still 28s (scr3).

I am quite confused.

---

### Post by the8thstar on 2008-11-02
I recounted myself. Either Bootchart is wrong or it doesn't take some operations into account; the true boot time is still well above 1min, staring from the HP bios image and ending with a fully operational Gnome desktop.

---

### Post by unutbu on 2008-11-02
I believe bootchart stops when all the scripts in /etc/rc3.d/ have at least started.
That is, around the time you see the gdm login screen.
Bootchart does not measure the time it takes to launch any programs
set to run after logging in through GDM. 

Are you seeing the gdm login screen, or have you configured auto-login?

[list=1]
[*]
Perhaps go to System>Preferences>Sessions and see 
if there are any programs set to run which can be eliminated.
Things like Tracker and Update Notifier may be turned off. There are other ways
to get the information that Tracker provides, and without using such a huge amount of disk space, and you may choose to run Update Notifier manually (/usr/bin/update-manager)
instead of at the start of every session.

[*]Look at the output of 
```

ps axwwf
```

to see if there are any other processes that can be eliminated. Post the output if unsure.

[*]You might be able to boot a little faster by eliminating boot scripts from /etc/rc3.d that you don't need. However, you are only spending 28 seconds in this phase, so you probably won't be able to improve on this much. See [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

[*]Do you think the machine might be looking for a wireless network connection and is getting hung up when it isn't finding an access point?
[/list]

---

### Post by the8thstar on 2008-11-03
Thanks again for a detailed response. According to each of the points you made, here is what I can tell you.

**_ps axwwf_**

Here is the output of:
> ps axwwf


> 
PID TTY      STAT   TIME COMMAND
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00  \_ [migration/0]
    4 ?        S<     0:00  \_ [ksoftirqd/0]
    5 ?        S<     0:00  \_ [watchdog/0]
    6 ?        S<     0:00  \_ [events/0]
    7 ?        S<     0:00  \_ [khelper]
   46 ?        S<     0:00  \_ [kintegrityd/0]
   48 ?        S<     0:00  \_ [kblockd/0]
   50 ?        S<     0:00  \_ [kacpid]
   51 ?        S<     0:00  \_ [kacpi_notify]
  143 ?        S<     0:00  \_ [cqueue]
  147 ?        S<     0:00  \_ [kseriod]
  188 ?        S      0:00  \_ [pdflush]
  189 ?        S      0:00  \_ [pdflush]
  190 ?        S<     0:00  \_ [kswapd0]
  232 ?        S<     0:00  \_ [aio/0]
 1266 ?        S<     0:00  \_ [ksuspend_usbd]
 1269 ?        S<     0:00  \_ [khubd]
 1310 ?        S<     0:00  \_ [khpsbpkt]
 1342 ?        S<     0:00  \_ [ata/0]
 1346 ?        S<     0:00  \_ [ata_aux]
 1769 ?        S<     0:00  \_ [scsi_eh_0]
 1770 ?        S<     0:00  \_ [scsi_eh_1]
 1771 ?        S<     0:00  \_ [scsi_eh_2]
 1772 ?        S<     0:00  \_ [scsi_eh_3]
 1781 ?        S<     0:00  \_ [knodemgrd_0]
 2153 ?        S<     0:00  \_ [scsi_eh_4]
 2155 ?        S<     0:00  \_ [scsi_eh_5]
 2299 ?        S<     0:00  \_ [kjournald]
 3135 ?        S<     0:00  \_ [iwl3945/0]
 3176 ?        S<     0:00  \_ [iwl3945]
 3262 ?        S<     0:00  \_ [kmmcd]
 3313 ?        S<     0:00  \_ [kpsmoused]
 4825 ?        S<     0:00  \_ [kjournald]
 5495 ?        S<     0:00  \_ [kondemand/0]
 6031 ?        S<     0:00  \_ [btaddconn]
 6033 ?        S<     0:00  \_ [btdelconn]
 6067 ?        S<     0:00  \_ [krfcommd]
    1 ?        Ss     0:01 /sbin/init
 2806 ?        S<s    0:00 /sbin/udevd --daemon
 5256 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 5257 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 5264 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 5265 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 5266 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5444 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 5576 ?        Ss     0:00 /sbin/syslogd -u syslog
 5635 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5637 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 5669 ?        Ss     0:01 /bin/dbus-daemon --system
 5700 ?        Ss     0:00 avahi-daemon: running [the8thstar-laptop.local]
 5701 ?        Ss     0:00  \_ avahi-daemon: chroot helper
 5754 ?        Ss     0:00 /usr/sbin/cupsd
 5830 ?        Ss     0:00 /usr/sbin/hald
 5905 ?        S      0:00  \_ hald-runner
 5943 ?        S      0:00      \_ hald-addon-input: Listening on /dev/input/event2 /dev/input/event6 /dev/input/event7 /dev/input/event5 /dev/input/event3 /dev/input/event4 /dev/input/event1
 5959 ?        S      0:00      \_ /usr/lib/hal/hald-addon-cpufreq
 5960 ?        S      0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 5974 ?        S      0:00      \_ hald-addon-storage: polling /dev/scd0 (every 2 sec)
 5836 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 6023 ?        Ss     0:00 /usr/sbin/bluetoothd
 6090 ?        Ssl    0:00 /usr/sbin/NetworkManager
 7347 ?        S      0:00  \_ /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/run/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
 6094 ?        S      0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
 6097 ?        S      0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
 6193 ?        Ss     0:00 /usr/sbin/gdm
 6196 ?        S      0:00  \_ /usr/sbin/gdm
 6200 tty7     Ss+    0:42      \_ /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 6597 ?        Ssl    0:01      \_ x-session-manager
 6710 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 6732 ?        Ss     0:00          \_ /usr/bin/seahorse-agent --execute x-session-manager
 6750 ?        S      0:00          \_ /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
 6756 ?        S      0:00          \_ /bin/sh /usr/bin/compiz
 6832 ?        S      0:05          |   \_ /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering core ccp
 6848 ?        Ss     0:00          |       \_ /bin/sh -c /usr/bin/compiz-decorator
 6849 ?        S      0:00          |           \_ /bin/sh /usr/bin/compiz-decorator
 6851 ?        S      0:00          |               \_ /usr/bin/gtk-window-decorator
 6852 ?        S      0:01          \_ gnome-panel
 6854 ?        S      0:01          \_ nautilus --no-desktop --browser
 6897 ?        S      0:00          \_ update-notifier
 6898 ?        SNl    0:00          \_ trackerd
 6900 ?        S      0:00          \_ python /usr/share/system-config-printer/applet.py
 6903 ?        S      0:00          \_ tracker-applet
 6904 ?        S      0:00          \_ nm-applet --sm-disable
 6906 ?        S      0:01          \_ avant-window-navigator
 6264 ?        Ss     0:00 /usr/bin/system-tools-backends
 6307 ?        Ss     0:00 /usr/sbin/atd
 6335 ?        Ss     0:00 /usr/sbin/cron
 6713 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 6714 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
 6717 ?        Ssl    0:00 /usr/bin/pulseaudio -D --log-target=syslog
 6720 ?        S      0:00  \_ /usr/lib/pulseaudio/pulse/gconf-helper
 6722 ?        S      0:01 /usr/lib/libgconf2-4/gconfd-2
 6741 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 6753 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 6755 ?        Ssl    0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 6764 ?        S      0:00 /usr/lib/gvfs/gvfsd
 6794 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/the8thstar/.gvfs
 6843 ?        Ss     0:00 gnome-screensaver
 6856 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 6868 ?        S      0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
 6870 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 6874 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=20
 6877 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.12 /org/gtk/gvfs/exec_spaw/0
 6880 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.12 /org/gtk/gvfs/exec_spaw/1
 6910 ?        Ss     0:00 gnome-power-manager
 6916 ?        S      0:00 Places let-activation -p /usr/share/awn/applets/places.desktop -u 1225626892 -w 37748773 -o 0 -h 48
 6960 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 6966 ?        S      0:00 Trash Applet tivation -p /usr/share/awn/applets/trash.desktop -u 1225625514 -w 37748784 -o 0 -h 48
 6970 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 7442 ?        Sl     1:06 /usr/lib/firefox-3.0.3/firefox
 7749 ?        Sl     0:00 gnome-terminal
 7751 ?        S      0:00  \_ gnome-pty-helper
 7752 pts/0    Ss     0:00  \_ bash
 7777 pts/0    R+     0:00      \_ ps axwwf

I do recognize some apps and services of course (awn, gnome-vfs-daemon, etc), but others are quite foreign to me. I'm not sure where to go from there.


**_Network_**

My wireless is turned off by default (the manual switch is set to off), but the ethernet port is connected to a windows XP box from which I'm getting the Internet access (shared in XP settings). Maybe this is the problem, but I'm not sure how I can improve things.

[B][U]
GDM/Login[/U][/B]

I have set Ubuntu to start with autologin. I did this to save on boot time actually!

[B][U]
Startup Programs[/U][/B]

I have removed some of the startup services. The ones remaining are:

1. AT SPI Registry Wrapper - no idea what this does!
2. Avant Window Navigator
3. GNOME Keyring Daemon Wrapper
4. GNOME Settings Daemon
5. GNOME Settings Daemon Helper
6. Network Manager
7. Power Manager
8. Print Queue Applet
9. PulseAudio Session Management
10. Tracker
11. Tracker Applet
12. Window Manager

I understand I can get rid of Tracker and Tracker applets. How about the others?

Thanks,

The8th

---

### Post by unutbu on 2008-11-03
The fundamental mystery is why booting took 45s under 8.04, and 80s under 8.10.
Unfortunately, I don't know the answer to this. Since you did a fresh install, maybe 8.10 has certain utilities that are launched by default that were not present under 8.04?

Bootchart showed us what is happening during the first 28s of boot. 
The problem seems to be occurring after this phase.
Here is how you can tell what processes are occupying the CPU during the next phase:

Open a terminal and type```

gksu gedit /etc/rc.local
```
Insert this line into the file, *before* the "exit 0" line:
```

top -n20 -d5 -b > /tmp/top.out
```

This will create a file called /tmp/top.out, and it will run 'top' 20 times, once every 5 seconds. (So it will take 100 seconds to complete. Since the total boot process is taking 80 seconds, this should give us some snapshots of what the system is doing.)

Then post /tmp/top.out

When you are done analyzing the boot process, remove this line from /etc/rc.local.

Here are some other things you could try to reduce your boot time:

AWN+Compiz -- There are less resource-intensive ways to get the same functionality, but you may not get all the cool special effects and it may not look as beautiful. 
[list]
[*]You could keep awn+compiz, but instead of running them immediately at boot time,
you could instead run a script which will sleep for 30 seconds before launching awn and compiz.

If there is some other program that you always use immediately at start up, like a text editor, or firefox, we can setup the machine to launch this app first instead of awn+compiz. Then you can get to work immediately, and you won't notice the lack of awn+compiz. Later, by the time you need awn+compiz, the script will have launched them...
[*]Or, you might want to look for a leaner window manager. 
[/list]

Network Manager (nm-applet) -- This is a GUI to help you set up the configuration file /etc/network/interfaces. Once you have networking set up, there is no need to run this at boot

Bluetooth (/etc/init.d/bluetooth) -- If you don't have any bluetooth devices, you don't need to run this. If you do use bluetooth, but not immediately, this could be added to the awn+compiz script too, thus delaying when it gets launched.

Tracker -- if you are comfortable with the command line, it is possible to get rid of this

update-notifier -- not necessary with every boot

---

### Post by the8thstar on 2008-11-03
Okay, here goes... (that's the longest paste I've ever put on ubuntuforums.org)

> top - 22:08:57 up 0 min,  0 users,  load average: 1.84, 0.42, 0.14
Tasks:  83 total,   2 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s): 33.3%us, 21.4%sy,  0.0%ni,  9.3%id, 35.7%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   2063268k total,   111888k used,  1951380k free,     5668k buffers
Swap:  4000176k total,        0k used,  4000176k free,    60520k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 6292 root      20   0  8684 3280 2408 D 44.0  0.2   0:01.24 Xorg                                                                                               
 5752 messageb  20   0  2772  912  600 S  4.0  0.0   0:00.04 dbus-daemon                                                                                        
 6186 root      20   0  6768 2972 2460 S  4.0  0.1   0:00.02 nm-system-setti                                                                                    
 6575 root      20   0  1776  612  504 R  4.0  0.0   0:00.02 modprobe                                                                                           
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 S  0.0  0.0   0:00.02 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.0  0.0   0:00.02 busybox                                                                                            
  969 root      20   0  1180  260  192 S  0.0  0.0   0:00.10 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1408 1176 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6284 4048 3384 S  0.0  0.2   0:00.30 hald                                                                                               
 5922 root      20   0  8192 2432 1672 S  0.0  0.1   0:00.00 console-kit-dae                                                                                    
 5988 root      20   0  3364 1104  924 S  0.0  0.1   0:00.00 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1044  892 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2556 2128 S  0.0  0.1   0:00.02 NetworkManager                                                                                     
 6183 root      20   0  4244 1856 1556 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6285 root      20   0 14240 1608  884 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14240 1752 1024 S  0.0  0.1   0:00.00 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2412 1024  804 R  0.0  0.0   0:00.00 top                                                                                                
 6561 root      20   0  2248  864  744 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6562 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 6565 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 6573 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 6574 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            


top - 22:09:02 up 0 min,  1 user,  load average: 1.69, 0.41, 0.14
Tasks:  85 total,   1 running,  84 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.6%us,  9.4%sy,  0.0%ni, 16.0%id, 23.6%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2063268k total,   231388k used,  1831880k free,     6100k buffers
Swap:  4000176k total,        0k used,  4000176k free,    63892k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 6292 root      20   0  341m 6488 3888 S 41.6  0.3   0:03.32 Xorg                                                                                               
  969 root      20   0  1180  260  192 S  0.8  0.0   0:00.14 busybox                                                                                            
 5919 haldaemo  20   0  6288 4052 3384 S  0.8  0.2   0:00.34 hald                                                                                               
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.04 busybox                                                                                            
 5752 messageb  20   0  2772  920  600 S  0.4  0.0   0:00.06 dbus-daemon                                                                                        
 5922 root      20   0 16388 2520 1740 S  0.4  0.1   0:00.02 console-kit-dae                                                                                    
 6179 root      20   0 14632 2564 2132 S  0.4  0.1   0:00.04 NetworkManager                                                                                     
 6288 root      20   0 14740 3188 2272 S  0.4  0.2   0:00.02 gdm                                                                                                
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 S  0.0  0.0   0:00.02 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1444 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5988 root      20   0  3364 1108  924 S  0.0  0.1   0:00.00 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1044  892 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1612  888 S  0.0  0.1   0:00.00 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2420 1116  884 R  0.0  0.1   0:00.00 top                                                                                                
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 root      20   0 14740 1412  496 S  0.0  0.1   0:00.00 gdm                                                                                                
 6826 root      20   0  1844  512  440 S  0.0  0.0   0:00.00 Default                                                                                            
 6827 root      20   0  3328 1248 1068 D  0.0  0.1   0:00.00 hal-acl-tool                                                                                       
 6829 root      20   0  1844  280  204 D  0.0  0.0   0:00.00 Default                                                                                            
 6830 root      20   0   168   40   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 6835 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 6836 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:07 up 0 min,  1 user,  load average: 1.71, 0.44, 0.15
Tasks:  90 total,   2 running,  88 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.0%us, 15.0%sy,  0.0%ni,  1.4%id, 63.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   256804k used,  1806464k free,     8332k buffers
Swap:  4000176k total,        0k used,  4000176k free,    78980k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7113 the8thst  20   0  7736 4640 2176 D  8.0  0.2   0:00.40 gconfd-2                                                                                           
 7091 the8thst  20   0 28836 3956 2960 S  3.6  0.2   0:00.18 pulseaudio                                                                                         
 6825 the8thst  20   0 16436 5092 4148 S  2.0  0.2   0:00.10 x-session-manag                                                                                    
 7170 the8thst  20   0 16404 3872 2716 D  1.2  0.2   0:00.06 seahorse-agent                                                                                     
  969 root      20   0  1180  260  192 S  0.8  0.0   0:00.18 busybox                                                                                            
 5752 messageb  20   0  2772 1080  732 S  0.8  0.1   0:00.10 dbus-daemon                                                                                        
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.04 busybox                                                                                            
 5919 haldaemo  20   0  6288 4052 3384 S  0.4  0.2   0:00.36 hald                                                                                               
 5988 root      20   0  3364 1112  924 S  0.4  0.1   0:00.02 hald-runner                                                                                        
 6179 root      20   0 14632 2584 2148 S  0.4  0.1   0:00.06 NetworkManager                                                                                     
 6534 root      20   0  2420 1116  884 R  0.4  0.1   0:00.02 top                                                                                                
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 R  0.0  0.0   0:00.00 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  966 root      20   0  1180  220  164 S  0.0  0.0   0:00.04 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 D  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6292 root      20   0  341m 6552 3952 S  0.0  0.3   0:03.32 Xorg                                                                                               
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6855 root      20   0  5664 2120 1756 S  0.0  0.1   0:00.00 nm-dispatcher.a                                                                                    
 7066 the8thst  20   0  4740  592  280 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  664  444 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  2640  776  588 S  0.0  0.0   0:00.00 dbus-daemon                                                                                        
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7225 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 7230 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 7231 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:12 up 0 min,  1 user,  load average: 1.82, 0.48, 0.16
Tasks:  99 total,   3 running,  94 sleeping,   0 stopped,   2 zombie
Cpu(s): 17.4%us, 18.6%sy,  0.0%ni, 16.6%id, 47.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   274688k used,  1788580k free,     9564k buffers
Swap:  4000176k total,        0k used,  4000176k free,    86872k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 6292 root      20   0  347m 9.8m 4700 S  9.6  0.5   0:03.80 Xorg                                                                                               
 7293 the8thst  20   0 29956 6572 5088 S  2.4  0.3   0:00.12 gnome-settings-                                                                                    
 7498 the8thst  20   0  6508 3080 2308 D  2.4  0.1   0:00.12 compiz.real                                                                                        
 7170 the8thst  20   0 17572 6164 4528 R  2.0  0.3   0:00.16 seahorse-agent                                                                                     
  969 root      20   0  1180  260  192 S  0.8  0.0   0:00.22 busybox                                                                                            
 6825 the8thst  20   0 24632 5456 4460 D  0.8  0.3   0:00.14 x-session-manag                                                                                    
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.06 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.06 busybox                                                                                            
 5752 messageb  20   0  2772 1092  732 S  0.4  0.1   0:00.12 dbus-daemon                                                                                        
 6855 root      20   0  5664 2120 1756 S  0.4  0.1   0:00.02 nm-dispatcher.a                                                                                    
 7070 the8thst  20   0  2640  840  588 S  0.4  0.0   0:00.02 dbus-daemon                                                                                        
 7113 the8thst  20   0  7736 4644 2180 D  0.4  0.2   0:00.42 gconfd-2                                                                                           
 7253 the8thst  20   0 13916 3660 2992 S  0.4  0.2   0:00.02 gnome-keyring-d                                                                                    
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 R  0.0  0.0   0:00.04 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6288 4052 3384 S  0.0  0.2   0:00.36 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1112  924 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2420 1120  884 R  0.0  0.1   0:00.02 top                                                                                                
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 7066 the8thst  20   0  4740  592  280 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  664  444 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7091 the8thst  20   0 28836 3976 2980 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5552 2084 1776 S  0.0  0.1   0:00.00 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2000 1580 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7457 the8thst  20   0     0    0    0 Z  0.0  0.0   0:00.00 xrdb <defunct>                                                                                     
 7517 the8thst  20   0     0    0    0 Z  0.0  0.0   0:00.00 xrdb <defunct>                                                                                     
 7530 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 7535 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 7536 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:17 up 0 min,  1 user,  load average: 1.83, 0.51, 0.17
Tasks: 100 total,   2 running,  98 sleeping,   0 stopped,   0 zombie
Cpu(s): 44.5%us, 11.2%sy,  0.0%ni,  0.0%id, 44.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   309580k used,  1753688k free,    10280k buffers
Swap:  4000176k total,        0k used,  4000176k free,    98456k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7498 the8thst  20   0 21700  13m 5864 S 26.3  0.7   0:01.44 compiz.real                                                                                        
 7293 the8thst  20   0 47456  16m 8412 S 10.8  0.8   0:00.66 gnome-settings-                                                                                    
 7740 the8thst  20   0 16308 7756 6328 R  2.8  0.4   0:00.14 gtk-window-deco                                                                                    
 6292 root      20   0  366m  14m 5380 S  2.0  0.7   0:03.90 Xorg                                                                                               
 7113 the8thst  20   0  7732 4652 2184 S  1.6  0.2   0:00.50 gconfd-2                                                                                           
  969 root      20   0  1180  260  192 S  1.2  0.0   0:00.28 busybox                                                                                            
 7170 the8thst  20   0 17796 6392 4648 S  1.2  0.3   0:00.22 seahorse-agent                                                                                     
 6825 the8thst  20   0 24856 5772 4644 S  0.8  0.3   0:00.18 x-session-manag                                                                                    
 6534 root      20   0  2420 1124  884 R  0.4  0.1   0:00.04 top                                                                                                
 7070 the8thst  20   0  2772  864  592 S  0.4  0.0   0:00.04 dbus-daemon                                                                                        
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 S  0.0  0.0   0:00.06 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.0  0.0   0:00.06 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2772 1092  732 S  0.0  0.1   0:00.12 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6288 4052 3384 S  0.0  0.2   0:00.36 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1112  924 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7091 the8thst  20   0 28836 4004 3008 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5552 2084 1776 S  0.0  0.1   0:00.00 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2000 1580 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7637 the8thst  20   0 21172 2736 1380 S  0.0  0.1   0:00.00 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7762 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 7765 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 7768 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:22 up 0 min,  1 user,  load average: 1.68, 0.50, 0.17
Tasks: 107 total,   5 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s): 33.3%us, 17.1%sy,  0.0%ni, 15.5%id, 33.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2063268k total,   342060k used,  1721208k free,    11508k buffers
Swap:  4000176k total,        0k used,  4000176k free,   108580k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7857 the8thst  20   0 25304  12m 8376 D  6.0  0.6   0:00.30 avant-window-na                                                                                    
 7891 the8thst  20   0 24912  11m 8028 R  6.0  0.6   0:00.30 awn-applet-acti                                                                                    
 7809 the8thst  20   0 25148  11m 8376 D  5.2  0.6   0:00.26 gnome-panel                                                                                        
 6292 root      20   0  368m  15m 5892 R  4.4  0.8   0:04.12 Xorg                                                                                               
 7835 the8thst  20   0 24260 3336 2648 S  4.0  0.2   0:00.20 bonobo-activati                                                                                    
 7293 the8thst  20   0 47456  16m 8412 S  2.8  0.8   0:00.80 gnome-settings-                                                                                    
 7824 the8thst  20   0 39960  10m 8736 D  2.8  0.5   0:00.14 nautilus                                                                                           
 7854 the8thst  20   0 19168 8144 6696 S  2.0  0.4   0:00.10 nm-applet                                                                                          
 7881 the8thst  20   0 24572 9376 6660 R  2.0  0.5   0:00.10 gnome-power-man                                                                                    
 7740 the8thst  20   0 16920 8412 6916 S  1.2  0.4   0:00.20 gtk-window-deco                                                                                    
 5752 messageb  20   0  2772 1112  732 R  0.8  0.1   0:00.16 dbus-daemon                                                                                        
 7113 the8thst  20   0  7732 4684 2184 S  0.8  0.2   0:00.54 gconfd-2                                                                                           
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.08 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.08 busybox                                                                                            
  969 root      20   0  1180  260  192 S  0.4  0.0   0:00.30 busybox                                                                                            
 5919 haldaemo  20   0  6432 4360 3584 S  0.4  0.2   0:00.38 hald                                                                                               
 6534 root      20   0  2420 1132  884 R  0.4  0.1   0:00.06 top                                                                                                
 7070 the8thst  20   0  2772  948  592 S  0.4  0.0   0:00.06 dbus-daemon                                                                                        
 7498 the8thst  20   0 21700  13m 5924 S  0.4  0.7   0:01.46 compiz.real                                                                                        
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5784 4648 S  0.0  0.3   0:00.18 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7091 the8thst  20   0 28836 4036 3024 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5552 2092 1776 S  0.0  0.1   0:00.00 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2000 1580 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7637 the8thst  20   0 21172 3076 1716 S  0.0  0.1   0:00.00 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 8030 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8034 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8035 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:27 up 0 min,  1 user,  load average: 1.95, 0.57, 0.20
Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 59.2%us, 16.6%sy,  0.0%ni,  0.0%id, 24.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2063268k total,   389216k used,  1674052k free,    12516k buffers
Swap:  4000176k total,        0k used,  4000176k free,   118156k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7824 the8thst  20   0 67440  24m  12m S 22.4  1.2   0:01.26 nautilus                                                                                           
 6292 root      20   0  379m  21m 6792 S 11.6  1.1   0:04.70 Xorg                                                                                               
 7857 the8thst  20   0 25840  12m 8668 S  6.8  0.6   0:00.64 avant-window-na                                                                                    
 7809 the8thst  20   0 27188  14m  10m D  5.6  0.7   0:00.54 gnome-panel                                                                                        
 8112 the8thst  20   0 57380  11m 7584 S  5.2  0.6   0:00.26 awn-applet-acti                                                                                    
 7881 the8thst  20   0 26764  11m 7268 S  4.8  0.6   0:00.34 gnome-power-man                                                                                    
 8128 the8thst  20   0 25252  10m 7448 S  4.0  0.5   0:00.20 mixer_applet2                                                                                      
 8125 the8thst  20   0 30120  13m 8344 D  3.2  0.7   0:00.16 python                                                                                             
 7891 the8thst  20   0 26128  12m 8748 S  2.0  0.6   0:00.40 awn-applet-acti                                                                                    
 7113 the8thst  20   0  7732 4688 2184 S  1.2  0.2   0:00.60 gconfd-2                                                                                           
 7498 the8thst  20   0 21700  13m 5924 S  1.2  0.7   0:01.52 compiz.real                                                                                        
  969 root      20   0  1180  260  192 S  0.8  0.0   0:00.34 busybox                                                                                            
 5752 messageb  20   0  2948 1288  732 S  0.8  0.1   0:00.20 dbus-daemon                                                                                        
 5919 haldaemo  20   0  6432 4376 3584 S  0.8  0.2   0:00.42 hald                                                                                               
   48 root      15  -5     0    0    0 S  0.4  0.0   0:00.02 kblockd/0                                                                                          
 6534 root      20   0  2420 1136  884 R  0.4  0.1   0:00.08 top                                                                                                
 7070 the8thst  20   0  2904 1072  592 S  0.4  0.1   0:00.08 dbus-daemon                                                                                        
 7293 the8thst  20   0 47456  16m 8412 S  0.4  0.8   0:00.82 gnome-settings-                                                                                    
 7380 the8thst  20   0  5556 2156 1824 S  0.4  0.1   0:00.02 gvfsd                                                                                              
 7637 the8thst  20   0 21172 3080 1716 S  0.4  0.1   0:00.02 gnome-screensav                                                                                    
 7740 the8thst  20   0 17024 8476 6920 S  0.4  0.4   0:00.22 gtk-window-deco                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.4  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8184 the8thst  20   0 13996 2656 2252 S  0.4  0.1   0:00.02 gvfsd-trash                                                                                        
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 R  0.0  0.0   0:00.04 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 S  0.0  0.0   0:00.08 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.0  0.0   0:00.08 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5784 4648 S  0.0  0.3   0:00.18 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7091 the8thst  20   0 28836 4036 3024 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 19168 8144 6696 S  0.0  0.4   0:00.10 nm-applet                                                                                          
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8260 the8thst  20   0 10136 1688 1304 D  0.0  0.1   0:00.00 net                                                                                                
 8263 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8266 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8269 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:32 up 1 min,  1 user,  load average: 1.95, 0.59, 0.20
Tasks: 115 total,   4 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s): 30.5%us, 14.3%sy,  0.0%ni, 18.1%id, 36.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2063268k total,   407044k used,  1656224k free,    13040k buffers
Swap:  4000176k total,        0k used,  4000176k free,   124952k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7809 the8thst  20   0 44464  20m  12m S 12.0  1.0   0:01.14 gnome-panel                                                                                        
 8125 the8thst  20   0 37680  22m  11m S 12.0  1.1   0:00.76 python                                                                                             
 7854 the8thst  20   0 23900  12m 7940 S  6.0  0.6   0:00.40 nm-applet                                                                                          
 7824 the8thst  20   0 68252  25m  13m S  2.8  1.2   0:01.40 nautilus                                                                                           
 6292 root      20   0  377m  18m 7732 S  2.0  0.9   0:04.80 Xorg                                                                                               
 8128 the8thst  20   0 44452  15m  10m S  2.0  0.8   0:00.30 mixer_applet2                                                                                      
  969 root      20   0  1180  260  192 S  1.2  0.0   0:00.40 busybox                                                                                            
    4 root      15  -5     0    0    0 R  0.4  0.0   0:00.06 ksoftirqd/0                                                                                        
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.10 busybox                                                                                            
 7070 the8thst  20   0  2904 1104  592 S  0.4  0.1   0:00.10 dbus-daemon                                                                                        
 7113 the8thst  20   0  7732 4704 2184 S  0.4  0.2   0:00.62 gconfd-2                                                                                           
 7498 the8thst  20   0 21700  13m 5928 R  0.4  0.7   0:01.54 compiz.real                                                                                        
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 S  0.0  0.0   0:00.08 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 R  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.0  0.1   0:00.20 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.42 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.00 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2420 1140  884 R  0.0  0.1   0:00.08 top                                                                                                
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5788 4648 S  0.0  0.3   0:00.18 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7293 the8thst  20   0 47456  16m 8412 S  0.0  0.8   0:00.82 gnome-settings-                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2160 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7637 the8thst  20   0 21172 3080 1716 S  0.0  0.1   0:00.02 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7740 the8thst  20   0 17024 8480 6920 S  0.0  0.4   0:00.22 gtk-window-deco                                                                                    
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.64 avant-window-na                                                                                    
 7881 the8thst  20   0 26764  11m 7344 S  0.0  0.6   0:00.34 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 8489 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8492 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8495 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:37 up 1 min,  1 user,  load average: 1.80, 0.58, 0.20
Tasks: 115 total,   2 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.4%us,  6.0%sy,  0.0%ni, 90.8%id,  0.2%wa,  0.6%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   407712k used,  1655556k free,    13064k buffers
Swap:  4000176k total,        0k used,  4000176k free,   125364k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
  969 root      20   0  1180  260  192 S  0.8  0.0   0:00.44 busybox                                                                                            
 6292 root      20   0  377m  18m 7744 S  0.8  0.9   0:04.84 Xorg                                                                                               
 7824 the8thst  20   0 68252  25m  13m S  0.8  1.2   0:01.44 nautilus                                                                                           
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.10 busybox                                                                                            
 6060 root      20   0  3440 1064  912 S  0.4  0.1   0:00.02 hald-addon-stor                                                                                    
 6534 root      20   0  2420 1140  884 R  0.4  0.1   0:00.10 top                                                                                                
 7113 the8thst  20   0  7728 4768 2188 S  0.4  0.2   0:00.64 gconfd-2                                                                                           
 7498 the8thst  20   0 21700  13m 5928 S  0.4  0.7   0:01.56 compiz.real                                                                                        
 7637 the8thst  20   0 21172 3080 1716 S  0.4  0.1   0:00.04 gnome-screensav                                                                                    
 7809 the8thst  20   0 44464  20m  12m S  0.4  1.0   0:01.16 gnome-panel                                                                                        
 7881 the8thst  20   0 26764  11m 7344 S  0.4  0.6   0:00.36 gnome-power-man                                                                                    
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  966 root      20   0  1180  220  164 S  0.0  0.0   0:00.10 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 R  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.0  0.1   0:00.20 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.00 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.42 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5788 4648 S  0.0  0.3   0:00.18 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  2904 1104  592 S  0.0  0.1   0:00.10 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7293 the8thst  20   0 47456  16m 8412 S  0.0  0.8   0:00.82 gnome-settings-                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2160 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7740 the8thst  20   0 17024 8480 6920 S  0.0  0.4   0:00.22 gtk-window-deco                                                                                    
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 23900  12m 7940 S  0.0  0.6   0:00.40 nm-applet                                                                                          
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.64 avant-window-na                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 8709 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8714 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8715 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:42 up 1 min,  1 user,  load average: 1.65, 0.57, 0.20
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.0%us,  8.8%sy,  0.0%ni, 32.7%id, 45.7%wa,  0.6%hi,  0.2%si,  0.0%st
Mem:   2063268k total,   428540k used,  1634728k free,    13440k buffers
Swap:  4000176k total,        0k used,  4000176k free,   140212k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 8807 the8thst  20   0 73992  17m  12m D  8.4  0.9   0:00.42 firefox                                                                                            
 6292 root      20   0  377m  18m 7808 S  2.4  0.9   0:04.96 Xorg                                                                                               
 7824 the8thst  20   0 68264  25m  13m S  2.4  1.3   0:01.56 nautilus                                                                                           
  969 root      20   0  1180  260  192 S  1.2  0.0   0:00.50 busybox                                                                                            
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.12 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.12 busybox                                                                                            
 2154 root      15  -5     0    0    0 S  0.4  0.0   0:00.02 scsi_eh_4                                                                                          
 5752 messageb  20   0  2948 1288  732 S  0.4  0.1   0:00.22 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.4  0.1   0:00.02 avahi-daemon                                                                                       
 6534 root      20   0  2420 1140  884 R  0.4  0.1   0:00.12 top                                                                                                
 6825 the8thst  20   0 24856 5792 4648 S  0.4  0.3   0:00.20 x-session-manag                                                                                    
 7293 the8thst  20   0 47456  16m 8432 S  0.4  0.8   0:00.84 gnome-settings-                                                                                    
 7740 the8thst  20   0 17024 8480 6920 S  0.4  0.4   0:00.24 gtk-window-deco                                                                                    
 7809 the8thst  20   0 44596  20m  12m S  0.4  1.0   0:01.18 gnome-panel                                                                                        
 7857 the8thst  20   0 25840  12m 8668 S  0.4  0.6   0:00.66 avant-window-na                                                                                    
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.42 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  2904 1112  592 S  0.0  0.1   0:00.10 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7732 4772 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2160 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7498 the8thst  20   0 21700  13m 5936 S  0.0  0.7   0:01.56 compiz.real                                                                                        
 7637 the8thst  20   0 21172 3092 1728 S  0.0  0.1   0:00.04 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 23900  12m 7940 S  0.0  0.6   0:00.40 nm-applet                                                                                          
 7881 the8thst  20   0 26764  11m 7344 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 8937 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8940 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 8944 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:47 up 1 min,  1 user,  load average: 1.60, 0.58, 0.21
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 39.6%us,  9.2%sy,  0.0%ni, 12.8%id, 38.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   455100k used,  1608168k free,    13628k buffers
Swap:  4000176k total,        0k used,  4000176k free,   149676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 8807 the8thst  20   0  131m  39m  20m S 37.7  2.0   0:02.31 firefox                                                                                            
 6292 root      20   0  386m  19m 8396 S  3.2  1.0   0:05.12 Xorg                                                                                               
  969 root      20   0  1180  260  192 S  1.2  0.0   0:00.56 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.14 busybox                                                                                            
 7498 the8thst  20   0 21700  13m 5964 S  0.4  0.7   0:01.58 compiz.real                                                                                        
 7740 the8thst  20   0 17056 8812 7168 S  0.4  0.4   0:00.26 gtk-window-deco                                                                                    
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 S  0.0  0.0   0:00.12 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.0  0.1   0:00.22 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.02 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.42 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2420 1140  884 R  0.0  0.1   0:00.12 top                                                                                                
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5792 4648 S  0.0  0.3   0:00.20 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  2904 1120  592 S  0.0  0.1   0:00.10 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7732 4772 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7293 the8thst  20   0 47456  16m 8432 S  0.0  0.8   0:00.84 gnome-settings-                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2160 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7637 the8thst  20   0 21172 3092 1728 S  0.0  0.1   0:00.04 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7809 the8thst  20   0 44596  20m  12m S  0.0  1.0   0:01.18 gnome-panel                                                                                        
 7824 the8thst  20   0 68264  25m  13m S  0.0  1.3   0:01.56 nautilus                                                                                           
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 23900  12m 7940 S  0.0  0.6   0:00.40 nm-applet                                                                                          
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.66 avant-window-na                                                                                    
 7881 the8thst  20   0 26764  11m 7344 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 9176 root      20   0   168   40   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9179 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9182 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:52 up 1 min,  1 user,  load average: 1.47, 0.57, 0.20
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  6.4%sy,  0.0%ni, 92.4%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   455672k used,  1607596k free,    13644k buffers
Swap:  4000176k total,        0k used,  4000176k free,   150244k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
  969 root      20   0  1180  260  192 S  0.8  0.0   0:00.60 busybox                                                                                            
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.14 busybox                                                                                            
 6534 root      20   0  2420 1140  884 R  0.4  0.1   0:00.14 top                                                                                                
 8807 the8thst  20   0  131m  40m  20m S  0.4  2.0   0:02.33 firefox                                                                                            
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  966 root      20   0  1180  220  164 S  0.0  0.0   0:00.14 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.0  0.1   0:00.22 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.02 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.42 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6292 root      20   0  386m  19m 8396 S  0.0  1.0   0:05.12 Xorg                                                                                               
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5792 4648 S  0.0  0.3   0:00.20 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  2904 1120  592 S  0.0  0.1   0:00.10 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7732 4772 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7293 the8thst  20   0 47456  16m 8432 S  0.0  0.8   0:00.84 gnome-settings-                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2160 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7498 the8thst  20   0 21700  13m 5964 S  0.0  0.7   0:01.58 compiz.real                                                                                        
 7637 the8thst  20   0 21172 3092 1728 S  0.0  0.1   0:00.04 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7740 the8thst  20   0 17056 8812 7168 S  0.0  0.4   0:00.26 gtk-window-deco                                                                                    
 7809 the8thst  20   0 44596  20m  12m S  0.0  1.0   0:01.18 gnome-panel                                                                                        
 7824 the8thst  20   0 68264  25m  13m S  0.0  1.3   0:01.56 nautilus                                                                                           
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 23900  12m 7940 S  0.0  0.6   0:00.40 nm-applet                                                                                          
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.66 avant-window-na                                                                                    
 7881 the8thst  20   0 26764  11m 7344 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 9398 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9403 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9404 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:09:57 up 1 min,  1 user,  load average: 1.35, 0.56, 0.20
Tasks: 116 total,   2 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.6%us,  8.0%sy,  0.0%ni, 60.2%id,  3.4%wa,  0.8%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   456796k used,  1606472k free,    13668k buffers
Swap:  4000176k total,        0k used,  4000176k free,   150828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 8807 the8thst  20   0  132m  40m  20m S 15.2  2.0   0:03.09 firefox                                                                                            
 6292 root      20   0  386m  20m 8396 R 13.6  1.0   0:05.80 Xorg                                                                                               
  969 root      20   0  1180  260  192 S  1.2  0.0   0:00.66 busybox                                                                                            
 7498 the8thst  20   0 21700  13m 5964 S  1.2  0.7   0:01.64 compiz.real                                                                                        
 5752 messageb  20   0  2948 1288  732 S  0.4  0.1   0:00.24 dbus-daemon                                                                                        
 5919 haldaemo  20   0  6432 4376 3584 S  0.4  0.2   0:00.44 hald                                                                                               
 7293 the8thst  20   0 47456  16m 8432 S  0.4  0.8   0:00.86 gnome-settings-                                                                                    
 7637 the8thst  20   0 21172 3092 1728 S  0.4  0.1   0:00.06 gnome-screensav                                                                                    
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 S  0.0  0.0   0:00.14 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.0  0.0   0:00.14 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.02 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2420 1140  884 R  0.0  0.1   0:00.14 top                                                                                                
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5792 4648 S  0.0  0.3   0:00.20 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  2904 1120  592 S  0.0  0.1   0:00.10 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7732 4772 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2160 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7740 the8thst  20   0 17056 8812 7168 S  0.0  0.4   0:00.26 gtk-window-deco                                                                                    
 7809 the8thst  20   0 44596  20m  12m S  0.0  1.0   0:01.18 gnome-panel                                                                                        
 7824 the8thst  20   0 68264  25m  13m S  0.0  1.3   0:01.56 nautilus                                                                                           
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 23900  12m 7940 S  0.0  0.6   0:00.40 nm-applet                                                                                          
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.66 avant-window-na                                                                                    
 7881 the8thst  20   0 26764  11m 7344 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 9615 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9620 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9621 root      20   0   168   40   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:10:02 up 1 min,  1 user,  load average: 1.25, 0.55, 0.20
Tasks: 116 total,   3 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.2%us,  7.8%sy,  0.0%ni, 74.3%id,  1.4%wa,  0.4%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   461404k used,  1601864k free,    13684k buffers
Swap:  4000176k total,        0k used,  4000176k free,   151508k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7809 the8thst  20   0 48624  24m  12m R  9.6  1.2   0:01.66 gnome-panel                                                                                        
 6292 root      20   0  386m  20m 8472 R  4.0  1.0   0:06.00 Xorg                                                                                               
 8807 the8thst  20   0  132m  40m  20m S  3.6  2.0   0:03.27 firefox                                                                                            
  969 root      20   0  1180  260  192 S  0.8  0.0   0:00.70 busybox                                                                                            
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.16 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.16 busybox                                                                                            
 6534 root      20   0  2420 1140  884 R  0.4  0.1   0:00.16 top                                                                                                
 7498 the8thst  20   0 21700  13m 5964 S  0.4  0.7   0:01.66 compiz.real                                                                                        
 7637 the8thst  20   0 21172 3092 1728 S  0.4  0.1   0:00.08 gnome-screensav                                                                                    
 7854 the8thst  20   0 23900  12m 7960 S  0.4  0.6   0:00.42 nm-applet                                                                                          
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.0  0.1   0:00.24 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.02 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.44 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5792 4648 S  0.0  0.3   0:00.20 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  2904 1120  592 S  0.0  0.1   0:00.10 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.18 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7732 4772 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7293 the8thst  20   0 47456  16m 8432 S  0.0  0.8   0:00.86 gnome-settings-                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2160 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7740 the8thst  20   0 17056 8816 7172 S  0.0  0.4   0:00.26 gtk-window-deco                                                                                    
 7824 the8thst  20   0 68264  25m  13m S  0.0  1.3   0:01.56 nautilus                                                                                           
 7835 the8thst  20   0 32456 3456 2672 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.66 avant-window-na                                                                                    
 7881 the8thst  20   0 26764  11m 7364 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 9838 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9839 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
 9841 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:10:07 up 1 min,  1 user,  load average: 1.22, 0.56, 0.20
Tasks: 117 total,   5 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s): 37.8%us,  9.8%sy,  0.0%ni, 41.4%id, 10.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   465588k used,  1597680k free,    13804k buffers
Swap:  4000176k total,        0k used,  4000176k free,   153440k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7824 the8thst  20   0 72104  30m  14m R 20.0  1.5   0:02.56 nautilus                                                                                           
 6292 root      20   0  390m  21m 8568 R 13.2  1.1   0:06.66 Xorg                                                                                               
 7809 the8thst  20   0 45196  21m  13m S  2.8  1.1   0:01.80 gnome-panel                                                                                        
 7857 the8thst  20   0 25840  12m 8668 S  2.4  0.6   0:00.78 avant-window-na                                                                                    
 8807 the8thst  20   0  132m  40m  20m S  1.8  2.0   0:03.36 firefox                                                                                            
 7498 the8thst  20   0 21700  13m 5964 S  1.2  0.7   0:01.72 compiz.real                                                                                        
  969 root      20   0  1180  264  192 S  0.8  0.0   0:00.74 busybox                                                                                            
 7740 the8thst  20   0 17056 8828 7172 S  0.8  0.4   0:00.30 gtk-window-deco                                                                                    
 7070 the8thst  20   0  3032 1140  592 S  0.4  0.1   0:00.12 dbus-daemon                                                                                        
 7293 the8thst  20   0 47456  16m 8432 S  0.4  0.8   0:00.88 gnome-settings-                                                                                    
 7637 the8thst  20   0 21172 3092 1728 S  0.4  0.1   0:00.10 gnome-screensav                                                                                    
 7091 the8thst  20   0 28836 4044 3032 S  0.2  0.2   0:00.19 pulseaudio                                                                                         
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
  964 root      20   0  1180  220  164 R  0.0  0.0   0:00.16 busybox                                                                                            
  966 root      20   0  1180  220  164 R  0.0  0.0   0:00.16 busybox                                                                                            
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.0  0.1   0:00.24 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.02 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.44 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2420 1140  884 R  0.0  0.1   0:00.16 top                                                                                                
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5796 4648 S  0.0  0.3   0:00.20 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7792 4776 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2168 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7835 the8thst  20   0 32456 3468 2684 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 23900  12m 7972 S  0.0  0.6   0:00.42 nm-applet                                                                                          
 7881 the8thst  20   0 26764  11m 7368 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 9914 the8thst  20   0 14044 2660 2236 S  0.0  0.1   0:00.00 gvfsd-computer                                                                                     
10061 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
10066 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
10067 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:10:12 up 1 min,  1 user,  load average: 1.13, 0.55, 0.20
Tasks: 117 total,   2 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.5%us,  7.6%sy,  0.0%ni, 75.1%id,  4.8%wa,  2.0%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   466680k used,  1596588k free,    13884k buffers
Swap:  4000176k total,        0k used,  4000176k free,   154108k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7824 the8thst  20   0 72368  30m  14m R  8.5  1.5   0:02.99 nautilus                                                                                           
 6292 root      20   0  390m  21m 8568 S  3.2  1.1   0:06.82 Xorg                                                                                               
  969 root      20   0  1180  264  192 S  1.2  0.0   0:00.80 busybox                                                                                            
    4 root      15  -5     0    0    0 S  0.4  0.0   0:00.08 ksoftirqd/0                                                                                        
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.18 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.18 busybox                                                                                            
 7498 the8thst  20   0 21700  13m 5964 S  0.4  0.7   0:01.74 compiz.real                                                                                        
 8807 the8thst  20   0  132m  40m  20m S  0.2  2.0   0:03.37 firefox                                                                                            
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1340 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                              
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.0  0.1   0:00.24 dbus-daemon                                                                                        
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.02 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.44 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6534 root      20   0  2420 1140  884 R  0.0  0.1   0:00.16 top                                                                                                
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5796 4648 S  0.0  0.3   0:00.20 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  3032 1140  592 S  0.0  0.1   0:00.12 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.19 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7792 4776 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7293 the8thst  20   0 47456  16m 8432 S  0.0  0.8   0:00.88 gnome-settings-                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2168 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7637 the8thst  20   0 21172 3092 1728 S  0.0  0.1   0:00.10 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7740 the8thst  20   0 17056 8828 7172 S  0.0  0.4   0:00.30 gtk-window-deco                                                                                    
 7809 the8thst  20   0 45196  21m  13m S  0.0  1.1   0:01.80 gnome-panel                                                                                        
 7835 the8thst  20   0 32456 3468 2684 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7854 the8thst  20   0 23900  12m 7972 S  0.0  0.6   0:00.42 nm-applet                                                                                          
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.78 avant-window-na                                                                                    
 7881 the8thst  20   0 26764  11m 7368 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 9914 the8thst  20   0 14044 2660 2236 S  0.0  0.1   0:00.00 gvfsd-computer                                                                                     
10282 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              
10285 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
10288 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep                                                                                              


top - 22:10:17 up 1 min,  1 user,  load average: 1.04, 0.54, 0.20
Tasks: 117 total,   2 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.9%us,  6.4%sy,  0.0%ni, 77.9%id,  2.6%wa,  1.2%hi,  0.0%si,  0.0%st
Mem:   2063268k total,   468276k used,  1594992k free,    13904k buffers
Swap:  4000176k total,        0k used,  4000176k free,   154684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 7824 the8thst  20   0 72716  30m  14m S  6.0  1.5   0:03.29 nautilus                                                                                           
 6292 root      20   0  391m  21m 8568 R  2.8  1.1   0:06.96 Xorg                                                                                               
 8807 the8thst  20   0  132m  40m  20m S  2.0  2.0   0:03.47 firefox                                                                                            
  969 root      20   0  1180  264  192 S  1.2  0.0   0:00.86 busybox                                                                                            
 6534 root      20   0  2420 1140  884 R  0.8  0.1   0:00.20 top                                                                                                
  964 root      20   0  1180  220  164 S  0.4  0.0   0:00.20 busybox                                                                                            
  966 root      20   0  1180  220  164 S  0.4  0.0   0:00.20 busybox                                                                                            
 1340 root      15  -5     0    0    0 S  0.4  0.0   0:00.02 ata/0                                                                                              
 5752 messageb  20   0  2948 1288  732 S  0.4  0.1   0:00.26 dbus-daemon                                                                                        
 7498 the8thst  20   0 21700  13m 5964 S  0.4  0.7   0:01.76 compiz.real                                                                                        
 7740 the8thst  20   0 17056 8828 7172 S  0.4  0.4   0:00.32 gtk-window-deco                                                                                    
 7854 the8thst  20   0 23900  12m 7972 S  0.4  0.6   0:00.44 nm-applet                                                                                          
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.36 init                                                                                               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0                                                                                        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                                           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                       
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                             
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                            
  188 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  189 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                            
  190 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                            
  232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                              
 1266 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                      
 1269 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                              
 1310 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                           
 1344 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                            
 1764 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                          
 1765 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                          
 1766 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                          
 1767 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                          
 1777 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                        
 2154 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_4                                                                                          
 2156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                          
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 2801 root      16  -4  2528 1020  400 S  0.0  0.0   0:00.26 udevd                                                                                              
 3043 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945/0                                                                                          
 3087 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 iwl3945                                                                                            
 3246 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                              
 3299 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                          
 4909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                          
 5336 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5337 root      20   0  1780  540  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5338 root      20   0  1844  588  464 S  0.0  0.0   0:00.00 rc                                                                                                 
 5346 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5348 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5349 root      20   0  1780  536  468 S  0.0  0.0   0:00.00 getty                                                                                              
 5533 root      20   0  2308 1220  536 S  0.0  0.1   0:00.00 acpid                                                                                              
 5578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                        
 5659 syslog    20   0  2012  672  536 S  0.0  0.0   0:00.02 syslogd                                                                                            
 5715 root      20   0  1940  544  448 S  0.0  0.0   0:00.06 dd                                                                                                 
 5720 klog      20   0  3628 2480  444 S  0.0  0.1   0:00.14 klogd                                                                                              
 5780 avahi     20   0  2888 1448 1208 S  0.0  0.1   0:00.02 avahi-daemon                                                                                       
 5781 avahi     20   0  2888  500  300 S  0.0  0.0   0:00.00 avahi-daemon                                                                                       
 5837 root      20   0  6408 2184 1572 S  0.0  0.1   0:00.00 cupsd                                                                                              
 5919 haldaemo  20   0  6432 4376 3584 S  0.0  0.2   0:00.44 hald                                                                                               
 5922 root      20   0 16388 2564 1784 S  0.0  0.1   0:00.02 console-kit-dae                                                                                    
 5988 root      20   0  3364 1120  932 S  0.0  0.1   0:00.02 hald-runner                                                                                        
 6023 root      20   0  3436 1060  908 S  0.0  0.1   0:00.00 hald-addon-inpu                                                                                    
 6039 root      20   0  3448 1036  892 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                    
 6041 haldaemo  20   0  2296  900  764 S  0.0  0.0   0:00.00 hald-addon-acpi                                                                                    
 6060 root      20   0  3440 1064  912 S  0.0  0.1   0:00.02 hald-addon-stor                                                                                    
 6106 root      20   0  3488 1548 1324 S  0.0  0.1   0:00.00 bluetoothd                                                                                         
 6114 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                          
 6116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                          
 6147 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                           
 6179 root      20   0 14632 2584 2148 S  0.0  0.1   0:00.06 NetworkManager                                                                                     
 6183 root      20   0  4244 1880 1580 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                     
 6186 root      20   0  6768 2972 2460 S  0.0  0.1   0:00.02 nm-system-setti                                                                                    
 6285 root      20   0 14240 1760 1032 S  0.0  0.1   0:00.00 gdm                                                                                                
 6288 root      20   0 14740 3192 2276 S  0.0  0.2   0:00.02 gdm                                                                                                
 6362 root      20   0  4336 1152  912 S  0.0  0.1   0:00.00 system-tools-ba                                                                                    
 6406 daemon    20   0  2068  456  324 S  0.0  0.0   0:00.00 atd                                                                                                
 6434 root      20   0  3412 1024  812 S  0.0  0.0   0:00.00 cron                                                                                               
 6529 root      20   0  1844  556  448 S  0.0  0.0   0:00.00 S99rc.local                                                                                        
 6533 root      20   0  1844  492  432 S  0.0  0.0   0:00.00 rc.local                                                                                           
 6561 root      20   0  2252  948  820 S  0.0  0.0   0:00.00 dhclient                                                                                           
 6825 the8thst  20   0 24856 5796 4648 S  0.0  0.3   0:00.20 x-session-manag                                                                                    
 7066 the8thst  20   0  4740  596  284 S  0.0  0.0   0:00.00 ssh-agent                                                                                          
 7069 the8thst  20   0  3124  676  456 S  0.0  0.0   0:00.00 dbus-launch                                                                                        
 7070 the8thst  20   0  3032 1140  592 S  0.0  0.1   0:00.12 dbus-daemon                                                                                        
 7091 the8thst  20   0 28836 4044 3032 S  0.0  0.2   0:00.19 pulseaudio                                                                                         
 7109 the8thst  20   0  7528 2548 2080 S  0.0  0.1   0:00.00 gconf-helper                                                                                       
 7113 the8thst  20   0  7792 4776 2188 S  0.0  0.2   0:00.64 gconfd-2                                                                                           
 7170 the8thst  20   0 17796 6392 4648 S  0.0  0.3   0:00.22 seahorse-agent                                                                                     
 7253 the8thst  20   0 13916 3660 2992 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                    
 7285 the8thst  20   0 14684 2000 1568 S  0.0  0.1   0:00.00 gnome-keyring-d                                                                                    
 7293 the8thst  20   0 47456  16m 8432 S  0.0  0.8   0:00.88 gnome-settings-                                                                                    
 7294 the8thst  20   0  1844  552  452 S  0.0  0.0   0:00.00 compiz                                                                                             
 7380 the8thst  20   0  5556 2168 1824 S  0.0  0.1   0:00.02 gvfsd                                                                                              
 7404 the8thst  20   0 29196 2048 1620 S  0.0  0.1   0:00.00 gvfs-fuse-daemo                                                                                    
 7637 the8thst  20   0 21172 3092 1728 S  0.0  0.1   0:00.10 gnome-screensav                                                                                    
 7736 the8thst  20   0  1844  488  424 S  0.0  0.0   0:00.00 sh                                                                                                 
 7737 the8thst  20   0  1844  520  440 S  0.0  0.0   0:00.00 compiz-decorato                                                                                    
 7809 the8thst  20   0 45196  21m  13m S  0.0  1.1   0:01.80 gnome-panel                                                                                        
 7835 the8thst  20   0 32456 3468 2684 S  0.0  0.2   0:00.20 bonobo-activati                                                                                    
 7857 the8thst  20   0 25840  12m 8668 S  0.0  0.6   0:00.78 avant-window-na                                                                                    
 7881 the8thst  20   0 26764  11m 7368 S  0.0  0.6   0:00.36 gnome-power-man                                                                                    
 7891 the8thst  20   0 26128  12m 8748 S  0.0  0.6   0:00.40 awn-applet-acti                                                                                    
 8044 the8thst  20   0  5852 2656 2012 S  0.0  0.1   0:00.00 gvfs-hal-volume                                                                                    
 8048 the8thst  20   0  9252 3516 2916 S  0.0  0.2   0:00.02 gnome-vfs-daemo                                                                                    
 8057 the8thst  20   0  5704 2228 1596 S  0.0  0.1   0:00.00 gvfs-gphoto2-vo                                                                                    
 8112 the8thst  20   0 57380  11m 7584 S  0.0  0.6   0:00.26 awn-applet-acti                                                                                    
 8125 the8thst  20   0 37680  22m  11m S  0.0  1.1   0:00.76 python                                                                                             
 8128 the8thst  20   0 44452  15m  10m S  0.0  0.8   0:00.30 mixer_applet2                                                                                      
 8160 the8thst  20   0  5556 2224 1892 S  0.0  0.1   0:00.00 gvfsd-burn                                                                                         
 8184 the8thst  20   0 13996 2656 2252 S  0.0  0.1   0:00.02 gvfsd-trash                                                                                        
 9914 the8thst  20   0 14044 2660 2236 S  0.0  0.1   0:00.00 gvfsd-computer                                                                                     
10510 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
10511 root      20   0   168   36   20 S  0.0  0.0   0:00.00 sleep                                                                                              
10514 root      20   0   168   32   20 S  0.0  0.0   0:00.00 sleep

---

### Post by the8thstar on 2008-11-15
Bump

---

### Post by thierrybo on 2008-11-25
Hi,

did you tried to boot without no option checked for Session (except Gnome Window manager) , disable Compiz, AWN, ... to see if you problem is solved, then check one by one until you find the "wrong" program?

---

