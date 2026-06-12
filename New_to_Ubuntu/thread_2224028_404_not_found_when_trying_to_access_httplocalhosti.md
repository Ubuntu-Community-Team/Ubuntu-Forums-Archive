---
title: "404 not found when trying to access http://localhost/info.php after setting up LAMP"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by thirdnipple on 2014-05-14
I have tried to install Apache, mySQL, and PHP on Ubuntu 14.04.  I can access local host in my browser and I get the default Apache page, which say "It Works!", but when I try to go to [http://localhost/info.php](http://localhost/info.php) I get the 404 error:

**Not Found**

[COLOR=#000000][FONT=Times New Roman]The requested URL /info.php was not found on this server.[/FONT][/COLOR]
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at localhost Port 80


this is what's in my info.php file:

[PHP]
<html><head><title>PHP Test</title></head><body><?php phpinfo(); ?></body></html>[/PHP]

Any help would be appreciated.

---

### Post by alket on 2014-05-14
Where did you put that file ? Did you change DocumentRoot ?

---

### Post by thirdnipple on 2014-05-14
The file is in /var/www/

I have not changed DocumentRoot.  How would I do that?

---

### Post by Doug S on 2014-05-14
The default location for DocumentRoot is now /var/www/html
You can change it in /etc/apache2/sites-available/000-default.conf

---

### Post by newbie2244 on 2014-05-14
You embedded php code in an <html> file. Strip the <html> tags and just leave the phpinfo()  enclosed in the php tags. Assuming that your path to the location of the file is correct, it should execute your php function. Keep the same file name, with ".php" ending.

---

### Post by thirdnipple on 2014-05-14
You guys are awesome!

I modified the file to remove the <html> tags and moved the file to the html folder rather than changing the DocumentRoot and the page came up properly.  Thanks again for all of the help!!!

---

### Post by Doug S on 2014-05-14
> **newbie2244 said:**
> You embedded php code in an <html> file. Strip the <html> tags and just leave the phpinfo()  enclosed in the php tags. Assuming that your path to the location of the file is correct, it should execute your php function. Keep the same file name, with ".php" ending.Huh?? That works fine. Try it. Both ways work fine.

@thirdnipple: Glad you got it working.

---

