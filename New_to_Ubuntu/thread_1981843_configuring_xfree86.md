---
title: "configuring xfree86"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by zedlinkus on 2012-05-17
In red hat linux, you can change your display settings by typing redhat-config-xfree86, How do you do change it in ubuntu using the terminal?

---

### Post by Vereinfachen on 2012-05-17
Ubuntu and any other modern Distribution don't use XFree86 anymore. They use Xorg, which forked XFree86. The main configuration file is /usr/share/X11/xorg.conf

Note that modern Xorg uses input hotplugging, so you most likely don't need to configure anything. If you need to configure small things like mouse etc. be sure to check the /usr/share/X11/xorg.conf.d/ directory.

If you want to configure display settings like resolution just use the Ubuntu System Settings.

---

### Post by steeldriver on 2012-05-17
... and for simple stuff like screen modes there's xrandr

---

### Post by zedlinkus on 2012-05-17
thank you so much vereinfachen, @ steel driver how do I access xrandr

---

### Post by steeldriver on 2012-05-17
> **zedlinkus said:**
> @ steel driver how do I access xrandr

you open a terminal and type 

```
xrandr
```which will show you a brief description of your current display(s) - then try 

```
xrandr --help
```to see the options, it takes some playing to get the hang of it - the GUI display manager tools are simpler - but you asked for a command line tool.

---

### Post by zedlinkus on 2012-05-18
so how do I access the gui display manager tools

---

