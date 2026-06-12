---
title: "Setting gallery2 as default web page"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by oraldlight on 2008-05-08
I once had Gallery2 set up and working. Browse to my url and user would go to Gallery2 home page. Then I wrecked it and rememberd how little I documented to make it work. Now I have rebuilt the server from scratch. 
Ubuntu server 8.04, 2gh, 3gb ram, no problem.

Apache2 works - [http://localhost/](http://localhost/) shows me the "it works!" message from /var/www/index.html.

Gallery2 installed and config'd. [http://localhost/gallery2](http://localhost/gallery2) takes me to gallery2 home page.

For the life of me, I can not find what/where to get this //localhost/gallery2/main.php to be the 'default' page for users when they browse to my url. I'm drowning in Apache and Gallery FAQ's and forums. Anyone got a quick and simple "point this file there" or "edit this file with that info" like answer?

---

### Post by spiderbatdad on 2008-05-08
should just be a matter of putting the php file in the appropriate directory. and naming it gallery2.php.  Navigate to [http://localhost/gallery2.php](http://localhost/gallery2.php)

Ah. I see what your after I think. If you want it to default to that page without the .php tag,  I think you will need a redirect in sites-available/your-site under the default directory.

---

### Post by quelx on 2008-05-08
```
sudo nano -w /etc/apache2/sites-available/default
```

look for 
DocumentRoot /var/www/default

and change it to
DocumentRoot /usr/share/gallery2

restart apache
```
sudo /etc/init.d/apache2 reload
```

---

### Post by oraldlight on 2008-05-08
BINGO!!!!  Thank you spiderbatdad and quelx. Exactly the one thing I could not sort out. Now users are directed to gallery2 as the default landing page for my url.

Now I need to revisit my notes, create a clean how-to and find a place to post.

---

