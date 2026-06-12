---
title: "Where is PHPMyAdmin?"
date: 2007-07-09
forum: Programming Talk
---

### Post by ankursethi on 2007-07-09
I posted this in the wrong section (Servers and Security). I request the mod to remove this post and move the other one to this forum.

I need some help. Guys, take a look at this thread : [http://ubuntuforums.org/showthread.php?t=495767](http://ubuntuforums.org/showthread.php?t=495767)

Anybody?

---

### Post by LaRoza on 2007-07-09
> **ankursethi said:**
> I posted this in the wrong section (Servers and Security). I request the mod to remove this post and move the other one to this forum.

I need some help. Guys, take a look at this thread : [http://ubuntuforums.org/showthread.php?t=495767](http://ubuntuforums.org/showthread.php?t=495767)

Anybody?

Type this in your browser:
> 
[http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin)

Did you get anything?

PHPMyAdmin is usually not in the www folder, it is aliased. At least on my Apache server.

---

### Post by mermshaus on 2007-07-09
In my /etc/apache2/sites-available/default file, I have:

```
NameVirtualHost *
<VirtualHost *>

    ...

    Alias /phpmyadmin/ "/var/www/phpmyadmin/"
    <Directory "/var/www/phpmyadmin/">
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

```
sudo /etc/init.d/apache2 restart
```

I post this because I *think* that it's not generated automatically.

---

### Post by ankursethi on 2007-07-10
Nope, nothing. Not even after adding the virtual host.

But it works if a copy a symlink of the phpmyadmin folder to the www folder in my home directory. Well, if it works it works. Thanks for the hints :-)

---

### Post by hawzor on 2007-07-12
Hey ankursethi, PMA is not included in the LAMP stack. And it is uber-easy to set up on its own, even noobs like me can hack this from the command line, so no worries. IM if you would like the brief tutorial. We can trade services. :)

---

### Post by Ek0nomik on 2007-07-12
> **hawzor said:**
> Hey ankursethi, PMA is not included in the LAMP stack. And it is uber-easy to set up on its own, even noobs like me can hack this from the command line, so no worries. IM if you would like the brief tutorial. We can trade services. :)

Why not post on the forum so everyone can benefit?

---

