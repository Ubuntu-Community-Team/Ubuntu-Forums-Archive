---
title: "There was an error starting the GNOME Settings Daemon."
date: 2008-05-03
forum: Philippine Team
---

### Post by SHENGTON on 2008-05-03
[color=blue]Just upgraded my Ubuntu Gutsy to Hardy. After I reboot my computer I received  this error:


[i][color=green]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the settings Daemon next time you log in.[/color][/i]


Here's the image of the error:

[IMG]http://i168.photobucket.com/albums/u162/SHENGTON/GNOMESettingsDaemon.png[/img]


I already searched it in Google but seems I can't find the exact solution with this. What seems to be the problem?... :([/color]

---

### Post by Script Warlock on 2008-05-03
sa tingin ko hindi to sa OS pero mismo sa machine mo ang may problema try to ALT+CTL+BACKSPACE medyo yan na muna ang konting lunas pero may nagpost na kaparehas ng problema mo but sa earlier version nga lang pero the error is the same. 

[http://ubuntuforums.org/showthread.php?t=339491](http://ubuntuforums.org/showthread.php?t=339491)

sana mapost mo din ang specs at mga hardware na nakakabit sa machine mo para may idea kami sa pagtroubleshoot.

---

### Post by SHENGTON on 2008-05-04
This command solved the problem.
```
sudo chmod -R 0777 /tmp
```

---

