---
title: "web server problem"
date: 2008-07-16
forum: Programming Talk
---

### Post by floryn on 2008-07-16
Hi...

i decided to create my own server were to host a couple of websites... I managed to get the server working, i installed the script i want my site to run on, but i`m getting an error now:

```

Warning: require() [function.require]: SAFE MODE Restriction in effect. The script whose uid is 10004 is not allowed to access /var/www/web10/web/smarty/Smarty.class.php owned by uid 0 in /var/www/web10/web/functions.php on line 17

Warning: require(/var/www/web10/web/smarty/Smarty.class.php) [function.require]: failed to open stream: Inappropriate ioctl for device in /var/www/web10/web/functions.php on line 17

Warning: require() [function.require]: SAFE MODE Restriction in effect. The script whose uid is 10004 is not allowed to access /var/www/web10/web/smarty/Smarty.class.php owned by uid 0 in /var/www/web10/web/functions.php on line 17

Warning: require(/var/www/web10/web/smarty/Smarty.class.php) [function.require]: failed to open stream: Inappropriate ioctl for device in /var/www/web10/web/functions.php on line 17

Fatal error: require() [function.require]: Failed opening required '/var/www/web10/web/smarty/Smarty.class.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/web10/web/functions.php on line 17

```


Can anyone help me solve this.... i`m kind of a beginer in, so can you please explain me hw to solve this ...

Thanks in advance

---

### Post by scragar on 2008-07-16
```
sudo gedit /etc/php5/apache2/php.ini
```
find "safemode = on"
turn it off.
save and restart apache to be sure:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by pmasiar on 2008-07-16
> **floryn said:**
> i decided to create my own server were to host a couple of websites...i`m kind of a beginer 

Seems like you want to **configure** a web server, not to write your own? Apache? No offense, but read "How to ask questions" first (in my sig).

There is server/administration forum, better experts for your question, ask mods post to be moved there.

---

### Post by floryn on 2008-07-16
thanks for your replys .. i managed to solve the problem it was a permision problem...

---

