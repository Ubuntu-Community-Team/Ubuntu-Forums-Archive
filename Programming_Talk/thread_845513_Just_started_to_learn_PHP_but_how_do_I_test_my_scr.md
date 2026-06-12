---
title: "Just started to learn PHP but how do I test my scripts without having to upload them?"
date: 2008-06-30
forum: Programming Talk
---

### Post by mattgaunt on 2008-06-30
Hey guys

Im new to scripting php, I just joined a project that is using it heavily at the moment, anyway I wanted to just start from the ground up and came across the first hurdle when just trying to run a php script.

So what do you guys think is the easiest option to start without needing to upload stuff to a server

also on a side note, any good tools that im missing out for html/php coding on linux and for trnasferring file to and from ftp?

Cheers for any help

Gaunt

---

### Post by LaRoza on 2008-06-30
A local server is best for development.

---

### Post by mattgaunt on 2008-06-30
cheer LaRoza I just had a go at getting it installed and got a test page appearing BUT how do I set it up so I can freely edit file in the /var/www/ directory without needing to be route? I know this is probably a stupid question but none of the how-to's i've read really mention anything regarding setting permissions

Cheers for the help

Gaunt

---

### Post by mattgaunt on 2008-06-30
Ignore me I think I managed to find a link that'll help me on this hopefully

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Gaunt

---

### Post by suprfish on 2008-06-30
> **mattgaunt said:**
> cheer LaRoza I just had a go at getting it installed and got a test page appearing BUT how do I set it up so I can freely edit file in the /var/www/ directory without needing to be route? I know this is probably a stupid question but none of the how-to's i've read really mention anything regarding setting permissions

Cheers for the help

Gaunt

```

sudo chown -R username /var/www/

```

EDIT: Found this very friendly tutorial (though it is for 7.04 it'll work fine for 8.04): [http://www.lullabot.com/node/289/play](http://www.lullabot.com/node/289/play)

---

### Post by slavik on 2008-06-30
> **suprfish said:**
> ```

sudo chown -R username /var/www/

```

EDIT: Found this very friendly tutorial (though it is for 7.04 it'll work fine for 8.04): [http://www.lullabot.com/node/289/play](http://www.lullabot.com/node/289/play)
I'd advice against this method.

sudo a2enmod userdir

then create a dir in your home called "public_html" and put your php stuff there (I am assuming you have all the proper modules installed). then visit the site at [http://localhost/~username/index.php](http://localhost/~username/index.php)

username is your username of course. :)

---

### Post by mattgaunt on 2008-07-03
cheers for all the help guys

---

