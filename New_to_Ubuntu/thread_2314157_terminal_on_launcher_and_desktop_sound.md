---
title: "terminal on launcher and desktop sound"
date: 2016-02-18
forum: New to Ubuntu
---

### Post by bdubawoop on 2016-02-18
ubuntu 14.04 on thinkpad e550.

how do i get a shortcut for the terminal on the launcher or desktop?

also would like the logon sound back as it was in 12.04 ( chorus). i found it in /usr/bin/canberra ... but it was grayed out.

---

### Post by Burgy on 2016-02-18
You can access the terminal by keyboard shortcut CTRL+ALT+T and to put an icon on the desktop you can search for the terminal in the top left and drag the icon to the desktop and marking it as executable.

May have to use root privileges to change files in system for that to work? Is your user account an admin?

---

### Post by mc4man on 2016-02-18
To add the terminal to the launcher (or any app), just open a terminal. An icon will then be in the launcher, right click on it > lock to launcher

As far as that old log in 'music', it's not used anymore. You could sort of enable it by 
Open the Dash from launcher (top icon), type in & open startup applications
Create a new one with this as command, scr. 1
```
usr/bin/canberra-gtk-play --id="desktop-login"
```
You can name it whatever you want, doesn't matter

If you grow tired of just open Startup Applications again & either disable it, (remove red ck. mark)  or remove it entirely, scr 2

---

### Post by bdubawoop on 2016-02-19
right click launcher. that worked.

ditto add to statup apps.

thanks mc4man

---

