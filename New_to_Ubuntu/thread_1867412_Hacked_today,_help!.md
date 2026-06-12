---
title: "Hacked today, help!"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-22
Hey guys, so today I check my hotmail and I see 60 new messages...all of them are "failed to send messages" and it looks like someone or something gained access to my account and was able to send ~150 emails saying stuff like "HEY! check this site out etc" but 60 failed because they were old contacts.

Anyway, for the past 2-3 weeks I have been using my Ubuntu partition exclusively so have no idea how this happened...I am very security conscious and was using a randomly generated password, although the same one for months now. I have visited several shady websites this week but this was on 11.04 and within Firefox v7 so I thought I was immune :(

I changed the password to the account, any other tips on what should I do? Should I contact hotmail?

I don't run an antivirus, but below is a complete list of all the process currently running on my machine, does anyone notice anything out of the ordinary? Please let me know!


```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 18:06 ?        00:00:00 /sbin/init
root         2     0  0 18:06 ?        00:00:00 [kthreadd]
root         3     2  0 18:06 ?        00:00:00 [ksoftirqd/0]
root         6     2  0 18:06 ?        00:00:00 [migration/0]
root         7     2  0 18:06 ?        00:00:00 [migration/1]
root         9     2  0 18:06 ?        00:00:00 [ksoftirqd/1]
root        11     2  0 18:06 ?        00:00:00 [migration/2]
root        13     2  0 18:06 ?        00:00:00 [ksoftirqd/2]
root        14     2  0 18:06 ?        00:00:00 [migration/3]
root        16     2  0 18:06 ?        00:00:00 [ksoftirqd/3]
root        17     2  0 18:06 ?        00:00:00 [cpuset]
root        18     2  0 18:06 ?        00:00:00 [khelper]
root        19     2  0 18:06 ?        00:00:00 [netns]
root        21     2  0 18:06 ?        00:00:00 [sync_supers]
root        22     2  0 18:06 ?        00:00:00 [bdi-default]
root        23     2  0 18:06 ?        00:00:00 [kintegrityd]
root        24     2  0 18:06 ?        00:00:00 [kblockd]
root        25     2  0 18:06 ?        00:00:00 [kacpid]
root        26     2  0 18:06 ?        00:00:00 [kacpi_notify]
root        27     2  0 18:06 ?        00:00:00 [kacpi_hotplug]
root        28     2  0 18:06 ?        00:00:00 [ata_sff]
root        29     2  0 18:06 ?        00:00:00 [khubd]
root        30     2  0 18:06 ?        00:00:00 [md]
root        32     2  0 18:06 ?        00:00:00 [khungtaskd]
root        33     2  0 18:06 ?        00:00:00 [kswapd0]
root        34     2  0 18:06 ?        00:00:00 [ksmd]
root        35     2  0 18:06 ?        00:00:00 [fsnotify_mark]
root        36     2  0 18:06 ?        00:00:00 [aio]
root        37     2  0 18:06 ?        00:00:00 [ecryptfs-kthrea]
root        38     2  0 18:06 ?        00:00:00 [crypto]
root        42     2  0 18:06 ?        00:00:00 [kthrotld]
root        46     2  0 18:06 ?        00:00:00 [kmpathd]
root        47     2  0 18:06 ?        00:00:00 [kmpath_handlerd]
root        48     2  0 18:06 ?        00:00:00 [kondemand]
root        49     2  0 18:06 ?        00:00:00 [kconservative]
root       213     2  0 18:06 ?        00:00:00 [scsi_eh_0]
root       257     2  0 18:06 ?        00:00:00 [scsi_eh_1]
root       261     2  0 18:06 ?        00:00:00 [scsi_eh_2]
root       262     2  0 18:06 ?        00:00:00 [scsi_eh_3]
root       263     2  0 18:06 ?        00:00:00 [scsi_eh_4]
root       264     2  0 18:06 ?        00:00:00 [scsi_eh_5]
root       265     2  0 18:06 ?        00:00:00 [scsi_eh_6]
root       266     2  0 18:06 ?        00:00:00 [scsi_eh_7]
root       268     2  0 18:06 ?        00:00:00 [kworker/u:4]
root       270     2  0 18:06 ?        00:00:00 [kworker/u:6]
root       308     2  0 18:06 ?        00:00:00 [jbd2/sdb5-8]
root       309     2  0 18:06 ?        00:00:00 [ext4-dio-unwrit]
root       362     1  0 18:06 ?        00:00:00 upstart-udev-bridge --daemon
root       386     1  0 18:06 ?        00:00:00 udevd --daemon
root       505   386  0 18:06 ?        00:00:00 udevd --daemon
root       506   386  0 18:06 ?        00:00:00 udevd --daemon
root       682     1  0 18:06 ?        00:00:00 upstart-socket-bridge --daemon
root       684     2  0 18:06 ?        00:00:00 [kworker/3:2]
root       691     2  0 18:06 ?        00:00:00 [kpsmoused]
root       746     2  0 18:06 ?        00:00:00 [rc0]
root       834     1  0 18:06 ?        00:00:00 /sbin/mount.ntfs-3g /dev/sdc1 /media/Damir -o rw,locale=en_US.utf8
root       843     1  0 18:06 ?        00:00:07 /sbin/mount.ntfs-3g /dev/sdb1 /media/Downloads -o rw,locale=en_US.utf8
syslog     857     1  0 18:06 ?        00:00:00 rsyslogd -c4
102        865     1  0 18:06 ?        00:00:00 dbus-daemon --system --fork --activation=upstart
avahi      874     1  0 18:06 ?        00:00:00 avahi-daemon: running [Damir-Ubuntu.local]
avahi      875   874  0 18:06 ?        00:00:00 avahi-daemon: chroot helper
root       879     1  0 18:06 ?        00:00:00 NetworkManager
root       881     1  0 18:06 ?        00:00:00 /usr/sbin/modem-manager
root       884     1  0 18:06 ?        00:00:00 /usr/lib/policykit-1/polkitd
root       900     1  0 18:06 ?        00:00:00 /sbin/wpa_supplicant -u -s
root       938     1  0 18:06 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       944     1  0 18:06 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       951     1  0 18:06 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       952     1  0 18:06 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       954     1  0 18:06 tty6     00:00:00 /sbin/getty -8 38400 tty6
root       957     1  0 18:06 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       963     1  0 18:06 ?        00:00:00 /usr/sbin/irqbalance
daemon     971     1  0 18:06 ?        00:00:00 atd
root       972     1  0 18:06 ?        00:00:00 cron
nobody    1031     1  0 18:06 ?        00:00:53 /usr/sbin/g15daemon
root      1052     1  0 18:06 ?        00:00:00 gdm-binary
root      1056     1  0 18:06 ?        00:00:00 /usr/sbin/console-kit-daemon --no-daemon
root      1128     1  0 18:06 ?        00:00:00 /usr/sbin/cupsd -F
root      1131  1052  0 18:06 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1142  1131  4 18:06 tty7     00:09:27 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-KHSUBY/database -nolisten tcp vt7
root      1287     2  0 18:06 ?        00:00:00 [flush-8:16]
root      1371     1  0 18:06 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1399  1131  0 18:06 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
rtkit     1403     1  0 18:06 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
root      1409     1  0 18:06 ?        00:00:00 /usr/lib/upower/upowerd
damir     1513     1  0 18:10 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login
damir     1532  1399  0 18:10 ?        00:00:00 gnome-session --session=ubuntu
damir     1566  1532  0 18:10 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
damir     1569     1  0 18:10 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
damir     1570     1  0 18:10 ?        00:00:04 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
damir     1575     1  0 18:10 ?        00:00:02 /usr/lib/libgconf2-4/gconfd-2
damir     1587     1  0 18:10 ?        00:00:03 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
damir     1590     1  0 18:10 ?        00:00:00 /usr/lib/gvfs/gvfsd
damir     1595     1  0 18:10 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/damir/.gvfs
damir     1600  1532  1 18:10 ?        00:03:26 compiz
damir     1602     1  0 18:10 ?        00:01:33 /usr/bin/pulseaudio --start --log-target=syslog
damir     1604  1532  0 18:10 ?        00:00:09 nautilus
damir     1606  1532  0 18:10 ?        00:00:00 gnome-power-manager
damir     1608  1532  0 18:10 ?        00:00:00 zeitgeist-datahub
damir     1609  1532  0 18:10 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
damir     1615  1532  0 18:10 ?        00:00:00 nm-applet --sm-disable
damir     1616  1532  0 18:10 ?        00:00:03 /usr/bin/python /usr/share/my-weather-indicator/my-weather-indicator.py
damir     1618     1  0 18:10 ?        00:00:00 /usr/bin/python /usr/bin/zeitgeist-daemon
damir     1620  1532  0 18:10 ?        00:00:17 /usr/bin/python /usr/bin/indicator-sysmonitor
damir     1629  1602  0 18:10 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
damir     1638     1  0 18:10 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1641     1  0 18:10 ?        00:00:00 /usr/lib/udisks/udisks-daemon
root      1642  1641  0 18:10 ?        00:00:00 udisks-daemon: polling /dev/sr0
damir     1649  1618  0 18:10 ?        00:00:00 /bin/cat
damir     1651  1618  0 18:10 ?        00:00:00 [zeitgeist-datah] <defunct>
damir     1655     1  0 18:10 ?        00:00:00 /usr/lib/notify-osd/notify-osd
damir     1660     1  0 18:10 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
damir     1698     1  0 18:10 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
damir     1700     1  0 18:10 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
damir     1705     1  0 18:10 ?        00:00:00 /usr/lib/d-conf/dconf-service
damir     1714  1600  0 18:10 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
damir     1715  1714  0 18:10 ?        00:00:02 /usr/bin/unity-window-decorator
damir     1718     1  0 18:10 ?        00:00:13 /usr/lib/unity/unity-panel-service
damir     1729     1  0 18:10 ?        00:00:00 /usr/lib/bamf/bamfdaemon
damir     1731     1  0 18:10 ?        00:00:00 /usr/lib/indicator-datetime/indicator-datetime-service
damir     1733     1  0 18:10 ?        00:00:01 /usr/lib/indicator-application/indicator-application-service
damir     1743     1  0 18:10 ?        00:00:00 /usr/lib/indicator-sound/indicator-sound-service
damir     1748     1  0 18:10 ?        00:00:00 /usr/lib/indicator-session/indicator-session-service
damir     1758     1  0 18:10 ?        00:00:00 /usr/lib/geoclue/geoclue-master
damir     1765     1  0 18:10 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.10 /org/gtk/gvfs/exec_spaw/1
damir     1768     1  0 18:10 ?        00:00:00 /usr/lib/evolution/e-calendar-factory
damir     1770     1  0 18:10 ?        00:00:00 /usr/bin/gnome-screensaver --no-daemon
damir     1786     1  0 18:10 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
damir     1792     1  0 18:10 ?        00:00:00 /usr/lib/evolution/e-addressbook-factory
damir     1866  1532  0 18:10 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
damir     2098     1  5 18:10 ?        00:12:27 /usr/lib/firefox-7.0.1/firefox
damir     2170  2098  3 18:10 ?        00:06:54 /usr/lib/firefox-7.0.1/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox-7.0.1/omni.jar 2098 true plugin
damir     2358  1532  0 18:11 ?        00:00:00 update-notifier
damir     3292     1  0 18:13 ?        00:00:00 /usr/lib/unity-place-applications/unity-applications-daemon
damir     3294     1  0 18:13 ?        00:00:00 /usr/lib/unity-place-files/unity-files-daemon
root      8933     2  0 21:02 ?        00:00:00 [kworker/2:2]
root     12580     2  0 21:10 ?        00:00:00 [kworker/1:2]
root     19751     2  0 21:28 ?        00:00:00 [kworker/0:2]
root     25778     2  0 21:42 ?        00:00:00 [kworker/3:1]
root     25807     2  0 21:42 ?        00:00:00 [kworker/2:1]
root     25850     2  0 21:42 ?        00:00:00 [kworker/1:0]
root     26005     2  0 21:43 ?        00:00:00 [kworker/0:1]
root     27827     2  0 21:47 ?        00:00:00 [kworker/3:0]
root     27870     2  0 21:47 ?        00:00:00 [kworker/2:0]
root     28067     2  0 21:48 ?        00:00:00 [kworker/0:0]
root     28152     2  0 21:48 ?        00:00:00 [kworker/1:1]
damir    29040  1600  0 21:50 ?        00:00:00 /bin/sh -c gnome-terminal
damir    29041 29040  2 21:50 ?        00:00:00 gnome-terminal
damir    29045 29041  0 21:50 ?        00:00:00 gnome-pty-helper
damir    29046 29041  1 21:50 pts/0    00:00:00 bash
damir    29156 29046  0 21:50 pts/0    00:00:00 ps -ef

```

---

### Post by critin on 2011-10-22
Hotmail has a reputation for being hacked.  Yes, you should contact them because they will think you are the one sending spam and will cancel you if they get complaints with your ip.  Read their forums and see what advice is given there.  Change your password often.

critin

---

### Post by LinuxFan999 on 2011-10-22
If you want to, you could switch to another e-mail service, like Google's GMail.

---

### Post by d4m1r on 2011-10-22
> **LinuxFan999 said:**
> If you want to, you could switch to another e-mail service, like Google's GMail.


I've had this email since 2008 and not a single issue until today....Does anyone know how these bots work? I think it's a bot because nobody is gonna sit there and copy/paste 200 emails, but at the same time I am worried about them stealing **personal emails** containing financial information etc. Come to think of it, someone could have just brute forced it as I don't think hotmail has a limit on the amount of failed logins...

In the [hotmail FAQ]("http://explore.live.com/windows-live-hotmail-hacked-account-faq"), the first link is "what to do if you got hacked" and it recommends:

1)create a strong password (done, randomly generated one)
2)make sure OS has latest updates (done)
3)never reply to emails asking for your password (duh)
4)don't sign in from public PCs or unsecured wireless connections (I never do)

The fact my friends got spammed, too bad for them (lol), but I am still dumbfounded as to how they even got access to my account...

---

### Post by dwasifar on 2011-10-22
> **d4m1r said:**
> The fact my friends got spammed, too bad for them (lol), but I am still dumbfounded as to how they even got access to my account...

Probably just a brute force bot attack on hotmail, trying passwords and accounts at random.  It happens.  You're lucky they didn't change the password and lock you out of the account completely once they had access.

---

### Post by rex_dante on 2011-10-22
[QUOTE=I have visited several shady websites this week but this was on 11.04 and within Firefox v7 so I thought I was immune :([/QUOTE]

as far as the SECURITY is concerned...
makeup your mind that even OBAMA isn't secured...;)

remember...there IS SOMEONE....who's ALWAYS keeping an eye on you...;)

just saying...'coz in SECURITY & EXPLOITING it...is ma field...:popcorn:

ALL u can do is...do WHATEVER u CAN...means...precautions like using VPNs,PROXIES etc.., watching unusual activities on your PC and APPS..

USEFUL plugins & extensions for FIREFOX-
"tor","no-script","adblock plus" & many more....google it ;)
and don't save PASSWORDS in BROWSER...;)


""and WATCH wat YOU doing""...........................


ADIOS...
dantehh......

---

### Post by rex_dante on 2011-10-22
> **dwasifar said:**
> Probably just a brute force bot attack on hotmail, trying passwords and accounts at random.  It happens.  You're lucky they didn't change the password and lock you out of the account completely once they had access.
absolutely....
:P

---

### Post by 3rdalbum on 2011-10-23
People often use the same password for everything. If you register a user account on a malicious website and put in your e-mail address, the site may very well try logging into your e-mail using the password you set.

I would advise that you have two or three different passwords for different security levels. Frivilous websites, like those for online games or Ubuntu Forums, should have Password 1. Your e-mail account should have Password 2. Your online banking and any other highly-trusted websites should have Password 3 - it's highly unlikely that any one Password 3 website would know enough about you to be able to find out the Password 3 websites you visit and your usernames for them.

These passwords should be as secure as you can make them while still being memorable, but Password 3 should be the most difficult-to-guess. If you can, use unpronouncable characters such as ! or # or {.

---

### Post by d4m1r on 2011-10-23
> **3rdalbum said:**
> People often use the same password for everything. If you register a user account on a malicious website and put in your e-mail address, the site may very well try logging into your e-mail using the password you set.

I would advise that you have two or three different passwords for different security levels. Frivilous websites, like those for online games or Ubuntu Forums, should have Password 1. Your e-mail account should have Password 2. Your online banking and any other highly-trusted websites should have Password 3 - it's highly unlikely that any one Password 3 website would know enough about you to be able to find out the Password 3 websites you visit and your usernames for them.

These passwords should be as secure as you can make them while still being memorable, but Password 3 should be the most difficult-to-guess. If you can, use unpronouncable characters such as ! or # or {.


Ah, yes thats probably it...I do use a 2 password system, 1 spam one, and the randomly generated one (which I used for email, banking, etc). I also had to change my banking stuff and I think other account on other sites also use that password but they are not important...

Anyway, thinking back, I may have used that pass for other non-essential sites so that is most likely where they got it from...which site and if it was hacked or a simple DB query, I guess I'll never know....

I hope they did not export/download all my emails to their local drive! :(

---

### Post by Redblade20XX on 2011-10-23
Ironically you'll be surprised how many times servers get hacked and no one knows about them. There is always alot of private information flowing around the internet. With every site you visit, you entrust them with your information and they don't tell you what has happened to it. :o

- Red

---

### Post by lisati on 2011-10-23
In addition to the above, you should be aware of "From:" and "Reply-to:" email addresses used in spam that have been spoofed/faked/forged. It's easy enough to do if you know how, and I'm not about to say here.

---

