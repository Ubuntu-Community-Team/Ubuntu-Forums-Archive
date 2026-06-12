---
title: "Hardy Heron Server"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Jordan247 on 2008-08-08
Is there a GUI interface for this server product like the desktop edition?  I installed it and it looks like straight up shell command prompts

Cheers

Jordan

---

### Post by webofunni on 2008-08-08
Hello Jordan,

  Running GUI in a server OS is not recomended. You can install desktop interface like Gnome or KDE if you need Desktop insteface.

---

### Post by GreenN00b on 2008-08-08
You can install the desktop gui by invoking
```
apt-get install ubuntu-desktop
```

---

### Post by Jordan247 on 2008-08-08
Thanks for apt-get command, but why would you say it is not recommended to install the GUI on server product?

Jordan

---

### Post by Oldsoldier2003 on 2008-08-08
> **Jordan247 said:**
> Thanks for apt-get command, but why would you say it is not recommended to install the GUI on server product?

Jordan

[uhelp]community/ServerGUI[/uhelp]

---

### Post by GreenN00b on 2008-08-08
You can try webmin from [http://webmin.com](http://webmin.com) for server administration. It has a web interface and it's pretty useful.

---

### Post by cariboo on 2008-08-08
I have to agree with GreenN00b, you can check out a webmin demo at:

[http://www.webmin.com/demo.html](http://www.webmin.com/demo.html)

Webmin sets out everyting that you need to administer your server, there are things in the menu that you probably haven't though of. You can check logs, it monitors your hardware, set up virtual domains, set up ftp servers and more. The only other thing you may need if you are planning on using mysql is to install phpmyadmin. It is available from the repositories.

Jim

---

### Post by WRDN on 2008-08-08
> **webofunni said:**
> Hello Jordan,

  Running GUI in a server OS is not recomended. You can install desktop interface like Gnome or KDE if you need Desktop insteface.

GNOME is a pretty 'heavy' GUI for a server. The OP may be better using XFCE or Fluxbox (light).

---

