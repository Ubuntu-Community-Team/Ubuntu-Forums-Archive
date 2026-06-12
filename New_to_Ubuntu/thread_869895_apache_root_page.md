---
title: "apache root page"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by ub007 on 2008-07-25
Hiya,

Plz help me out with this....
Currently the default web page for my apache server is index.html in var/www directory
> [http://david.surrey.ac.uk](http://david.surrey.ac.uk)      gives index.html
I have installed osCommerce and would like to change the defualt page to the login page of this shopping portal

The file is login.php which resides in /var/www/oscommerce/catalog/
 
i tried
sudo nano /etc/apache2/sites-available/default
DocumentRoot/var/www/oscommerce/logg/login.php (created a new folder logg and cut&pasted login.php into it as folder catalog had many php files)

sudo /etc/init.d/apache2 restart

but it doesnt work,still gives me the index.html page...what am i missing here?

---

### Post by superprash2003 on 2008-07-25
add a line
DirectoryIndex index.php

---

### Post by Endwin on 2008-07-25
Apache generally looks for a index.SOMETHING when you go to a directory for a website. Since you have login.php you either need to change it to index.php or create a symbolic link to login.php in that directory.

Something like: 
```
ln -s ./login.php index.php
```

---

### Post by ub007 on 2008-07-31
hi,

Tried both options,but I'm still unable to set oscommerce/catalog/login.php as the Document root

what i intend to do is when i point the browser to [http://david.surrey.ac.uk](http://david.surrey.ac.uk)  or [http://192.168.12.3](http://192.168.12.3) it should fetch me the webpage at /var/www/oscommerce/catalog/login.php  instead of the defualt index.html page......

When i tried the two options i could point to the login page instead of the catalog(previously set) but only when i type [http://david.surrey.ac.uk/oscommerce](http://david.surrey.ac.uk/oscommerce) in the browser

[http://david.surrey.ac.uk](http://david.surrey.ac.uk) still gives me the default index page...

what am i missing here

Cheers

David

---

### Post by aeiah on 2008-07-31
when you did the symbolic link did you do 
```
ln -s ./login.php index.php
```

or did you do 
```
ln -s /oscommerce/catalog/login.php index.php
``` whilst within /www/var/?

---

### Post by halitech on 2008-07-31
you could always code your index page to refresh and point to the link  you want to open

---

