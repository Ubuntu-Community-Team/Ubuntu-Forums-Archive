---
title: "Help With Apache2"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by UbuntuNerd on 2008-07-03
hey guys can someone please help get mi site working im new to ubuntu so im just trying as i go i have apache 2 ready to go and i can see the default site. i moved my site files to the folder call (www) using nautilus as root. i disable the default site and restarted apache but when i try to acces my site by typing the ip i get this error

Not Found

The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) Server at 192.168.1.102 Port 80

also i notice that the file extension in my site's index is htm and not html like the default site can someone help please 

:confused:

---

### Post by Xerp on 2008-07-03
The Apache documentation can be found here:

[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

You will need to modify your Apache configuration to match what you want to do.

---

### Post by superprash2003 on 2008-07-03
are you trying to use virtual hosts?? you neednt do that actually.. just replace the default document root to whatever folder you want

---

### Post by UbuntuNerd on 2008-07-03
yes im trying to do the virtual host and how do i replace the document root to point at the folder i want please help  thanks

---

### Post by superprash2003 on 2008-07-04
as i said , you dont need to do virtual hosts.. go to the terminal and type sudo gedit /etc/apache2/sites-available/default , the text editor should open with the default file.now replace /var/www with whatever folder you want.. and restart apache by typing sudo /etc/init.d/apache2 restart

---

### Post by mbeach on 2008-07-04
@jperez78: please don't post the same question in multiple places 
[http://ubuntuforums.org/showthread.php?t=848701](http://ubuntuforums.org/showthread.php?t=848701)

thanks,
mb.

---

### Post by Sef on 2008-07-04
> [QUOTE]@jperez78: please don't post the same question in multiple places
[http://ubuntuforums.org/showthread.php?t=848701](http://ubuntuforums.org/showthread.php?t=848701)

thanks,
mb. [/QUOTE]

Thank you mbeach for spotting it.

Post Closed and warning given.

---

