---
title: "Apache2 directories question"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Darkmatter5 on 2008-05-12
I have Apache, phpmyadmin, and Gallery2 installed on my Ubuntu 8.04 LAMP server.  How does one configure Apache so that directories not under Apache's Server root directory show up as directories in Apache. Meaning Apache uses /var/www/apache-default/ as the location of which localhost will show the index.html file from. PHPmyadmin stores all it's files in /usr/share/phpmyadmin. If I type [http://localhost](http://localhost) it'll display the index file from /var/www/apache-default/, if I type [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it'll show the index file from /usr/share/phpmyadmin/. This was setup upon phpmyadmin's installation, when I installed Gallery2 it put the index file in /usr/share/gallery2/, so how do I include Gallery2 in Apache the same way PHPmyadmin is so I can just type [http://loaclhost/gallery2/](http://loaclhost/gallery2/) to access the index file of Gallery2?

Thanks!

---

### Post by spiderbatdad on 2008-05-12
You can create any number of directories in the virtual hosts file: sites-available. It is generally a good idea to put your index.html's in a non root directory...like /home/user/public_html/index.html (or even create an unprivileged user with no shell access, and host files from that account.) Your /public_html/index.html can link any number of other pages, or you can create multiple DNS's. You can also use redirects in the virtual host file to access other pages.

To enable a site other than the default, simply run sudo a2ensite /etc/apache2/sites-available/your_site  and sudo a2dissite /etc/apache2/sites-available/default, to disable the default site.

---

### Post by mkoehler on 2008-05-12
Virtual Directories in Apache is one possible solution.  Additionally, a less elegant solution (but one which provides the same result) is just to put a simlink to the Gallery2 folder in your apache-default folder - I can't say for sure without checking, but I believe that phpmyadmin does the latter.

---

