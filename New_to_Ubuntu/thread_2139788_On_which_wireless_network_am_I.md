---
title: "On which wireless network am I?"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by dtconnor on 2013-04-27
How can I tell what wireless network I have accessed

Here a brief history
-was on 12.10
-was using Wicd
-upgraded to 13.04
-got all kinds of issues to include "kernel panic"
-re-installed 13.04 useimg a DVD cleared up most big issues - I can boot up
-Wicd stopped working 
-uninstalled ALL network mangers
-re-installed Wicd - still not working (aslking for a password)
-re-installed gnome NM can not find it on the Dash board
-re-installed the default NM (the one that looks like a folder with a cat5 jack)
-drove down to the beach thinking I would have to use a wired connection
-powered up and I am on-line without useing the PW I was given to access wireless
-obviously I am on some random wireless network

---

### Post by wildmanne39 on 2013-04-27
Please do:
```
iwconfig
```
Thanks

---

### Post by dtconnor on 2013-04-27
THX - that worked and I noticed the network was checked 
One other question how can I get the fan/two way arrow icons back

---

### Post by wildmanne39 on 2013-04-27
For network manager?

---

### Post by dtconnor on 2013-04-27
I think so - in the bar across the top next to the sound, mail, bluetooth etc. icons.
There used to be a fan (wireless) or double arrows (wired) 
They are gone and I have be researching how to get them back

Big mistake upgrading to 13.04 BTW

---

### Post by wildmanne39 on 2013-04-27
I believe this will do it:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
Thanks

---

### Post by dtconnor on 2013-04-27
THX - but that didn't do it
ran the cmd - saw no change so I rebooted - still no icon

---

### Post by wildmanne39 on 2013-04-27
I checked and that should have done it, maybe the package name has changed in 13.04, you can look it up with software center, I do not have 13.04 installed.
The name use to be network-manager-gnome.

Did the command complete sucessfully?
Thanks

---

### Post by dtconnor on 2013-04-27
It did - see below

dtconnor@HP-ProBook-4520s:~$ sudo apt-get install --reinstall network-manager network-manager-gnome
[sudo] password for dtconnor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-urwid
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/911 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 185628 files and directories currently installed.)
Preparing to replace network-manager 0.9.8.0-0ubuntu6 (using .../network-manager_0.9.8.0-0ubuntu6_amd64.deb) ...
Unpacking replacement network-manager ...
Preparing to replace network-manager-gnome 0.9.8.0-1ubuntu2 (using .../network-manager-gnome_0.9.8.0-1ubuntu2_amd64.deb) ...
Unpacking replacement network-manager-gnome ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up network-manager (0.9.8.0-0ubuntu6) ...
Setting up network-manager-gnome (0.9.8.0-1ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dtconnor@HP-ProBook-4520s:~$

---

### Post by wildmanne39 on 2013-04-27
I do not know why it did not work according to the information you posted it should of.
Thanks

---

### Post by dtconnor on 2013-04-27
THX for the help - I'll keep trying 
I think it all started with Wicd crapping out with the upgrade to 13.04
I ended up ripping out all the nm and re-installing 

problem is I can't configure anything now except from the command line which being a Windows convert puts me  on a steep learning curve

---

### Post by wildmanne39 on 2013-04-27
Your welcome! it is possible you did not get all of wicd removed.

You can not have network manager and wicd installed at the same time.

---

### Post by steeldriver on 2013-04-27
The actual GUI part of network-manager-gnome is called nm-applet (I don't think this has changed for 13.xx) - see if you can start it manually e.g.

```
nohup nm-applet 2>/dev/null &
```

If that works, but nm-applet is not starting automatically, then check the settings in /etc/xdg/autostart/nm-applet.desktop (or ~/.config/autostart/nm-applet.desktop if you have one) - make sure Unity is not included in the NotShowIn list

---

### Post by dtconnor on 2013-04-27
Bingo - that did it - popped right up

THX much Wild Man and steeldriver

---

### Post by dtconnor on 2013-05-02
nohup nm-applet 2>/dev/null &
how can I make this persistant

---

### Post by -kg- on 2013-05-02
Include the command in Startup.  It will run as part of the startup procedure every time you reboot.

---

