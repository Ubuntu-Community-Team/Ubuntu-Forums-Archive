---
title: "how to load my site to apache2 help"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by UbuntuNerd on 2008-06-29
hey guys i have a network of 3 pc's one vista and Ubuntu desktop and server also everything is working great i can see and access my shares from everywhere i made a site and now im ready to try it i have apache 2 configure to the point where it says (it works) and i have some really good tutorials on how to load your site in apache 2 the problem is im new to the server and i know very little about editing files in the terminal can some one please help me step by step:confused:

---

### Post by Matthewslf on 2008-06-29
All of your configuration should be done in /etc/apache2/sites-available/Default unless you have made your own config file. To edit it, hit alt-F2 and type "gksudo gedit /etc/apache2/sites-available/Default". This should bring up the config file without any use of the terminal. When you want to apply the changes you've made, type in a terminal "sudo /etc/init.d/apache2 reload". If you want help with the config file, tell me what settings you want to change.

---

### Post by kool_kat_os on 2008-06-29
....or just move the files of your website in the "/var/www/" directory

---

