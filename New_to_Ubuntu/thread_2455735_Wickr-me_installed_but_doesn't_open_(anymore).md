---
title: "Wickr-me installed but doesn't open (anymore)"
date: 2020-12-26
forum: New to Ubuntu
---

### Post by ulfhanu on 2020-12-26
Hi all and merry Christmas,

I'm recently on Ubuntu 20.04 and I installed wickr-me with snap a week ago. It worked fine and then I shut down the PC and went away for a couple of days. Now I'm back, nobody touched the PC (impossible because I live alone) and after startup wickr just doesn't open at all. I click the icon and nothing happens at all.
I tried to remove and reinstall and nothing. Unfortunately I'm pretty new to Linux and I have no idea how to solve this. Wick-me is very important to me.

Any aditional information you might need I will gladly provide.

Thanks

---

### Post by ulfhanu on 2020-12-26
By the way I alrady tried stable, candidate and beta

---

### Post by #&amp;thj^% on 2020-12-26
Wickrme explicitly states that they only support Ubuntu 16.04
EDIT: It did install stable and it opened for me with:
```
wickrme
Gtk-Message: 12:03:18.950: Failed to load module "appmenu-gtk-module"
Gtk-Message: 12:03:18.954: Failed to load module "canberra-gtk-module"
[1226/120319.951148:WARNING:resource_bundle_qt.cpp(116)] locale_file_path.empty() for locale 
Qt WebEngine ICU data not found at /opt/qt512/resources. Trying parent directory...
Qt WebEngine ICU data not found at /opt/qt512. Trying application directory...
Installed Qt WebEngine locales directory not found at location /opt/qt512/translations/qtwebengine_locales. Trying application directory...
Qt WebEngine locales directory not found at location /snap/wickrme/440/usr/bin/qtwebengine_locales. Trying fallback directory... Translations MAY NOT not be correct.
Path override failed for key ui::DIR_LOCALES and path '/home/me/snap/wickrme/440/.QtWebEngineProcess'
Qt WebEngine resources not found at /opt/qt512/resources. Trying parent directory...
Qt WebEngine resources not found at /opt/qt512. Trying application directory...
[1226/120320.038987:WARNING:resource_bundle_qt.cpp(116)] locale_file_path.empty() for locale 

```

---

### Post by ulfhanu on 2020-12-26
Yes. Funny enough it worked though. So no chance then?

EDIT: just saw your edit

Tried to start and it says:

Segmentation fault (core dumped)

---

### Post by #&amp;thj^% on 2020-12-26
> **ulfhanu said:**
> Yes. Funny enough it worked though. So no chance then?

EDIT: just saw your edit

Tried to start and it says:

Segmentation fault (core dumped)

```
snap list
Name                 Version           Rev    Tracking         Publisher      Notes
core18               20201210          1944   latest/stable    canonical&#10003;     base
gtk-common-themes    0.1-50-gf7627e4   1514   latest/stable    canonical&#10003;     -
makemkv              1.15.4            232    latest/stable    diddledan      -
snapd                2.48.1            10492  latest/stable    canonical&#10003;     snapd
software-boutique    0+git.f633ffb     54     latest/stable/…  flexiondotorg  classic
ubuntu-mate-welcome  20.10.0-bb92cef1  575    latest/stable/…  flexiondotorg  classic
wickrme              5.68.7            440    latest/stable    tleavy         -

```
Try Installing it again, might show us something.

---

### Post by ulfhanu on 2020-12-26
Well. Running wickr sudo it says:

No protocol specified
Aborted



And:

Name                           Version                     Rev    Tracking         Publisher             Notes
canonical-livepatch            9.5.5                       95     latest/stable    canonical&#10003;            -
chromium-ffmpeg                0.1                         17     latest/stable    canonical&#10003;            -
core                           16-2.48                     10577  latest/stable    canonical&#10003;            core
core18                         20201210                    1944   latest/stable    canonical&#10003;            base
core20                         20201210                    904    latest/stable    canonical&#10003;            base
gnome-3-28-1804                3.28.0-19-g98f9e67.98f9e67  145    latest/stable    canonical&#10003;            -
gnome-3-34-1804                0+git.3556cb3               60     latest/stable/&#8230;  canonical&#10003;            -
gtk-common-themes              0.1-50-gf7627e4             1514   latest/stable/&#8230;  canonical&#10003;            -
opera                          73.0.3856.284               104    latest/stable    opera-software&#10003;       -
protonmail-desktop-unofficial  1.2.1                       11     latest/stable    kontrollanten         -
signal-desktop                 1.39.4                      344    latest/stable    snapcrafters          -
snap-store                     3.38.0-59-g494f078          518    latest/stable/&#8230;  canonical&#10003;            -
snapd                          2.48.1                      10492  latest/stable    canonical&#10003;            snapd
spotify                        1.1.46.916.g416cacf1        43     latest/stable    spotify&#10003;              -
telegram-desktop               2.5.1                       2315   latest/stable    telegram.desktop      -
vuze-vs                        5.7.6.0-snap1               3      latest/stable    vasilisc              -
walc                           0.1.11                      17     latest/stable    cstayyab              -
warzone2100                    3.4.1                       1573   latest/stable    warzone-2100-project  -
warzone2100-videos             1                           2      latest/stable    warzone-2100-project  -
wickrme                        5.68.7                      440    latest/stable    tleavy                -

---

### Post by CelticWarrior on 2020-12-26
The suggestion was/is to reinstall it and try again. NOT to run it with sudo, something you never do with graphical user apps.

---

### Post by ulfhanu on 2020-12-26
ulfhanu@ulfhanu-comp:/run/user$ sudo snap remove wickrme
wickrme removed

ulfhanu@ulfhanu-comp:/run/user$ sudo snap install wickrme
wickrme 5.68.7 from Wickr Inc (tleavy) installed

I guess nothing new. I'm new to this Linux anyway. I used Linux many yaers ago but I find it quiete confusing now

---

### Post by ulfhanu on 2020-12-26
> **CelticWarrior said:**
> The suggestion was/is to reinstall it and try again. NOT to run it with sudo, something you never do with graphical user apps.


I had tried that before you suggested it..... Sorry.

---

### Post by #&amp;thj^% on 2020-12-26
did it open?

---

### Post by ulfhanu on 2020-12-26
> **1fallen said:**
> did it open?

No. Nothing. Dead

---

### Post by #&amp;thj^% on 2020-12-26
Either log out and back in again, or restart your system, to ensure snap&#8217;s paths are updated correctly.

---

### Post by ulfhanu on 2020-12-26
I will do that now. BRB

---

### Post by deadflowr on 2020-12-26
Move or remove the snap wickrme directory in the /home/user/snap directory.

All snaps create a configuration directory inside the snap folder.
These folders remain on the system regardless of whether or not the snap is still installed.
They need to be manually moved or removed.
Deleting or moving the folder will allow the app to reset itself, and will create a new configuration directory with the default values.

---

### Post by ulfhanu on 2020-12-26
> **deadflowr said:**
> Move or remove the snap wickrme directory in the /home/user/snap directory.

All snaps create a configuration directory inside the snap folder.
These folders remain on the system regardless of whether or not the snap is still installed.
They need to be manually moved or removed.
Deleting or moving the folder will allow the app to reset itself, and will create a new configuration directory with the default values.

Ok. Restarted and nothing.
Deleted the directory and nothing either

---

### Post by ulfhanu on 2020-12-26
Well. As you said there is no support for Ubuntu 20.04 I just give up.
Spent too much time on this already but it wasn't really beneficial to me work to install Ubuntu at all. Now I spend my time fixing my PC like in the olden days instead of just working on things I actually have to do. Seems to be more of a past-time this OS.
But thank you for your help.
Merry Christmas

---

### Post by deadflowr on 2020-12-26
Run the command
```
wickrme
```
then copy the output and post it.

---

### Post by ulfhanu on 2020-12-26
Segmentation fault (core dumped)

That's all it says

---

### Post by #&amp;thj^% on 2020-12-27
> **ulfhanu said:**
> Segmentation fault (core dumped)

That's all it says

I may have duplicated your problem, but I had to do it on arch.
First i removed the snap wickrme:
```

sudo snap remove --purge wickrme
```
After talking with them i decided to go pro.(Free)
```

sudo snap install wickrpro
```
then ran in debug:
```

wickrpro
```
It would never say Segfault, but the error was permission related, i also run apparmor on Arch Linux.
My fix to this was:
```

systemctl enable --now apparmor.service
```
Cleaned up a bit:
***Run One Line at a time.
```

sudo apparmor_parser -r /etc/apparmor.d/*snap-confine*
sudo apparmor_parser -r /var/lib/snapd/apparmor/profiles/snap-confine*
```
Now reload those:
```

systemctl restart apparmor.service
systemctl restart snapd.service
systemctl enable --now snapd.apparmor.service
```
As you can see it now loads on mutiple reboots.
```
aa-status
apparmor module is loaded.
68 profiles are loaded.
68 profiles are in enforce mode.
   /usr/lib/apache2/mpm-prefork/apache2
   /usr/lib/apache2/mpm-prefork/apache2//DEFAULT_URI
   /usr/lib/apache2/mpm-prefork/apache2//HANDLING_UNTRUSTED_INPUT
   /usr/lib/apache2/mpm-prefork/apache2//phpsysinfo
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /var/lib/snapd/snap/core/10577/usr/lib/snapd/snap-confine
   /var/lib/snapd/snap/core/10577/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /var/lib/snapd/snap/snapd/10492/usr/lib/snapd/snap-confine
   /var/lib/snapd/snap/snapd/10492/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   apache2
   apache2//DEFAULT_URI
   apache2//HANDLING_UNTRUSTED_INPUT
   apache2//phpsysinfo
   avahi-daemon
   dnsmasq
   dnsmasq//libvirt_leaseshelper
   dovecot
   dovecot-anvil
   dovecot-auth
   dovecot-config
   dovecot-deliver
   dovecot-dict
   dovecot-dovecot-auth
   dovecot-dovecot-lda
   dovecot-dovecot-lda//sendmail
   dovecot-imap
   dovecot-imap-login
   dovecot-lmtp
   dovecot-log
   dovecot-managesieve
   dovecot-managesieve-login
   dovecot-pop3
   dovecot-pop3-login
   dovecot-script-login
   dovecot-ssl-params
   dovecot-stats
   firejail-default
   identd
   klogd
   lsb_release
   mdnsd
   nmbd
   nscd
   ntpd
   nvidia_modprobe
   nvidia_modprobe//kmod
   php-fpm
   ping
   smbd
   smbldap-useradd
   smbldap-useradd///etc/init.d/nscd
   snap-update-ns.core
   snap-update-ns.session-desktop
   snap-update-ns.viber-mtd
   snap-update-ns.viber-unofficial
   snap-update-ns.wickrpro
   snap.core.hook.configure
   snap.session-desktop.session-desktop
   snap.viber-mtd.viber
   snap.viber-unofficial.viber
   _**snap.wickrpro.wickrpro**_
   syslog-ng
   syslogd
   traceroute
   winbindd
0 profiles are in complain mode.
0 profiles are in kill mode.
0 profiles are in unconfined mode.
0 processes have profiles defined.
0 processes are in enforce mode.
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.


```

---

