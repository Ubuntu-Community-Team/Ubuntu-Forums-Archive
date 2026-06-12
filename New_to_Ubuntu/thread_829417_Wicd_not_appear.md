---
title: "Wicd not appear"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-14
Hello, i install Wicd to replace Network Manager. I can access the Setup windows immediately after installing it through Synaptic. However after reboot I can not see it window at all when I click the icon. I dont even find related entry in System Monitor to tell that it is running at the background. Please assist me on this.

---

### Post by TeoBigusGeekus on 2008-06-14
Go to Preferences->Sessions.
Click Add: type Wicd as name (or whatever you want to) and 
```
/opt/wicd/tray.py
```
as the command. Click Ok and reboot.

---

### Post by wariskampar on 2008-06-14
Hello, i already tried this but problem still persist. Maybe my earlier explanation has making everyone confuse so let me expalin once again. I can see Wicd icon in Application>Internet>Wicd. However, when i click on that icon, nothing happen (presumably WIcd window will appear). I thought maybe there are some packages related with Network Manager still linger in my System so I clear my Orphaned Package as well as Config Residue. The problem still persist. I even restart several time and the problem still stay. What should I do!

---

### Post by cariboo on 2008-06-14
Is tray.py running? to find out, in a terminal type the following:

```
ps ax | grep tray
```

This will list everything with the word tray in it. If you don't get any output then tray.py is not running.

Jim

---

### Post by imdano on 2008-06-15
Delete /opt/wicd/data/wired-settings.conf, then restart the daemon, then start the tray.

---

