---
title: "linux newbie, lamp server, php5, mysql, apache 2 help"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by nakita on 2008-05-10
I am moving from windows to linux and am not familiar with linux. I instlled ubuntu server 8.04 with the lamp option during the install. The lack of a gui is no big deal but i am not familiar with the commands to make things work. I have searched the forum and need help with the cli commands to start php and mysql etc. also i was thinking should i maybe install the desktop version and install lamp or should i just add a gui to my server install until i am more familliar with linux commands. I want to set up a website for family and friends and general learning of php, apache 2,  mysql creating a few tables etc for a couple of small databases. any help and suggestions is appreciated.

---

### Post by songshu on 2008-05-10
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

these might be a good starting point.

i could recommend something like Joomla to make an easy but good looking website but there are many others to choose from.

php does not need to be started and mysql and apache are already running.

you could do something like this to restart - start -restart them

```
/etc/init.d/apache2 restart
```

---

### Post by nakita on 2008-05-10
Thank you very much for your time and help. :KS:KS

---

### Post by Journeyman on 2008-05-10
You might look into installing webmin, it is a web based gui control panel.  Might help with configuring apache and such.

---

