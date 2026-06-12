---
title: "Script execution on user log out/shutdown"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by abybaddi on 2012-04-27
Hello everyone,
I want to remove all the changes done to the desktop, the settings in the guest account of Ubuntu 11.10 aka Ocelot.

I found this to remove all the settings, etc.:

[Here.]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

and this thread for the log out and shutdown:

[http://ubuntuforums.org/showthread.php?t=1517628]("http://ubuntuforums.org/showthread.php?t=1517628")

> **gzarkadas said:**
> [B]User Logout
[/B]Modify /etc/gdm/PostSession/Default (or just place a script in the directory /etc/gdm/PostSession; didn't try that one)

References (see especially the later):
[URL="http://ubuntuforums.org/showthread.php?t=45184"]http://ubuntuforums.org/showthread.php?t=45184
[/URL][http://www.linuxquestions.org/questions/linux-desktop-74/gnome-run-script-on-logout-724453/](http://www.linuxquestions.org/questions/linux-desktop-74/gnome-run-script-on-logout-724453/)

[B]Shutdown, Reboot
[/B]Make a startup script in /etc/init.d (use one of the installed there as a template) and then use from a terminal the `update-rc.d' command to install the appropriate start-stop links at the /etc/rcX.d/ directories.

The easiest setup would be IMO to make one script in /etc/init.d and just call it from within /etc/gdm/PostSession/Default.


But I cannot find the directory /etc/gdm/PostSession in Ubuntu 11.10. Any ideas how to implement this in Ocelot? Thanks in advance.

---

