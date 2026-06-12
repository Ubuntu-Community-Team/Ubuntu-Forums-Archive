---
title: "Can't get rid of winefix!"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by BlackDragonBE on 2008-07-26
I installed winefix recently and for some reason I wanted to remove it, however it gave a lot of errors..
Whenever I use a package manager now to do WHATEVER, I get the following (a lot is Dutch):
```


/var/lib/dpkg/info/winefix.prerm: 8: gtk-update-icon-cache: not found
/var/lib/dpkg/info/winefix.prerm: 9: update-mime-database: not found
dpkg: waarschuwing - verouderd pre-removal script gaf een foutcode 127
dpkg - script uit het nieuwe pakket wordt geprobeerd ...
/var/lib/dpkg/tmp.ci/prerm: 8: gtk-update-icon-cache: not found
/var/lib/dpkg/tmp.ci/prerm: 9: update-mime-database: not found
dpkg: fout bij afhandelen van /home/eric/Bureaublad/winefix_1.0-1ubuntu2_i386.deb (--install):
 subproces nieuw pre-removal script gaf een foutwaarde 127 terug
+ [ ! -f /etc/gnome/defaults.list.bak ]
+ [ -f /etc/gnome/defaults.list ]
+ grep -o -m 1 winefix /etc/gnome/defaults.list
grep: /etc/gnome/defaults.list: No such file or directory
+ match=
+ [  != winefix ]
+ echo application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ tee -a /etc/gnome/defaults.list
tee: /etc/gnome/defaults.list: No such file or directory
application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ gtk-update-icon-cache /usr/share/icons/gnome
/var/lib/dpkg/info/winefix.postinst: 1: gtk-update-icon-cache: not found
+ update-mime-database /usr/share/mime/
/var/lib/dpkg/info/winefix.postinst: 1: update-mime-database: not found
dpkg: fout tijdens opruimen:
 subproces post-installation script gaf een foutwaarde 127 terug
Fouten gevonden tijdens behandelen van:
 /home/eric/Bureaublad/winefix_1.0-1ubuntu2_i386.deb

```

when using apt-get it says I need to reinstall winefix, but it doesn't find an archive (while I got the .deb package on my desktop!!)

Can anyone help? This is really annoying

Cheers

---

### Post by ejpyle on 2008-07-26
> **BlackDragonBE said:**
> I installed winefix recently and for some reason I wanted to remove it, however it gave a lot of errors..
Whenever I use a package manager now to do WHATEVER, I get the following (a lot is Dutch):
```


/var/lib/dpkg/info/winefix.prerm: 8: gtk-update-icon-cache: not found
/var/lib/dpkg/info/winefix.prerm: 9: update-mime-database: not found
dpkg: waarschuwing - verouderd pre-removal script gaf een foutcode 127
dpkg - script uit het nieuwe pakket wordt geprobeerd ...
/var/lib/dpkg/tmp.ci/prerm: 8: gtk-update-icon-cache: not found
/var/lib/dpkg/tmp.ci/prerm: 9: update-mime-database: not found
dpkg: fout bij afhandelen van /home/eric/Bureaublad/winefix_1.0-1ubuntu2_i386.deb (--install):
 subproces nieuw pre-removal script gaf een foutwaarde 127 terug
+ [ ! -f /etc/gnome/defaults.list.bak ]
+ [ -f /etc/gnome/defaults.list ]
+ grep -o -m 1 winefix /etc/gnome/defaults.list
grep: /etc/gnome/defaults.list: No such file or directory
+ match=
+ [  != winefix ]
+ echo application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ tee -a /etc/gnome/defaults.list
tee: /etc/gnome/defaults.list: No such file or directory
application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ gtk-update-icon-cache /usr/share/icons/gnome
/var/lib/dpkg/info/winefix.postinst: 1: gtk-update-icon-cache: not found
+ update-mime-database /usr/share/mime/
/var/lib/dpkg/info/winefix.postinst: 1: update-mime-database: not found
dpkg: fout tijdens opruimen:
 subproces post-installation script gaf een foutwaarde 127 terug
Fouten gevonden tijdens behandelen van:
 /home/eric/Bureaublad/winefix_1.0-1ubuntu2_i386.deb

```

when using apt-get it says I need to reinstall winefix, but it doesn't find an archive (while I got the .deb package on my desktop!!)

Can anyone help? This is really annoying

Cheers
read up on this.....it may help you
[http://ubuntuforums.org/showthread.php?t=352766](http://ubuntuforums.org/showthread.php?t=352766)

---

### Post by BlackDragonBE on 2008-07-26
Ok I'll try that right now

---

### Post by BlackDragonBE on 2008-07-26
It didn't help..
I can't install anything now, every time I try to install something it says I need to reinstall the winefix package, but there's no archive found.
This really sucks, I have no idea what to do

EDIT: 
I fixed it myself, I removed the last 2 lines out of /var/lib/dpkg/info/winefix.prerm
and suddenly I could just remove winefix using the usual apt-get method!
Man I'm happy :p

---

### Post by ejpyle on 2008-07-26
> **BlackDragonBE said:**
> It didn't help..
I can't install anything now, every time I try to install something it says I need to reinstall the winefix package, but there's no archive found.
This really sucks, I have no idea what to do

EDIT: 
I fixed it myself, I removed the last 2 lines out of /var/lib/dpkg/info/winefix.prerm
and suddenly I could just remove winefix using the usual apt-get method!
Man I'm happy :p


strange....i just installed it and tried to uninstall it and I have the same problem....though I was able to correct it by doing a few things in that link I posted.....

I have a negative impression of winefix....heck or anything that starts with "WIN"

---

