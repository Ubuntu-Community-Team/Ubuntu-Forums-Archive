---
title: "[SOLVED] What/why are things running?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by anewguy on 2008-06-16
I switched to comcast.net for my broadband Saturday.  Since then, I see things running that I don't know why they are.  For example, I have found more than 1 instance of apache running, and as far as I know I never have done anything with apache.  There are a lot of processes that show of which I know nothing.  Is there a sticky or something somewhere that would explain what these processes are and if they should be running on my system?  I feel that perhaps someone has hacked my system, and that is why apache has shown up.  I don't need it as I only have 1 PC currently.

Thank you!

---

### Post by skymera on 2008-06-16
Where are you seeing all these processes running?

---

### Post by _sphinx_ on 2008-06-16
Have you uncheck the Apache from System->Preferences->Sessions

---

### Post by kpkeerthi on 2008-06-16
> **anewguy said:**
> I switched to comcast.net for my broadband Saturday.  Since then, I see things running that I don't know why they are.  For example, I have found more than 1 instance of apache running, and as far as I know I never have done anything with apache.  There are a lot of processes that show of which I know nothing.  Is there a sticky or something somewhere that would explain what these processes are and if they should be running on my system?  I feel that perhaps someone has hacked my system, and that is why apache has shown up.  I don't need it as I only have 1 PC currently.

Thank you!

If you are suspicious, type
```
netstat -antp
``` to check if any program is using your internet to connect to foreign IPs.

---

### Post by anewguy on 2008-06-16
I see the processes when I ps -e to see what all is running.  I now there are a lot of background processes that must run, but how can I check what I have to know if they are all valid?

Apache doesn't show under system/preferences/session.

Output of netstat -antp is:

dave@dave-desktop:~$ sudo netstat -antp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:10026         0.0.0.0:*               LISTEN      6073/clamsmtpd  
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5487/cupsd      
tcp        0      1 192.168.1.2:56291       69.147.76.15:80         FIN_WAIT1   -               
tcp        1      1 192.168.1.2:58371       209.170.117.153:80      LAST_ACK    -               
tcp        0      0 192.168.1.2:41651       66.135.218.117:80       ESTABLISHED 7203/firefox    
tcp        0      0 192.168.1.2:52614       216.113.185.197:80      ESTABLISHED 7203/firefox    
tcp        0      1 192.168.1.2:43916       69.147.76.15:80         FIN_WAIT1   -               
tcp        0      0 192.168.1.2:39233       216.113.183.159:80      ESTABLISHED 7203/firefox    
tcp        0      0 192.168.1.2:47654       66.135.215.44:80        ESTABLISHED 7203/firefox    
tcp        0      0 192.168.1.2:51262       63.215.124.52:80        ESTABLISHED 7203/firefox    
tcp        1      1 192.168.1.2:50633       212.58.226.20:80        LAST_ACK    -               
tcp6       0      0 :::80                   :::*                    LISTEN      6573/apache2    
dave@dave-desktop:~$ 



The output of a ps -e is as follows - please note this is from now, right after I rebooted the system.  I don't understand Apache being in there.  I have no idea why it shows two "sh"'s.  I'd like to know what the rest of the stuff is and if I need it running as well.  Why is winbindd running?  How do I turn off the bluetooth stuff?  I remember experimenting in 7.10 with a mac emulator - anyone know how I remove softmac?  What is seahorse agent?  == Well, you get the idea.  Where do I find this information and how do I remove these things from start up?


dave@dave-desktop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:03 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   42 ?        00:00:00 kblockd/0
   45 ?        00:00:00 kacpid
   46 ?        00:00:00 kacpi_notify
  108 ?        00:00:00 kseriod
  139 ?        00:00:00 pdflush
  140 ?        00:00:00 pdflush
  141 ?        00:00:00 kswapd0
  184 ?        00:00:00 aio/0
 1446 ?        00:00:00 ksuspend_usbd
 1455 ?        00:00:00 khubd
 1500 ?        00:00:00 ata/0
 1507 ?        00:00:00 ata_aux
 2235 ?        00:00:00 scsi_eh_0
 2239 ?        00:00:00 scsi_eh_1
 2985 ?        00:00:00 kjournald
 3203 ?        00:00:02 udevd
 3592 ?        00:00:00 kgameportd
 3644 ?        00:00:00 zd1211rw
 3687 ?        00:00:00 softmac
 5029 tty4     00:00:00 getty
 5030 tty5     00:00:00 getty
 5034 tty2     00:00:00 getty
 5035 tty3     00:00:00 getty
 5037 tty6     00:00:00 getty
 5205 ?        00:00:00 acpid
 5242 ?        00:00:00 kondemand/0
 5312 ?        00:00:00 syslogd
 5368 ?        00:00:00 dd
 5371 ?        00:00:00 klogd
 5393 ?        00:00:00 dbus-daemon
 5410 ?        00:00:00 NetworkManager
 5424 ?        00:00:00 NetworkManagerD
 5437 ?        00:00:00 system-tools-ba
 5457 ?        00:00:00 avahi-daemon
 5458 ?        00:00:00 avahi-daemon
 5487 ?        00:00:00 cupsd
 5731 ?        00:00:17 clamd
 5831 ?        00:00:00 freshclam
 6062 ?        00:00:00 clamav-milter
 6073 ?        00:00:00 clamsmtpd
 6119 ?        00:00:00 usbb2k_api
 6134 ?        00:00:00 winbindd
 6162 ?        00:00:00 winbindd
 6188 ?        00:00:00 dhcdbd
 6207 ?        00:00:01 hald
 6210 ?        00:00:00 console-kit-dae
 6272 ?        00:00:00 hald-runner
 6292 ?        00:00:00 hald-addon-acpi
 6301 ?        00:00:00 hald-addon-inpu
 6311 ?        00:00:00 hald-addon-stor
 6319 ?        00:00:00 hald-addon-stor
 6344 ?        00:00:00 hcid
 6359 ?        00:00:00 btaddconn
 6360 ?        00:00:00 btdelconn
 6378 ?        00:00:00 bluetoothd-serv
 6379 ?        00:00:00 bluetoothd-serv
 6389 ?        00:00:00 krfcommd
 6438 ?        00:00:00 gdm
 6446 ?        00:00:00 gdm
 6453 tty7     00:02:16 Xorg
 6463 ?        00:00:00 anacron
 6479 ?        00:00:00 atd
 6495 ?        00:00:00 cron
 6573 ?        00:00:18 apache2
 6647 tty1     00:00:00 getty
 6673 ?        00:00:00 apache2
 6675 ?        00:00:00 apache2
 6676 ?        00:00:00 apache2
 6677 ?        00:00:00 apache2
 6678 ?        00:00:00 apache2
 6682 ?        00:00:02 gconfd-2
 6684 ?        00:00:00 gnome-keyring-d
 6686 ?        00:00:00 gnome-session
 6742 ?        00:00:00 seahorse-agent
 6750 ?        00:00:00 dbus-daemon
 6751 ?        00:00:03 gnome-settings-
 6755 ?        00:00:00 pulseaudio
 6758 ?        00:00:00 gconf-helper
 6767 ?        00:00:01 gnome-screensav
 6772 ?        00:00:00 compiz
 6774 ?        00:00:10 gnome-panel
 6775 ?        00:00:03 nautilus
 6788 ?        00:00:00 bonobo-activati
 6800 ?        00:00:00 gvfsd
 6809 ?        00:00:00 gvfs-fuse-daemo
 6844 ?        00:00:17 compiz.real
 6845 ?        00:00:00 bluetooth-apple
 6848 ?        00:00:00 update-notifier
 6851 ?        00:00:00 tracker-applet
 6852 ?        00:00:00 evolution-alarm
 6855 ?        00:00:04 trackerd
 6860 ?        00:00:02 nm-applet
 6862 ?        00:00:00 python
 6865 ?        00:00:00 gnome-volume-ma
 6866 ?        00:00:00 gnome-power-man
 6869 ?        00:00:00 gvfsd-burn
 6873 ?        00:00:00 evolution-data-
 6884 ?        00:00:00 evolution-excha
 6897 ?        00:00:00 trashapplet
 6900 ?        00:00:00 gvfsd-trash
 6942 ?        00:00:04 deskbar-applet
 6946 ?        00:00:01 mixer_applet2
 6948 ?        00:00:00 fast-user-switc
 6950 ?        00:00:00 sh
 6951 ?        00:00:00 compiz-decorato
 6953 ?        00:00:02 gtk-window-deco
 7033 ?        00:00:00 gnome-vfs-daemo
 7036 ?        00:00:00 sh <defunct>
 7091 ?        00:00:00 wpa_supplicant
 7092 ?        00:00:00 dhclient
 7203 ?        00:01:02 firefox
 7228 ?        00:00:00 sh
 7229 ?        00:00:00 run-parts
 7241 ?        00:00:00 apt
 7262 ?        00:00:00 sleep
 7264 ?        00:00:02 gnome-terminal
 7266 ?        00:00:00 gnome-pty-helpe
 7267 pts/0    00:00:00 bash
 7293 pts/0    00:00:00 ps
dave@dave-desktop:~$

---

### Post by abn91c on 2008-06-16
if you want to see who/whats running in a terminal type top

---

### Post by meindian523 on 2008-06-16
seahorse is the GUI frontend for gpg.

---

### Post by anewguy on 2008-06-16
Thanks, but already know that - looking for a source of information to tell me what all of these processes are that are already running, and what I need to do to get rid of those I don't need running.

---

### Post by anewguy on 2008-06-16
> **meindian523 said:**
> seahorse is the GUI frontend for gpg.

Sorry - you got in there between my response to the person before you.  I see that gpg has something to do with cryptography so I can leave it alone.

Thanks!

---

### Post by meindian523 on 2008-06-16
init is the father of all processes,Legit.All processes starting with k are KDE processes,shouldn't be there(not necessarily malicious) unless you are running a KDE app like K3B,Amarok,etc.Tracker*,gnome-*,Xorg,compiz*,gtk-window-decorator are all legit.So is pulseaudio,dbus*,evolution*,clam* if you are running clamAV.I do recall a document on security citing what processes to shutdown  and prevent from running,I can't seem to find it.

---

### Post by spupy on 2008-06-16
winbindd - sounded suspicious, is SAMBA stuff;
console-kit-daemon - freedesktop.org stuff, seems legit;
usbb2k_api - can't find info, something to do with usb, skype pops in google.
btaddconn, btdelconn, bluetoothd - bluetooth stuff.
krfcommd - no idea!

Other processes seem normal... apart from the fact that you are probably running a bajillion programs. ;)

---

### Post by anewguy on 2008-06-16
usbb2k_api is a process for using a USb Telbox to connect my regular phone to my PC so I can use it for regular calls or for SKype.  I have since moved to Vonage and removed the USB Telbox, but I don't know where stuff is specified to be loaded at boot so I can delete the usbb2k_api from it.

---

### Post by anewguy on 2008-06-17
so if I go in to the various rcx directories and either rename or remove things apache, I should be okay?

---

### Post by cariboo on 2008-06-17
Are you running a server of some type as I can see a lot of  things that only need to be run on a server:

```
5731 ? 00:00:17 clamd
5831 ? 00:00:00 freshclam
6062 ? 00:00:00 clamav-milter
6073 ? 00:00:00 clamsmtpd
6673 ? 00:00:00 apache2
6675 ? 00:00:00 apache2
6676 ? 00:00:00 apache2
6677 ? 00:00:00 apache2
6678 ? 00:00:00 apache2
6134 ? 00:00:00 winbindd
6162 ? 00:00:00 winbindd

```

You can safely uninstall all the listed items.

Jim

---

### Post by anewguy on 2008-06-18
> **cariboo907 said:**
> Are you running a server of some type as I can see a lot of  things that only need to be run on a server:

```
5731 ? 00:00:17 clamd
5831 ? 00:00:00 freshclam
6062 ? 00:00:00 clamav-milter
6073 ? 00:00:00 clamsmtpd
6673 ? 00:00:00 apache2
6675 ? 00:00:00 apache2
6676 ? 00:00:00 apache2
6677 ? 00:00:00 apache2
6678 ? 00:00:00 apache2
6134 ? 00:00:00 winbindd
6162 ? 00:00:00 winbindd

```

You can safely uninstall all the listed items.

Jim



Thanks, Jim.  Not running anything more than just plain old Ubuntu.  I noticed some these appeared after I went to comcast and after I installed ies4linux.  I did install clam myself thinking it couldn't hurt to have it running.

I'll look in the various rcx files and rename or remove the others.

Thanks again!

---

### Post by Dedoimedo on 2008-06-18
Hello,

If you want to learn more about each of those processes, either in terminal or in Google, simply type:

man "process name"

This should turn up manual pages for these processes and give you more information, especially regarding their use, necessity etc.

For example man clamd

Dedoimedo

---

### Post by barney385 on 2008-06-18
My *top* says there are two users. Is root concidered a user?

---

### Post by mcduck on 2008-06-18
> **barney385 said:**
> My *top* says there are two users. Is root concidered a user?

If you are on the graphical desktop and you open a terminal that counts as you being logged in twice, thus 2 users.. Open another terminal and it will become 3 users and so on.

By the way, if you want to get rid of services you don't need (like Apache) I wouldn't recommend messing around configuration files to disable them. If you don't need them, uninstall them. The risk of breaking something is much smaller,and you'll gain some disk space as well..

---

### Post by anewguy on 2008-06-21
Well, apparently there is no easy answer, check this list type of answer for this question.  I guess I will have to do the google one at a time thing and see what is needed, then figure out how the heck to get rid of that which isn't.

Thanks everyone!

---

