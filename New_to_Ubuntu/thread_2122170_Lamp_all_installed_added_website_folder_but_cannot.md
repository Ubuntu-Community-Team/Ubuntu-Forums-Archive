---
title: "Lamp all installed added website folder but cannot access website localhost/web  ??"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by baker556 on 2013-03-04
So installed everything lamp etc and my database

Added my website folder to var/www/web

Myfolder containing all website related stuff is web, now when i point localhost/web in my browser it cannot find it? 

any ideas the website is a drupal website that i want to upgrade.

Heres a lamp tutorial i created along the way quick  [http://chrisbaker556.blogspot.com/p/lamp-install.html](http://chrisbaker556.blogspot.com/p/lamp-install.html)

-Chris

---

### Post by TheFu on 2013-03-04
var/www/web or /var/www/web?
What do the log files show?
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

Is apache running? Are you using apache?
Is apache configured to allow php?
Is the DB running and you have specified the credentials correctly?

I would expect these things to be mostly pre-configured during the install.

Checking the log files is the first step for any Linux troubleshooting.

---

### Post by baker556 on 2013-03-05
Thanks for the reply let me explain..

[COLOR=#000000]var/www/web or /var/www/web   - Yes this is where the website is stored in web and in that correct order of directorys

Checking the log files did not work in terminal within root/su using [/COLOR][COLOR=#63FF00][FONT=bitstream vera sans mono]$ sudo egrep -i &#8216;error|warning&#8217; /var/log/*log[/FONT][/COLOR][COLOR=#63FF00][FONT=bitstream vera sans mono]
[/FONT][/COLOR]Using Apache and is all working..

[IMG]http://2.bp.blogspot.com/-A3yTCWeMwKc/UTDvqWLRVJI/AAAAAAAAAB8/07pAP4Q-HeQ/s1600/Screenshot+from+2013-03-01+18:12:34.png[/IMG]


Apache is configure to allow php i think its allowed and confgured with mysql

Database all correct

okay i am going to look into this php to apache config file could you point me in the right direction

Thanks
-Chris

---

### Post by lisati on 2013-03-05
"It works" usually goes into **/var/www** by default, which is *not* necessarily the same as **var/www**.

Do you see your website when you browse to **localhost/web**?

---

### Post by baker556 on 2013-03-05
This is my php test page..

[IMG]http://3.bp.blogspot.com/-88UGf13bRrI/UTSxLczzD5I/AAAAAAAAAC0/dIWDZtvY0og/s640/Screenshot+from+2013-03-04+14:35:15.png[/IMG]

---

### Post by baker556 on 2013-03-05
Thanks for the reply lisati

I have copied the 'web' folder into /var/www/web

When i browse to localhost/web i get the following..

[h=1]Not Found[/h][COLOR=#000000][FONT=Times New Roman]The requested URL /web/ was not found on this server.[/FONT][/COLOR]
[HR][/HR][COLOR=#000000][FONT=Times New Roman]Apache/2.2.22 (Ubuntu) Server at localhost Port 80[/FONT][/COLOR]

---

### Post by baker556 on 2013-03-05
The /var/www/web folder i have used also has other file in their such as phpmyadmin index.htmk and testphp.php i think this is the correct directory

-Chris

---

### Post by baker556 on 2013-03-05
Actually sorry i get this message

I actually changed the folder name from web to icm so /var/www/icm

just pointed browser to icm to get this message

[h=1]Server error[/h][COLOR=#000000][FONT=Helvetica]The website encountered an error while retrieving **[http://localhost/icm/](http://localhost/icm/)**. It may be down for maintenance or configured incorrectly.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][h=2]Here are some suggestions:[/h]
[LIST]
[*][Reload]("http://localhost/icm/") this web page later.
[/LIST]
[/FONT][/COLOR]
[COLOR=#777777][FONT=Helvetica]HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfil the request.[/FONT][/COLOR]

---

### Post by baker556 on 2013-03-05
Anyone have any more ideas I'm pretty stuck..

---

### Post by TheFu on 2013-03-05
> **baker556 said:**
> Anyone have any more ideas I'm pretty stuck..

Which user is running apache and do your file and directory permissions allow that user the needed access?

Have you verified that Apache is configured to allow php in your /var/www/* area?  The config files are usually under /etc/apache*/ somewhere.

---

### Post by baker556 on 2013-03-05
Running root with access to it all!

---

### Post by baker556 on 2013-03-05
This is the reply on starting apache

root@chris:~# /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 11504) already running

---

### Post by baker556 on 2013-03-05
> **TheFu said:**
> Which user is running apache and do your file and directory permissions allow that user the needed access?

Have you verified that Apache is configured to allow php in your /var/www/* area?  The config files are usually under /etc/apache*/ somewhere.

I'm not too sure what part i need to change in the apache2.conf file?

---

### Post by TheFu on 2013-03-05
> **baker556 said:**
> Running root with access to it all!

Apache is NOT running as root. It starts up that way, then switched to a different account.  Check the process table using ```
ps -eaf
```
That other account needs access to your files.  Usually, it is easiest to ```
chown -R /var/www {whatever-that-other-account-is}
```

May I suggest some background reading?
* Linux file permissions - [https://www.linux.com/learn/tutorials/309527:understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527:understanding-linux-file-permissions)
* Linux process control - [http://linux.about.com/od/nwb_guide/a/gdenwb01t66.htm](http://linux.about.com/od/nwb_guide/a/gdenwb01t66.htm)
* Apache configuration - [https://httpd.apache.org/docs/2.4/configuring.html](https://httpd.apache.org/docs/2.4/configuring.html)

I cannot tell you what settings to change (you might need to add them), since the settings can be located in any of 20 different files.  The configuration files are under /etc/apache*/ somewhere.

Sorry, but I stopped using apache about 4 yrs ago and avoid running php (security concerns) at all.
This how-to might help: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp)
There are many comments which might be useful too.

I'll ask again, what do the log files show?  Apache log files usually are located here: /var/log/apache*/  There should be other an access and error log which should provide extremely useful information about any issues.

---

### Post by baker556 on 2013-03-06
Thanks for the reply

When [COLOR=#000000][FONT=Ubuntu Mono]ps -eaf

[/FONT][/COLOR]```
root         1     0  0 11:54 ?        00:00:00 /sbin/initroot         2     0  0 11:54 ?        00:00:00 [kthreadd]
root         3     2  0 11:54 ?        00:00:00 [ksoftirqd/0]
root         4     2  0 11:54 ?        00:00:00 [kworker/0:0]
root         6     2  0 11:54 ?        00:00:00 [migration/0]
root         7     2  0 11:54 ?        00:00:00 [watchdog/0]
root         8     2  0 11:54 ?        00:00:00 [migration/1]
root        10     2  0 11:54 ?        00:00:00 [ksoftirqd/1]
root        11     2  0 11:54 ?        00:00:00 [watchdog/1]
root        12     2  0 11:54 ?        00:00:00 [migration/2]
root        14     2  0 11:54 ?        00:00:00 [ksoftirqd/2]
root        15     2  0 11:54 ?        00:00:00 [watchdog/2]
root        16     2  0 11:54 ?        00:00:00 [migration/3]
root        18     2  0 11:54 ?        00:00:00 [ksoftirqd/3]
root        19     2  0 11:54 ?        00:00:00 [watchdog/3]
root        20     2  0 11:54 ?        00:00:00 [cpuset]
root        21     2  0 11:54 ?        00:00:00 [khelper]
root        22     2  0 11:54 ?        00:00:00 [kdevtmpfs]
root        23     2  0 11:54 ?        00:00:00 [netns]
root        25     2  0 11:54 ?        00:00:00 [sync_supers]
root        26     2  0 11:54 ?        00:00:00 [bdi-default]
root        27     2  0 11:54 ?        00:00:00 [kintegrityd]
root        28     2  0 11:54 ?        00:00:00 [kblockd]
root        29     2  0 11:54 ?        00:00:00 [ata_sff]
root        30     2  0 11:54 ?        00:00:00 [khubd]
root        31     2  0 11:54 ?        00:00:00 [md]
root        33     2  0 11:54 ?        00:00:00 [kworker/1:1]
root        34     2  0 11:54 ?        00:00:00 [kworker/2:1]
root        35     2  0 11:54 ?        00:00:00 [kworker/3:1]
root        36     2  0 11:54 ?        00:00:00 [khungtaskd]
root        37     2  0 11:54 ?        00:00:00 [kswapd0]
root        38     2  0 11:54 ?        00:00:00 [ksmd]
root        39     2  0 11:54 ?        00:00:00 [khugepaged]
root        40     2  0 11:54 ?        00:00:00 [fsnotify_mark]
root        41     2  0 11:54 ?        00:00:00 [ecryptfs-kthrea]
root        42     2  0 11:54 ?        00:00:00 [crypto]
root        51     2  0 11:54 ?        00:00:00 [kthrotld]
root        52     2  0 11:54 ?        00:00:00 [scsi_eh_0]
root        53     2  0 11:54 ?        00:00:00 [kworker/u:2]
root        54     2  0 11:54 ?        00:00:00 [binder]
root        73     2  0 11:54 ?        00:00:00 [deferwq]
root        74     2  0 11:54 ?        00:00:00 [charger_manager]
root        75     2  0 11:54 ?        00:00:00 [devfreq_wq]
root       256     2  0 11:54 ?        00:00:00 [scsi_eh_1]
root       262     2  0 11:54 ?        00:00:00 [scsi_eh_2]
root       264     2  0 11:54 ?        00:00:00 [scsi_eh_3]
root       265     2  0 11:54 ?        00:00:00 [scsi_eh_4]
root       266     2  0 11:54 ?        00:00:00 [scsi_eh_5]
root       267     2  0 11:54 ?        00:00:00 [scsi_eh_6]
root       274     2  0 11:54 ?        00:00:00 [kworker/u:5]
root       291     2  0 11:54 ?        00:00:00 [scsi_eh_7]
root       292     2  0 11:54 ?        00:00:00 [usb-storage]
root       296     2  0 11:54 ?        00:00:00 [kworker/1:2]
root       297     2  0 11:54 ?        00:00:00 [firewire]
root       303     2  0 11:54 ?        00:00:00 [kworker/3:2]
root       321     2  0 11:54 ?        00:00:00 [kworker/2:2]
root       325     2  0 11:54 ?        00:00:00 [jbd2/sdb1-8]
root       326     2  0 11:54 ?        00:00:00 [ext4-dio-unwrit]
root       344     2  0 11:54 ?        00:00:00 [flush-8:16]
root       414     1  0 11:54 ?        00:00:00 upstart-udev-bridge --daemon
root       416     1  0 11:54 ?        00:00:00 /sbin/udevd --daemon
root       497     2  0 11:54 ?        00:00:00 [hci0]
root       541   416  0 11:54 ?        00:00:00 /sbin/udevd --daemon
root       543   416  0 11:54 ?        00:00:00 /sbin/udevd --daemon
root       621     2  0 11:54 ?        00:00:00 [kpsmoused]
root       642     2  0 11:54 ?        00:00:00 [ttm_swap]
root       658     2  0 11:54 ?        00:00:00 [kworker/0:3]
root       678     2  0 11:54 ?        00:00:00 [kvm-irqfd-clean]
root       753     2  0 11:54 ?        00:00:00 [hd-audio0]
root       776     1  0 11:54 ?        00:00:00 upstart-socket-bridge --daemon
102        895     1  0 11:54 ?        00:00:00 dbus-daemon --system --fork
root       918     1  0 11:54 ?        00:00:00 /usr/sbin/modem-manager
root       921     1  0 11:54 ?        00:00:00 /usr/sbin/bluetoothd
syslog     925     1  0 11:54 ?        00:00:00 rsyslogd -c5
root       933     1  0 11:54 ?        00:00:00 NetworkManager
root       934     2  0 11:54 ?        00:00:00 [krfcommd]
avahi      937     1  0 11:54 ?        00:00:00 avahi-daemon: running [chris.loc
avahi      938   937  0 11:54 ?        00:00:00 avahi-daemon: chroot helper
root       968     1  0 11:54 ?        00:00:00 /usr/lib/policykit-1/polkitd --n
root       982     1  0 11:54 ?        00:00:00 /usr/sbin/cupsd -F
root      1032     1  0 11:54 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1039     1  0 11:54 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1055     1  0 11:54 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1057     1  0 11:54 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1066     1  0 11:54 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1070   933  0 11:54 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/li
root      1097     1  0 11:54 ?        00:00:00 acpid -c /etc/acpi/events -s /va
whoopsie  1108     1  0 11:54 ?        00:00:00 whoopsie
root      1123     1  0 11:54 ?        00:00:00 /usr/sbin/irqbalance
mysql     1132     1  0 11:54 ?        00:00:00 /usr/sbin/mysqld
root      1160     1  0 11:54 ?        00:00:00 lightdm
root      1166     1  0 11:54 ?        00:00:00 cron
daemon    1167     1  0 11:54 ?        00:00:00 atd
root      1178  1160  3 11:54 tty7     00:00:13 /usr/bin/X :0 -core -auth /var/r
root      1191     1  0 11:54 ?        00:00:00 /usr/sbin/apache2 -k start
root      1311     1  0 11:54 ?        00:00:00 /usr/lib/accountsservice/account
root      1391     1  0 11:54 ?        00:00:00 /usr/sbin/console-kit-daemon --n
root      1468     1  0 11:54 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1529     1  0 11:54 ?        00:00:00 /usr/lib/upower/upowerd
colord    1722     1  0 11:55 ?        00:00:00 /usr/lib/x86_64-linux-gnu/colord
root      1729  1160  0 11:55 ?        00:00:00 lightdm --session-child 12 21
nobody    1733   933  0 11:55 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --
rtkit     1886     1  0 11:55 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
www-data  2002  1191  0 11:55 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2003  1191  0 11:55 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2004  1191  0 11:55 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2005  1191  0 11:55 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2006  1191  0 11:55 ?        00:00:00 /usr/sbin/apache2 -k start
chris     2304     1  0 11:56 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
chris     2315  1729  0 11:56 ?        00:00:00 gnome-session --session=ubuntu
chris     2350  2315  0 11:56 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
chris     2353     1  0 11:56 ?        00:00:00 /usr/bin/dbus-launch --exit-with
chris     2354     1  0 11:56 ?        00:00:00 //bin/dbus-daemon --fork --print
chris     2356     1  0 11:56 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus
chris     2360  2356  0 11:56 ?        00:00:00 /bin/dbus-daemon --config-file=/
chris     2363     1  0 11:56 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-re
chris     2375  2315  0 11:56 ?        00:00:00 /usr/lib/gnome-settings-daemon/g
chris     2382     1  0 11:56 ?        00:00:00 /usr/lib/gvfs/gvfsd
chris     2386     1  0 11:56 ?        00:00:00 /usr/lib/gvfs//gvfsd-fuse -f /ru
chris     2395  2315  3 11:56 ?        00:00:08 compiz
chris     2401     1  0 11:56 ?        00:00:00 /usr/lib/dconf/dconf-service
chris     2403  2315  0 11:56 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
chris     2408  2315  0 11:56 ?        00:00:00 /usr/lib/gnome-settings-daemon/g
chris     2409  2315  0 11:56 ?        00:00:00 nm-applet
chris     2411  2315  0 11:56 ?        00:00:02 nautilus -n
chris     2414  2315  0 11:56 ?        00:00:00 bluetooth-applet
chris     2423     1  0 11:56 ?        00:00:00 /usr/lib/gvfs/gvfs-udisks2-volum
root      2428     1  0 11:56 ?        00:00:00 /usr/lib/udisks2/udisksd --no-de
chris     2438     1  0 11:56 ?        00:00:00 /usr/bin/pulseaudio --start --lo
chris     2456     1  0 11:56 ?        00:00:00 /usr/lib/x86_64-linux-gnu/gconf/
chris     2458     1  0 11:56 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
chris     2462     1  0 11:56 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-mo
root      2468  2428  0 11:56 ?        00:00:00 mount /media/floppy0
chris     2471  2438  0 11:56 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
chris     2473     1  0 11:56 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
chris     2480     1  0 11:56 ?        00:00:00 /usr/lib/bamf/bamfdaemon
chris     2485  2395  0 11:56 ?        00:00:00 /bin/sh -c /usr/bin/gtk-window-d
chris     2486  2485  0 11:56 ?        00:00:00 /usr/bin/gtk-window-decorator
chris     2494     1  0 11:56 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
chris     2498     1  0 11:56 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
chris     2503     1  0 11:56 ?        00:00:00 /usr/lib/unity/unity-panel-servi
chris     2505     1  0 11:56 ?        00:00:00 /usr/lib/indicator-appmenu/hud-s
chris     2515     1  0 11:56 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indica
chris     2518     1  0 11:56 ?        00:00:00 /usr/lib/indicator-session/indic
chris     2525     1  0 11:56 ?        00:00:00 /usr/lib/indicator-datetime/indi
chris     2526     1  0 11:56 ?        00:00:00 /usr/lib/indicator-printers/indi
chris     2533     1  0 11:56 ?        00:00:00 /usr/lib/indicator-sound/indicat
chris     2534     1  0 11:56 ?        00:00:00 /usr/lib/indicator-messages/indi
chris     2553     1  0 11:56 ?        00:00:00 /usr/lib/evolution/evolution-sou
chris     2564     1  0 11:56 ?        00:00:00 /usr/lib/gnome-online-accounts/g
chris     2572     1  0 11:56 ?        00:00:00 /usr/lib/geoclue/geoclue-master
chris     2585     1  0 11:56 ?        00:00:00 /usr/lib/ubuntu-geoip/ubuntu-geo
chris     2595  2315  0 11:56 ?        00:00:00 telepathy-indicator
chris     2601     1  0 11:56 ?        00:00:00 /usr/lib/telepathy/mission-contr
chris     2607     1  0 11:56 ?        00:00:00 /usr/bin/signon-ui
chris     2611  2315  0 11:56 ?        00:00:00 zeitgeist-datahub
chris     2612  2315  0 11:56 ?        00:00:00 gnome-screensaver
chris     2618     1  0 11:56 ?        00:00:00 /usr/bin/zeitgeist-daemon
chris     2626     1  0 11:56 ?        00:00:00 /usr/lib/zeitgeist/zeitgeist-fts
chris     2634  2626  0 11:56 ?        00:00:00 /bin/cat
chris     2647     1  0 11:57 ?        00:00:00 /usr/bin/python /usr/lib/ubuntuo
chris     2688     1  0 11:57 ?        00:00:00 /usr/lib/unity-lens-applications
chris     2690     1  0 11:57 ?        00:00:00 /usr/lib/unity-lens-files/unity-
chris     2692     1  0 11:57 ?        00:00:00 /usr/lib/gwibber/unity-gwibber-d
chris     2694     1  0 11:57 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-
chris     2696     1  0 11:57 ?        00:00:00 /usr/bin/python3 /usr/lib/unity-
chris     2698     1  0 11:57 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-
chris     2700     1  0 11:57 ?        00:00:00 /usr/bin/python /usr/lib/unity-l
chris     2768     1  0 11:57 ?        00:00:00 /usr/bin/python /usr/lib/unity-s
chris     2770     1  0 11:57 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-
chris     2772     1  0 11:57 ?        00:00:00 /usr/bin/python3 /usr/lib/unity-
chris     2804  2315  0 11:57 ?        00:00:00 update-notifier
root      2815     1  0 11:57 ?        00:00:00 /usr/bin/python /usr/lib/system-
chris     2819  2315  0 11:58 ?        00:00:00 /usr/lib/x86_64-linux-gnu/deja-d
chris     2824     1  5 11:59 ?        00:00:06 /opt/google/chrome/chrome       
chris     2832     1  0 11:59 ?        00:00:00 gnome-terminal
chris     2846  2832  0 11:59 ?        00:00:00 gnome-pty-helper
chris     2847  2832  0 11:59 pts/0    00:00:00 bash
chris     2898  2824  0 11:59 ?        00:00:00 /opt/google/chrome/chrome       
chris     2899  2824  0 11:59 ?        00:00:00 /opt/google/chrome/chrome-sandbo
chris     2900  2899  0 11:59 ?        00:00:00 /opt/google/chrome/chrome --type
chris     2904  2900  0 11:59 ?        00:00:00 /opt/google/chrome/nacl_helper_b
chris     2905  2900  0 11:59 ?        00:00:00 /opt/google/chrome/chrome --type
chris     2932  2905  0 11:59 ?        00:00:00 /opt/google/chrome/chrome --type
root      3038     2  0 11:59 ?        00:00:00 [kworker/2:0]
chris     3046  2905  1 11:59 ?        00:00:00 /opt/google/chrome/chrome --type
chris     3056  2905  3 11:59 ?        00:00:02 /opt/google/chrome/chrome --type
chris     3063  2905  0 11:59 ?        00:00:00 /opt/google/chrome/chrome --type
chris     3074  2905  1 11:59 ?        00:00:01 /opt/google/chrome/chrome --type
chris     3098  2905  0 11:59 ?        00:00:00 /opt/google/chrome/chrome --type
chris     3105  2905  3 11:59 ?        00:00:02 /opt/google/chrome/chrome --type
chris     3180  2905  2 12:00 ?        00:00:01 /opt/google/chrome/chrome --type
chris     3233  2847  0 12:01 pts/0    00:00:00 ps -eaf


```[COLOR=#000000][FONT=Ubuntu Mono]

Using
[/FONT][/COLOR][COLOR=#000000]
chown -R /var/www {whatever-that-other-account-is}
I'm gussing it would be www-data

So 


chown -R /var/www {www-data}

Thanks for the reading materials i did lamp and unix at uni with file permissions but not in true depth more make files.


Also created a group called www the tired changing the permission but no luck..


sudo chown root[COLOR=#666600]:[/COLOR]www [COLOR=#666600]/[/COLOR][COLOR=#000088]var[/COLOR][COLOR=#666600]/[/COLOR]www
sudo chmod [COLOR=#006666]2775[/COLOR] [COLOR=#666600]/[/COLOR][COLOR=#000088]var[/COLOR][COLOR=#666600]/[/COLOR]www


The install document is the one i followed i then created my own for future reference here

[http://chrisbaker556.blogspot.co.uk/p/lamp-install.html](http://chrisbaker556.blogspot.co.uk/p/lamp-install.html)

So its still not working although i guess its something to do with the user that has not changed the permission or the web file Drupal itself?



[/COLOR]

---

### Post by baker556 on 2013-03-06
All fixed well kinda..

Followed this guide

**Optional Publishing Method**

[FONT=Lato]Publishing can be kind of a pain because when you install Apache it makes the document root of the webserver /var/www that is owned by root. So this causes a problem. Here is one solution.[/FONT][FONT=inherit][TABLE]
[TR]
[TD="class: gutter"][/TD]
[TD="class: code"][FONT=inherit]sudo mkdir /srv/www[/FONT][FONT=inherit]sudo cp -r /var/www/* /srv/www/[/FONT][/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=Lato]then, open up your config file:[/FONT][FONT=inherit][TABLE]
[TR]
[TD="class: gutter"][/TD]
[TD="class: code"][FONT=inherit]sudo nano /etc/apache2/sites-available/default[/FONT][/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=Lato]And change your DocumentRoot. There will be a section that says:[/FONT][FONT=inherit][TABLE]
[TR]
[TD="class: gutter"][/TD]
[TD="class: code"][FONT=inherit]Change [/FONT][FONT=inherit]DocumentRoot /var/www[/FONT][FONT=inherit]to [/FONT][FONT=inherit]DocumentRoot /srv/www[/FONT][FONT=inherit]and [/FONT][FONT=inherit]<Directory /var/www>[/FONT][FONT=inherit]to[/FONT][FONT=inherit]<Directory /srv/www>[/FONT][/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=Lato]then restart your server:[/FONT][FONT=inherit][TABLE]
[TR]
[TD="class: gutter"][/TD]
[TD="class: code"][FONT=inherit]sudo etc/init.d/apache2 restart[/FONT][/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=Lato]I created a folder in my home directory called “web” and then created a symbolic link:[/FONT][FONT=inherit][TABLE]
[TR]
[TD="class: gutter"][/TD]
[TD="class: code"][FONT=inherit]sudo ln -s /srv/www/ /home/jeremy/web/[/FONT][/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=Lato]so I can work in a folder in my home directory ( I actually do most work in VIM ). Of course there’s a little permissions issue still, so run the following commands, but be sure to subsitute your user name.[/FONT][FONT=inherit][TABLE]
[TR]
[TD="class: gutter"][/TD]
[TD="class: code"][FONT=inherit]sudo usermod -g www-data jeremy[/FONT][FONT=inherit]sudo chown -R jeremy:www-data /srv/www[/FONT][FONT=inherit]sudo chmod -R 775 /srv/www/[/FONT][/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=Lato]Now I can create files or entire an entire website in my own folder ( /home/jeremy/web ) and view it thru localhost.

From this website [http://www.jeremymorgan.com/tutorials/linux/how-to-install-apache-php-and-mysql-on-ubuntu-12-dot-10-quantal-quetzal/](http://www.jeremymorgan.com/tutorials/linux/how-to-install-apache-php-and-mysql-on-ubuntu-12-dot-10-quantal-quetzal/)

Only problem now is linking the database with Drupal...[/FONT]

---

### Post by TheFu on 2013-03-06
Please try not to post non-relevant data. Most of the **ps -eaf** output wasn't needed.

> **baker556 said:**
>  chown -R /var/www {www-data}
This should be 
```
sudo chown -R www-data.www-data /var/www 
```

when commands don't work, please read the man page. **man chown**.

Why do you want a new group, www?
Apache is setup to work with www-data. Changing the group means you'll need to change all sorts of other things. 
I strongly recommend you stay with the defaults when you are struggling.

Where are the Drupal files located?  If they aren't under /var/www somewhere, then you need to tell apache and php where they are in the apache config files.

Certainly there is a drupal on Ubuntu how-to with step by step instructions that you can copy/paste.  Seaching for "drupal install ubuntu 12.04" found lots of results. [http://ubuntuserverguide.com/2012/08/how-to-install-drupal-7-on-ubuntu-server-12-04.html](http://ubuntuserverguide.com/2012/08/how-to-install-drupal-7-on-ubuntu-server-12-04.html) seems pretty straight forward, if it is correct.

---

### Post by TheFu on 2013-03-06
Putting files that need to be owned by www-data under your HOME is a bad idea. Trust me.
If you want an easy way to get to those files, use **cdpath**.  Avoid the temptation to use softlinks in this situation.  This can screw with all sorts of things.

Often, the simplistic solution is to add your account to the www-data group and set the g+rwxs on all folders under /var/www.  I think that was want the usermod did above, but you want www-data to be the owner, not your userid.  This is a security issue.

---

### Post by baker556 on 2013-03-06
Thanks for the info TheFu i understand its all a learning curve some of this to me.

I'm going to take them out of my directory well the softlinks anyway.

---

### Post by TheFu on 2013-03-06
No prob.  UNIX file permissions are deceptively complex with tremendous flexibility. Most people don't need to know much more than r, w, x, user, group, other, but when we setup servers, file permissions are the core of the security model.

Everyone here was new to this stuff at some point.
* google
* RTFM
* Ask for help.
I find that I learn things more deeply if I've struggled with the solution. To learn even more, teach the solution.

---

