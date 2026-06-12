---
title: "Installing and changing between desktop enviroments"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by msmr on 2008-07-24
Hello I'd like to be able to switch between say xfce and gnome. 

I honestly have never done this before and would like to know how.

Thanks.

---

### Post by BGFG on 2008-07-24
Hi, 
Do you just want the window manager or the xubuntu desktop ?
Because in a terminal:
```

sudo apt-get install xubuntu-desktop

```
will give you the xubuntu desktop and at login, you can click 'options' to the bottom left of the screen and select between gnome and xfce sessions.

That command should basically work for any desktop that you'd like to try out...and then
```

sudo apt-get remove xubuntu-desktop
             or
sudo apt-get purge xubuntu-desktop 
```

to remove it if you feel the need

also 
```

sudo apt-get -h

```
for a helpful list of apt-get commands.

---

### Post by RobbyemCee on 2008-07-24
This was most helpful for me.

[https://help.ubuntu.com/8.04/config-desktop/C/other-desktops.htm](https://help.ubuntu.com/8.04/config-desktop/C/other-desktops.htm)

-RobbyemCee

---

### Post by nachomania on 2008-07-24
Oh...I thought you meant the other "switch". Well, if you did, you can change the desktop environment at the login window (options, session type). After you've installed the packages, of course (I didn't know this for a while...wondered where kubuntu was).

---

