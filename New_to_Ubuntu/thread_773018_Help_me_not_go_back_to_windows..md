---
title: "Help me not go back to windows."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by TheTouti on 2008-04-28
Hi Forum,

I've been on Ubuntu for 2 weeks now and I have a few problems, nothing extremely bad but annoying enough to make think about going back to windows now.

There's 3 things that I need to be able to fix.

1: Amarok.  It seems to be the best media player available for Linux.  I installed it with SQLLite because I didn't want to go through the extra steps required (so the documentation says) to use MySQL.  There's 2 problems with it. First it's very unstable, almost every time I try the "search" feature to find something it hangs on me and I have to kill it.  The other problem is less annoying but it would be nice if my multimedia keyboard worked.  Most of the multimedia buttons aren't recognized and I had to remap keyboard combinations to almost every function in amarok.

2: Remote access.  This is the biggest issue, it's a must for me and I can't "live" without it.  I obviously want it to be secure so I installed Nochine server to connect through SSH.  The problem is that it seems to interfere with the xorg configuration.  Every time I connect remotely or login locally I get a warning about the keyboard (pc102 vs pc105) and I have to choose betwen X or Gnome layout.  It also screws up the graphics card configuraiton and when I reboot my machine I end up at a very low res like 640x480 and can't change it to a nigher one.  My only way out of this is to run "sudo dpkg-reconfigure xserver.xorg".  Had to do that twice in the last 5 days.

3: No volume control on SPDIF output.  This is quite annoying because it worked in Windows and it works in Amarok so I'm wondering why I can't control the volume in other applications in Ubuntu.

That's it.  I would really like to fix these 3 problems and stay on Ubuntu but if the remote desktop vs screen resolution issue can't be fixed I'll have to go back.

BTW, graphics card is nVidia Geforce 7600

---

### Post by Oldsoldier2003 on 2008-04-28
for problem 2 openssh is probably what you want.

---

### Post by TheTouti on 2008-04-28
openssh is installed along with ddclient, they're both working fine.  The problem really seems to come from "Nomachine".  I uninstalled it and the keyboard layout and resolution problems are gone.  Of course now I no longer have my remote desktop so it's not a good solution.

---

### Post by fs3rp4 on 2008-04-28
Amarok is designed in QT, and Ubuntu use GTK. When you try to use Amarok in ubuntu you are using too several QT libraries. I prefer use a Exaile, its a clone of Amarok and is developed in gtk.

Sometimes less is better.

---

### Post by barney385 on 2008-04-28
Ubuntu media players list...
[http://www.ubuntugeek.com/ubuntu-media-players-overview.html](http://www.ubuntugeek.com/ubuntu-media-players-overview.html)

---

### Post by stchman on 2008-04-28
> **TheTouti said:**
> Hi Forum,

I've been on Ubuntu for 2 weeks now and I have a few problems, nothing extremely bad but annoying enough to make think about going back to windows now.

There's 3 things that I need to be able to fix.

1: Amarok.  It seems to be the best media player available for Linux.  I installed it with SQLLite because I didn't want to go through the extra steps required (so the documentation says) to use MySQL.  There's 2 problems with it. First it's very unstable, almost every time I try the "search" feature to find something it hangs on me and I have to kill it.  The other problem is less annoying but it would be nice if my multimedia keyboard worked.  Most of the multimedia buttons aren't recognized and I had to remap keyboard combinations to almost every function in amarok.

2: Remote access.  This is the biggest issue, it's a must for me and I can't "live" without it.  I obviously want it to be secure so I installed Nochine server to connect through SSH.  The problem is that it seems to interfere with the xorg configuration.  Every time I connect remotely or login locally I get a warning about the keyboard (pc102 vs pc105) and I have to choose betwen X or Gnome layout.  It also screws up the graphics card configuraiton and when I reboot my machine I end up at a very low res like 640x480 and can't change it to a nigher one.  My only way out of this is to run "sudo dpkg-reconfigure xserver.xorg".  Had to do that twice in the last 5 days.

3: No volume control on SPDIF output.  This is quite annoying because it worked in Windows and it works in Amarok so I'm wondering why I can't control the volume in other applications in Ubuntu.

That's it.  I would really like to fix these 3 problems and stay on Ubuntu but if the remote desktop vs screen resolution issue can't be fixed I'll have to go back.

BTW, graphics card is nVidia Geforce 7600

1.  Use Rhythmbox.  I use it and it is really nice.  It is a native Gnome app.

2.  Use VNC viewer.  You can remote into your PC from anywhere as long as the other desktop has VNC installed.  There is a way to do it with a Java enable browser.

3.  I believe in the gnome-volume-manager there should be an SPDIF volume slider.

---

### Post by Alehbye on 2008-04-28
I'm using Amarok in 8.04, using MySQL, it was really easy and took more time to scan my music library than to install and configure both MySQL and Amarok. I'm no where near a pro, but if you want help setting it up, I can probably help you.

---

