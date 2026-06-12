---
title: "Unable to reboot 13.04"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2013-05-17
Hi,

Whenever I try to reboot 13.04 it freezes with the purple screen dots. I've tried various 'fixes' found through google, but none have helped. All of them seem to require making changes within the grub file...```
gksu gedit /etc/default/grub
```

I have no problems at all using Shutdown or log out.

It's a completely fresh x64 install, currently using GS3.6, but it does it with Unity as well. Completely updated. I had no probs with the i386 version which was previously installed.

Any help would be very much appreciated!

---

### Post by fantab on 2013-05-17
Did it used to boot properly before? Or do you have this problem since it first boot off the HDD? What is your Machine and what are its specs, especially Graphics, CPU, and RAM?

The simplest solution will be to REINSTALL Ubuntu. Backup your DATA first, if you have any in there.

---

### Post by Baldrick_NZ on 2013-05-18
It's a new install on a Dell Latitude PC, 4x Intel core i5-2540M CPU @ 2.60GHz, 4G Ram, Sadny Bridge graphics.

Previously, the x64 PC had i386 (13.04) installed, with no probs. The problem has been there since x64 install.

Don't want to re-install, it's taken a while to get it where I want it.

Cheers.

---

### Post by fantab on 2013-05-18
I still suggest you re-install because sometimes it is possible that it could be bad install. It happens. Also since yours is a new install it will be easy to re-install.

If you insist on continuing without re-install then:
Remove the line "quiet splash" from the /etc/default/grub, save the file:
```
sudo update-grub
```
And reboot... this will show boot text and note if it reports any errors. And get back.

Copy/paste the contents of /etc/default/grub file here.
Also post the contents of: 
/var/log/boot.log
/var/log/syslog
/var/log/Xorg.0.log

You can use [Ubuntu Pastebin]("http://paste.ubuntu.com/") to paste the logs and poste the links here.

---

### Post by Baldrick_NZ on 2013-05-18
Nope, I think I gave the forum site a bit of a headache with all that info...

Fatal error: Maximum execution time of 180 seconds exceeded in /srv/www.ubuntuforums.org/public_html/includes/functions.php on line 2355

Might just have to forget about reboots and shutdown instead.

Cheers, and thanks for your help.

---

