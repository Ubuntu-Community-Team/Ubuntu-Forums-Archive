---
title: "deb for  xfce 4.10"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-04-30
if anyone is interested here is a list of deb installs for xfce 4.10 for ubuntu 12.04
works greats

[http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/](http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/)

---

### Post by pqwoerituytrueiwoq on 2012-04-30
where can i get more applets for it?

---

### Post by rburkartjo on 2012-04-30
pq if you right click on the side of the toolbar you get the option to pick from a set of apps. also if you right click and then choose add new launcher you can install anything in your system on the top or bottom panel/have fun

---

### Post by pqwoerituytrueiwoq on 2012-04-30
like the ones in the xfce4-goodies meta package
weather, sensors, cpu govenor

---

### Post by kranklin on 2012-04-30
I installed the package, ran "sudo service lightdm restart" but I don't see XFCE as an option from the login screen. What now?

---

### Post by Toz on 2012-04-30
I haven't tested this deb file so I can't verify whether this works, but you need to have a relevant .desktop file for lightdm to recognize the session. That being the case and taking the contents of the deb file into account, try creating a file in /usr/share/xsessions called xfce4.10.desktop with the following content (with apologies to non-english locales):
```
[Desktop Entry]
Version=1.0
Name=Xfce 4.10 Session
Comment=Use this session to run Xfce 4.10 as your desktop environment
Exec=/usr/local/bin/startxfce4
Icon=
Type=Application

```
...(note: you'll need admin rights to create the file)

---

### Post by KoolPenguin on 2012-05-01
Is there a 32 bit ubuntu package for Xfce 4.10?

Thanks

---

