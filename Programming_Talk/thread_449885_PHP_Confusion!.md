---
title: "PHP Confusion!"
date: 2007-05-20
forum: Programming Talk
---

### Post by sdmike on 2007-05-20
I have a forum which I used PHPBB2 and I want to configure it. So what editor should I use for PHP and how am I able to make changes and visually SEE what I am doing?

Future thanks,
Mike

---

### Post by pbw on 2007-05-20
vim is my editor of choice, so easy and saves alot of time compared to others. But there's many you could use.. kate, bluefish, nvu, gedit, nano (with php syntax highlighting enabled), etc etc, see what you like best.

And as for seeing the effects, just run phpbb locally to test your changes out before going live onsite. If you're unsure of your edits.

-- pbw

---

### Post by sdmike on 2007-05-20
do I just drop all of my code into var/www/ ?

---

### Post by sdmike on 2007-05-20
When I go to view my forum locally ([http://localhost/forums/](http://localhost/forums/)) I get this error "Fatal error: Call to undefined function mysql_connect() in /var/www/forums/db/mysql4.php on line 48"

---

### Post by pbw on 2007-05-20
yeah, if that is where you set your apache document root at (which is default in ubuntu i believe).

---

### Post by pbw on 2007-05-20
I'm assuming that you installed php and mysql correctly, created a database for your forum, imported and set the phpbb config to reflect that?

-- pbw

---

### Post by sdmike on 2007-05-20
So where should I put it then?

---

### Post by pbw on 2007-05-20
/var/www is default document root for ubuntu. Just make sure your mysql settings are correct and you'll be good to go.

---

### Post by sdmike on 2007-05-20
I made a phpinfo.php file and it worked there. I put my websites fodler there and it worked.

But the forum doesn't work like my websites folder.

---

### Post by pbw on 2007-05-20
Make sure your mysql is configured correctly, and your forums are connecting to your db and everything should be fine. I'm sure that's all it is.

---

### Post by kaptainlange on 2007-05-20
"Fatal error: Call to undefined function mysql_connect() in /var/www/forums/db/mysql4.php on line 48"

That suggests the mysql lib for php isn't installed.

Did you do:
```
sudo apt-get install php5-mysql
```

---

