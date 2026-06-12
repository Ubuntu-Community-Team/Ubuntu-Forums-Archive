---
title: "Can't start phpmyadmin in any way"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by spectatorx on 2014-06-03
I've installed lamp following this instruction:
[http://howtoubuntu.org/how-to-install-lamp-on-ubuntu](http://howtoubuntu.org/how-to-install-lamp-on-ubuntu)
When i open localhost in webbrowser it shows to me localhost apache website so it means apache works.
Next i've installed sudo apt-get install phpmyadmin
When i tried to open localhost/phpmyadmin it doesn't show it in browser, instead it gives me 404 error message. So i created virtual link and did chmod:
cd /var/www/
 sudo ln -s /usr/share/phpmyadmin/ phpmyadmin
sudo chmod -R 777 /var/www/
but still it doesn't want to work. Rstarted apache sudo /etc/init.d/apache2 restart and still nothing.

I am out of ideas, google seems to be so as well.

---

### Post by jdeca57 on 2014-06-03
In essence, phpmyadmin (mind the capitals) is a php script. You can download it from the website as a zip file (phpMyAdmin-4.2.2-all-languages.zip) and copy its content under phpmyadmin to /var/www/html, the default documentroot for 14.04 or you can change the documentroot to /var/www and put it there. I didn't try apt-get way, and so I can't advice much more than download the script - it works - and be aware of the place to put it.

---

### Post by Duncubuntu on 2014-06-03
You really don't want to 777 your web dir. In almost all cases, 664 for files and 755 for folders is good. By giving 777 to everything under the www directory, all your files/directories will be readable, writeable and executable. You may write files with different permissions, but be careful when using 777.

In regards to your phpmyadmin problem:

You can try:
```
sudo dpkg-reconfigure phpmyadmin
```

Or remove phpmyadmin (be sure to copy this EXACT line):
```
sudo apt-get purge phpmyadmin*
```

then re-install.

If that doesn't fix it there is lots of good information here:
[uhelp]community/phpMyAdmin[/uhelp]

and here:
[https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04](https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04)

---

