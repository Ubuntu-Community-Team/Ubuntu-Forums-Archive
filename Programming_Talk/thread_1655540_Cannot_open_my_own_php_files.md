---
title: "Cannot open my own php files"
date: 2010-12-29
forum: Programming Talk
---

### Post by burton247 on 2010-12-29
I have been messing around with some php but every time I try and view the page using firefox/chrome it just downloads the files. I have php installed along with apache. Can anyone help sort this issue out as it makes it very hard to develop 

Thanks

---

### Post by secondstage on 2010-12-29
Have you installed libapache2-mod-php5?
```
sudo apt-get install libapache2-mod-php5
```

After doing so, did you restart Apache?
```
sudo service apache2 restart
```

---

### Post by ziekfiguur on 2010-12-30
Are your php files located in `/var/www/' and are you opening with [http://localhost/yourfile.php](http://localhost/yourfile.php) as url?
If you try to open them with file:///var/www/yourfile.php they are not handled by apache.

---

### Post by burton247 on 2010-12-30
Thanks, didn't realise I had to put my files in var/www I'm used to being able to load them from anywhere in Windows

Thanks again

---

### Post by ziekfiguur on 2010-12-30
You don't *have* to have your files in /var/www, but by default apache is configured to only allow access to /var/www (and /usr/share/doc, but only from localhost)
You can change the settings in a file somewhere in /etc/apache2

---

