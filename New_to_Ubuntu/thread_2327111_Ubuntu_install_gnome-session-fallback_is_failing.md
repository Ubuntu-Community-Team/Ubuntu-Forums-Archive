---
title: "Ubuntu install gnome-session-fallback is failing"
date: 2016-06-07
forum: New to Ubuntu
---

### Post by ben5 on 2016-06-07
We run ubuntu on older PC's and unity is super slow so we use gnome-session-fallback.  Recently though having an error trying to install it. 


(I wonder if it could be a network issue... this is at a remote site who has it's internet routed through VPN to main site before going out to internet... but have not had any other problems and our firewall rules are not restrictive outgoing... however... pc on main site installed the package just fine so thats odd....)


Output below (I did try update and fixmissing as suggested at the bottom but still get same output)






```
admin@port178x2:~$ sudo apt-get install gnome-session-fallback
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel gnome-panel-data gnome-session-flashback
  gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete
  libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libmetacity-private0a
  libpanel-applet-4-0 metacity metacity-common notification-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base
  gnome-themes-standard
The following NEW packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel gnome-panel-data gnome-session-fallback
  gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf
  indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1
  libpanel-applet-4-0 metacity notification-daemon
The following packages will be upgraded:
  libmetacity-private0a metacity-common
2 upgraded, 20 newly installed, 0 to remove and 615 not upgraded.
Need to get 4,993 kB/10.4 MB of archives.
After this operation, 50.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libpanel-applet-4-0 gir1.2-panelapplet-4.0 gnome-panel-data gnome-panel
  gnome-control-center-data gnome-settings-daemon gnome-control-center
  libmetacity-private0a metacity-common metacity gnome-session-flashback
  gnome-session-fallback
Install these packages without verification? [y/N] y
Get:1 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/universe gnome-panel-data all 1:3.8.0-1ubuntu12.2 [1,167 kB]
Get:2 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/main gnome-control-center-data all 1:3.6.3-0ubuntu56.1 [1,216 kB]
Get:3 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/main gnome-settings-daemon i386 3.8.6.1-0ubuntu11.2 [482 kB]
Get:4 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/main gnome-control-center i386 1:3.6.3-0ubuntu56.1 [460 kB]
Get:5 http://do.archive.ubuntu.com/ubuntu/ trusty/universe libgnome-media-profiles-3.0-0 i386 3.0.0-1ubuntu2 [53.6 kB]
Get:6 http://do.archive.ubuntu.com/ubuntu/ trusty/main gstreamer0.10-gconf i386 0.10.31-3+nmu1ubuntu5 [67.9 kB]
Get:7 http://do.archive.ubuntu.com/ubuntu/ trusty/universe gnome-media i386 3.4.0-1ubuntu2 [1,000 kB]
Get:8 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/main libmetacity-private0a i386 1:2.34.13-0ubuntu4.1 [105 kB]
Get:9 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/main metacity-common all 1:2.34.13-0ubuntu4.1 [96.3 kB]
Get:10 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/main metacity i386 1:2.34.13-0ubuntu4.1 [220 kB]
Get:11 http://do.archive.ubuntu.com/ubuntu/ trusty/main notification-daemon i386 0.7.6-1 [30.6 kB]
Get:12 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/universe gnome-session-flashback all 1:3.8.0-1ubuntu12.2 [71.7 kB]
Get:13 http://do.archive.ubuntu.com/ubuntu/ trusty-updates/universe gnome-session-fallback all 1:3.8.0-1ubuntu12.2 [2,946 B]
Get:14 http://do.archive.ubuntu.com/ubuntu/ trusty/universe indicator-applet-complete i386 12.10.2+14.04.20140403-0ubuntu1 [19.7 kB]
Fetched 14.3 kB in 3s (4,519 B/s)
E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-panel/gnome-panel-data_3.8.0-1ubuntu12.2_all.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center-data_3.6.3-0ubuntu56.1_all.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.8.6.1-0ubuntu11.2_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_3.6.3-0ubuntu56.1_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnome-media-profiles/libgnome-media-profiles-3.0-0_3.0.0-1ubuntu2_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-gconf_0.10.31-3+nmu1ubuntu5_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-media/gnome-media_3.4.0-1ubuntu2_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/m/metacity/libmetacity-private0a_2.34.13-0ubuntu4.1_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity-common_2.34.13-0ubuntu4.1_all.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity_2.34.13-0ubuntu4.1_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/main/n/notification-daemon/notification-daemon_0.7.6-1_i386.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-panel/gnome-session-flashback_3.8.0-1ubuntu12.2_all.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-panel/gnome-session-fallback_3.8.0-1ubuntu12.2_all.deb  Size mismatch


E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/pool/universe/i/indicator-applet/indicator-applet-complete_12.10.2+14.04.20140403-0ubuntu1_i386.deb  Size mismatch


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
admin@port178x2:~$

```

---

### Post by X-RED_Tech on 2016-06-08
Try changing the server, then **sudo apt-get update** before anything else.

---

### Post by grahammechanical on 2016-06-08
If it was me I would not install gnome-session-fallback on any version of Ubuntu from 14.04 onwards. Fallback was fine for Ubuntu 12.04 but for 14.04 it should be Flashback.

You will notice from the printout that in trying to install Fallback you are getting packages for both Fallback & Flashback. The combination of the two might be causing this problem.

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

with Gnome Flashback we get two additional login options. Gnome Flashback (Metacity) & Gnome Flashback (Compiz). It is the Metacity option that your computers should use as Metacity uses less memory that Compiz and requires less powerful graphic adapters.

Regards.

---

### Post by CantankRus on 2016-06-08
> **grahammechanical said:**
> If it was me I would not install gnome-session-fallback on any version of Ubuntu from 14.04 onwards. Fallback was fine for Ubuntu 12.04 but for 14.04 it should be Flashback.

You will notice from the printout that in trying to install Fallback you are getting packages for both Fallback & Flashback. The combination of the two might be causing this problem.



I don't think installing **gnome-session-fallback** would cause any problems as this is a transitional dummy package and as such just points to one package as a dependency....**gnome-session-flashback**
which then pulls in the required packages.
After 14.04 there is no **gnome-session-fallback** package.

If you search "Failed to fetch size mismatch" on [**_[COLOR="#B22222"]Googlubuntu[/COLOR]_**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Failed+to+fetch+size+mismatch&as_qdr=all&sa=Google+Search&lang=en") most of the problems point to the use of a proxy.
Some were even caused by Dansguardian blocking the downloading of python-sexy because of the naughty word. :o

---

### Post by ben5 on 2016-06-08
> **CantankRus said:**
> I don't think installing **gnome-session-fallback** would cause any problems as this is a transitional dummy package and as such just points to one package as a dependency....**gnome-session-flashback**
which then pulls in the required packages.
After 14.04 there is no **gnome-session-fallback** package.

If you search "Failed to fetch size mismatch" on [**_[COLOR=#B22222]Googlubuntu[/COLOR]_**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Failed+to+fetch+size+mismatch&as_qdr=all&sa=Google+Search&lang=en") most of the problems point to the use of a proxy.
Some were even caused by Dansguardian blocking the downloading of python-sexy because of the naughty word. :o

I can whitelist domains in my firewall... what should I whitelist do you think to prevent this?  Or what ports does this need?  Perhaps I can set up a separate policy just for those ports that doesn't have the content filtering.

---

### Post by CantankRus on 2016-06-08
Firstly I would try what **X-RED_Tech** said in post#2 to see if you get the same errors.

> **ben5 said:**
> I can whitelist domains in my firewall... what should I whitelist do you think to prevent this?  Or what ports does this need?  Perhaps I can set up a separate policy just for those ports that doesn't have the content filtering.
Not my field of expertise sorry, but your first post shows the mirror server you're using as your software source. 
[http://do.archive.ubuntu.com](http://do.archive.ubuntu.com)
This will change if you change the server in software sources.

---

