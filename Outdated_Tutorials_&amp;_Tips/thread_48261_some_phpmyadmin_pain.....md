---
title: "some phpmyadmin pain...."
date: 2005-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by nephish on 2005-07-11
Hey there all,

i have installed phpmyadmin on fresh install of Hoary, i go to localhost/phpmyadmin and the browser tells me it cannot find /cgi-bin/yada yadda on this server.
the directory it put into my /var/www is not a directory but a symlink. i tried to get the thing by typing in the whole path and when i go for the index.php file, it asks me if i want to open it with a text editor or save it to disk, basically, my php isnt working.. 
what should i do?
thanks

---

### Post by petard on 2005-07-11
It sounds like you need to install apache with php and mysql support.  Here's a link that should get you started....

[http://www.visiomode.com/ndmanual/installing/installing_on_ubuntu_linux.html](http://www.visiomode.com/ndmanual/installing/installing_on_ubuntu_linux.html)

---

### Post by drummer on 2005-07-11
[QUOTE=nephish]Hey there all,

i have installed phpmyadmin on fresh install of Hoary, i go to localhost/phpmyadmin and the browser tells me it cannot find /cgi-bin/yada yadda on this server.
the directory it put into my /var/www is not a directory but a symlink. i tried to get the thing by typing in the whole path and when i go for the index.php file, it asks me if i want to open it with a text editor or save it to disk, basically, my php isnt working.. 
what should i do?
thanks[/QUOTE]
 There are also some instructions on the Ubuntu Guide: [http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver)
After following these instructions and installing phpmyadmin from apt, my server worked without a hitch.

---

### Post by nephish on 2005-07-11
[QUOTE=drummer]There are also some instructions on the Ubuntu Guide: [http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver)
After following these instructions and installing phpmyadmin from apt, my server worked without a hitch.[/QUOTE]
 yep think with all the installs / removes / etc.... i have totally gakked up my system.
not to worry. i can start fresh tomorrow, format, install, etc... follow the starter guide.
ah-well.

thanks for the tips.

---

