---
title: "How do I install Apache on Ubuntu?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Crash 0verride on 2008-05-11
Hi, I'm relatively new to setting up web servers for Linux and I need to figure out how to install it. I looked at the Synaptic Package Manager and I can't figure out what to install.

Could someone give me the Sudo Apt-Get commands to get everything i need to be able to easily turn it on and off and configure it.

Thanks,
Falling-Inferno
Crash 0verride

---

### Post by otrojake on 2008-05-11
I'm not in front of my Ubuntu box right now, so I'm not 100% sure, but I believe it's```
sudo apt-get install apache2
```

---

### Post by Crash 0verride on 2008-05-11
Ok it worked Apache2 is installed but there is no menu or anything to virtually start and stop my program. So how would i get a menu for my Application Bar

---

### Post by annda on 2008-05-11
take a look here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

you can easily switch apache2 on and off using the system > administration > services tool, in addition to the CLI method in the guide. (UPDATE: in ubuntu, if apache2 is installed, it starts at boot automatically.)

post again if you have any problems.

---

### Post by Crash 0verride on 2008-05-11
Ok I got it installed and followed the directions but its loading the "Default" Directory instead of my "New Site" Directory

---

### Post by spiderbatdad on 2008-05-11
I believe the command is ```
sudo a2dissite /etc/apache2/sites-available/default
sudo a2ensite /etc/apache2/sites-available/your_site
```

---

