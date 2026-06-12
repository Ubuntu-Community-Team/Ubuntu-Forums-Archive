---
title: "Dedicated Linux server"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by Majekoo on 2014-08-30
[hello everybody ,,Which version of Ubuntu should I use? and how can access to my dedicated server from windows  ]("http://ubuntuforums.org/showthread.php?t=2242040")? i would like also know how to make my server safe afterwards ,, i would like to install Rutorrent and deluge ,FTP and so on , and excuse me i am beginner

it will be nice if someone help me youtube videos i would like use Dedicated server as Seedbox

---

### Post by Tadaen_Sylvermane on 2014-08-30
Server == Ubuntu Server maybe? Once it's installed and setup you can remove the monitor and keyboard and run it headless in a closet or something. SSH access with putty from windows.

---

### Post by whitesmith on 2014-08-30
I can think of no rational reason for not using the latest LTS version, 14.04, unless your machine is on the anemic side. Access may be as the previous poster indicated. Regards.

---

### Post by ian-weisser on 2014-08-30
> **Majekoo said:**
> Which version of Ubuntu should I use?

All versions of Ubuntu will do what you describe. Ubuntu Server is the flavor closest to your desired end state, but also has the steepest learning curve. No GUI - command line only, and that scares some windows users.

If it scares you, then install normal Ubuntu Desktop instead. It functions as a very good server, too. And it has a comfortable GUI.


> **Majekoo said:**
> how can access to my dedicated server from windows?

All the normal ways. Web, ftp, ssh, whatever you want. You will need to install and configure them, of course.


> **Majekoo said:**
> i would like also know how to make my server safe afterwards

Use ssh keys instead of passwords.
Don't run extra services.
Don't let services bind to extra ports.
Use proper users and permissions for services.
Monitor your system for unusual activity.
Check your logs regularly.
Regular backups.

---

### Post by Majekoo on 2014-08-31
> **ian-weisser said:**
> All versions of Ubuntu will do what you describe. Ubuntu Server is the flavor closest to your desired end state, but also has the steepest learning curve. No GUI - command line only, and that scares some windows users.

If it scares you, then install normal Ubuntu Desktop instead. It functions as a very good server, too. And it has a comfortable GUI.




All the normal ways. Web, ftp, ssh, whatever you want. You will need to install and configure them, of course.




Use ssh keys instead of passwords.
Don't run extra services.
Don't let services bind to extra ports.
Use proper users and permissions for services.
Monitor your system for unusual activity.
Check your logs regularly.
Regular backups.

thank you so much for all

there is some video explain all steps one by one ?

---

### Post by ian-weisser on 2014-08-31
We didn't make any videos. With so many possible flavors of Ubuntu, so many ways to configure them, so many server software possibilities, that would be a huge number of videos to cover all the possibilities simply. Plus updates for each new release of Ubuntu every six months. How confusing that would be! No way; we're not doing that. 

Ubuntu is like a Lego kit. You must put together the pieces yourself and discover how it works. That's the fun part.
We have a huge wiki that covers many topics, including how to set up a  server, and details on all associated topics. Look there first.

You're making your task harder by specifying non-Ubuntu software (rutorrent)...which won't work on a headless server anyway (requires a GUI).

If you want to learn how to build a server, you will find a lot of help here.
If you merely want to build a copyright-violation machine as fast as possible, with no real interest in Ubuntu, you won't find much help here.

---

### Post by Iowan on 2014-08-31
[www.howtoforge.com]("www.howtoforge.com") has several Ubuntu server articles (not videos).
[This]("http://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3") is the 14.04 version of The Perfect Server.
Their version of "perfect" probably does not match yours...

---

### Post by Doug S on 2014-08-31
There is also the Ubuntu Official Documentation:
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/14.04/serverguide/index.html](https://help.ubuntu.com/14.04/serverguide/index.html)

myself, I prefer the pdf version:
[https://help.ubuntu.com/14.04/serverguide/serverguide.pdf](https://help.ubuntu.com/14.04/serverguide/serverguide.pdf)
although, due to some compile challenges, the PDF is only available in English on the main site (some regional sites have the pdf posted in their language).

---

### Post by mastablasta on 2014-09-01
> **Majekoo said:**
> thank you so much for all

there is some video explain all steps one by one ?

just use Zentyal Community edition (Ubuntu based). it will install desktop by default you can use expertmode and install it with no desktop. You can then connect to it from windows using a browser. installing what you wan is mostly just clicking a few icons and then clicking install.

I also just tested ClearOS (Cent OS/Red Hat based) also very easy to setup and install. want torrent? connect to server form browser click marketplace and then click torrent it will install it. etc. 

ofcourse you can always just use pure CLI server.

---

