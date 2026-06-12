---
title: "Problem running apache server in Ubuntu 11.04"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by artagnon on 2011-10-03
[SIZE=3]Hi,
I have installed Ubuntu 11.04 as Guest OS through Virtual Box on Windows 7 as host OS.
 WhiIe installing lamp and setting up local server, I accidentally deleted the file default and default-ssl in etc/apache/sites-enabled/  folder and now I'm unable to run my apache server. I tried completely removing the Apache2 package from synaptics manager and then, reinstalling it but it does not seem to work as the sites-enabled folder remains empty. While typing apachectl start in terminal, it shows 
/usr/sbin/apachectl: 148: /usr/sbin/apache2: not found
Action 'start' failed.
The Apache error log may have more information.
The error log is empty. 
[/SIZE]

---

### Post by cavh on 2011-10-03
In a terminal, try the following (you will need to enter your password but you will not see it displayed on screen, just type the password and hit the enter key):

1. ```
sudo apt-get purge apache2
```

and then the following to install LAMP super-easily:

2. ```
sudo apt-get install tasksel
``` Note - you may get a message saying tasksel is already installed - if so, just move on to point 3 below.

and then 

3. ```
sudo tasksel
```

Note: when running tasksel, use the down arrow to move down the list and the space bar to select/deselect an item. Use the tab key to move to the 'OK' box. DO NOT deselect any of the items which are already listed.

---

### Post by artagnon on 2011-10-04
Thanks a lot, it works as good as ever but now Phpmyadmin doesn't seem to work. As I point my browser to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) all it shows is
**Not Found**

 The requested URL /phpMyAdmin was not found on this server. I installed Lamp server from tasksel as mentioned by you.

---

### Post by cavh on 2011-10-04
Do you have a folder /etc/phpmyadmin and if so, what files are listed there?

You can list the files by typing this in a terminal window:

```
ls /etc/phpmyadmin
```

If you don't have this folder, suggest you run tasksel again and go through the LAMP installation again, paying close attention to the choices ...

---

### Post by artagnon on 2011-10-05
Yes, indeed I could not find the phpmyadmin in the etc folder, so I just installed it again ad everything now seems to work perfectly.

Thanks a lot, more for being patient with a newbie !!

---

