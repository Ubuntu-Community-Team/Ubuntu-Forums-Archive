---
title: "How to search for a file in Hardy Heron"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-06
I am trying to find the php.ini file that seems to be causing so much trouble (I can`t continue installing Joomla into the Hardy Heron, until I do `something` to this file). Now, I am unclear if it is in the server directory, or the Joomla directory, but what I`d like to know: how does one search for files in Linux? I used the file tracker, and the `search`  in my file browser, but did not come up with it, and I`m pretty sure it`s there somewhere. thanks in advance :)

---

### Post by stephanvaningen on 2008-11-06
You can:
 ```
find / -name "php.ini"
```
(Or sudo it to be sure you have rights in all places where you are searching)

---

### Post by hyper_ch on 2008-11-06
open a terminal, run:
```

locate php.ini

```

or browse to
/etc/php5/apache2/

If you have installed php4 then it's not the php5 folder obviously and if you don't use php as apache module but as cgi then you'd go to "cgi" instead of "apache2" and if you use apache 1.3 then you have to adjust accordingly.

---

### Post by Lakeside on 2008-11-06
> **hyper_ch said:**
> if you don't use php as apache module but as cgi then you'd go to "cgi" instead of "apache2" Hmmm, I should have just asked YOU where this php.ini was lol (but it was good how to practice looking for a file anyway). There was a php.ini in both the cgi and the apache2 directory. Not sure how to see if php is module or cgi though.  I installed it from the synaptec package manager though, if that helps :) And does it matter which one I use, aren`t they both the same anyway, and I have to put it in var/www after it`s modified.

---

### Post by hyper_ch on 2008-11-07
they work differently...

ru

```

sudo a2enmod php5

```

and it will then be run as module.

---

### Post by Lakeside on 2008-11-07
> **hyper_ch said:**
> they work differently...

ru

[code]

and it will then be run as module.
And...that`s what I want? Remember, still early days for me lol

---

### Post by hyper_ch on 2008-11-07
you have to konw what you want - but most people run it as module.

---

