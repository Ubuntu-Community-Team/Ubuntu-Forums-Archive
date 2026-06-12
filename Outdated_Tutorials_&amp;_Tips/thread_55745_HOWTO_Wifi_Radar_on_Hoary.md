---
title: "HOWTO: Wifi Radar on Hoary"
date: 2005-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by vvlist on 2005-08-10
Download [wifi-radar.deb](http://www.bitbuilder.com/wifi_radar/) from "Debian Packages" link. Type "sudo dpkg -i wifi-radar_1.9.4-0ubuntu4_all.deb" in terminal, enter root password. *Note* Some may be able to stop here, however, I received an error message saying "/etc/conf.d/wifi-radar.conf is missing" If you get this error as well, read on.
Download the [tar.gz file](http://www.bitbuilder.com/wifi_radar/) from the same page. Untar the file, and copy the "wifi-radar.conf" file into /etc/conf.d. (/etc/conf.d/ didn't exist on my system, so I think that goes for all Ubuntu users, although I am not sure) I hope this helps somebody, because it took me a good hour to figure out. Cheers!

---

### Post by dabear on 2005-08-10
[QUOTE=vvlist]Download [wifi-radar.deb](http://www.bitbuilder.com/wifi_radar/) from "Debian Packages" link. Type "sudo dpkg -i wifi-radar_1.9.4-0ubuntu4_all.deb" in terminal, enter root password. *Note* Some may be able to stop here, however, I received an error message saying "/etc/conf.d/wifi-radar.conf is missing" If you get this error as well, read on.
Download the [tar.gz file](http://www.bitbuilder.com/wifi_radar/) from the same page. Untar the file, and copy the "wifi-radar.conf" file into /etc/conf.d. (/etc/conf.d/ didn't exist on my system, so I think that goes for all Ubuntu users, although I am not sure) I hope this helps somebody, because it took me a good hour to figure out. Cheers![/QUOTE]
 Worked fine for me. However, how do I automatically start this when gnome starts? Is there a way to load it as an applet on my panel?

---

### Post by vvlist on 2005-08-18
[QUOTE=dabear]Worked fine for me. However, how do I automatically start this when gnome starts? Is there a way to load it as an applet on my panel?[/QUOTE]
 Go to System>Preferences>Sessions>Startup tab>add wifi-radar as a startup program. Oh, and you better check [this site](http://www.bitbuilder.com/wifi_radar/)  out. Near the bottom it tells you how to integrate it into gnome panel.  :razz:

---

### Post by Rob2687 on 2005-08-18
I tried following the guide for adding the gnome launcher thing, but most of the folders listed throughout that guide don't even exist.

like /usr/bin/consolehelper 
and when I do:
        4. ln -s /usr/bin/consolehelper /usr/local/bin/wifi_radar
the file says something about broken link

---

### Post by daller on 2005-08-30
If you use Kubuntu, you will need the "gnome-sudo"-package!

Afterwards, trying to execute wifi-radar, I get this error:

daniel@dallap:~/downloads$ wifi-radar
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1255, in ?
    confFile.readfp( open( CONF_FILE ) )
IOError: [Errno 13] Permission denied: '/etc/wifi-radar.conf'

Running "sudo wifi-radar" works - But that is not good - then it asks for a password all the time...

---

### Post by celticmonkey on 2005-09-04
If you are adding wifi-radar to your applications menu using smeg or as a custom gnome panel launcher you can use this in the command field:

gksudo wifi-radar


Just for the record, a quick way to grab and install this:
```
wget -c http://master.grad.hr/~ivoks/ubuntu/wifi-radar_1.9.4-0ubuntu4_all.deb
sudo dpkg -i wifi-radar_1.9.4-0ubuntu4_all.deb
```

---

