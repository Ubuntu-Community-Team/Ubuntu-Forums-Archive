---
title: "Installing Mozilla Firefox in Ubuntu Server"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-08-30
Greetings,
I have installed Ubuntu 8.04 server edition, have an internet connection. I want to install the Webmin project to have a GUI to be able to control LAMP. I understand that I must have a browser to install Webmin.  I ran "sudo apt-get install firefox" and everything appeared to install when I type in firefox at the command promp I get Error: No display settings found.  

What do I have to do to set up the display to be able to see the browser?

All help will be appreciated.

---

### Post by volkswagner on 2008-08-30
You do not need firefox on the server.  You need a browser on the remote machine to access webmin on the server.

From your remote machine enter in the browser

```
http://YOUR-DOMAIN.NAME:10000/
```

if you are inside you LAN replace yourdomain for internal ip address

---

### Post by jemate18 on 2008-08-30
> **JKHinton CPBD said:**
> Greetings,
I have installed Ubuntu 8.04 server edition, have an internet connection. I want to install the Webmin project to have a GUI to be able to control LAMP. I understand that I must have a browser to install Webmin.  I ran "sudo apt-get install firefox" and everything appeared to install when I type in firefox at the command promp I get Error: No display settings found.  

What do I have to do to set up the display to be able to see the browser?

All help will be appreciated.

If you have other terminals or computer, follow the instructions stated before this reply. If you have just your server and want to install a browser for it, then try installing KDE or GNOME

for KDE
```

sudo apt-get install kubuntu-desktop

```

for GNOME
```

sudo apt-get install ubuntu-desktop

```

After you have installed your desktop environment
may try running your browser or just reinstall firefox

Thanks.

Hope this helps.

jemate18

---

### Post by JKHinton CPBD on 2008-08-30
Hey Volkswagner and Jemate18 thank you both for the respones.  With your instructions, I got Webmin loaded on the Ubunutu server and can view it on my XP box network connection.

---

