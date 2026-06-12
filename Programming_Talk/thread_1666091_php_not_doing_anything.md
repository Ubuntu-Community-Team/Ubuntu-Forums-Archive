---
title: "php not doing anything"
date: 2011-01-13
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-13
ok, I have mysql, apache2, php5 installed 

running some examples at
[http://devzone.zend.com/node/view/id/625](http://devzone.zend.com/node/view/id/625)

> <html>
<head></head>
<body>

Agent: So who do you think you are, anyhow?
<br />

<?php
// print output
echo 'Neo: I am Neo, but my people call me The One.';
?>

</body>
</html> 

gives only the "Agent: So who do you think you are, anyhow?' line in the browser
I recall seeing some interactive config screen when doing the php5 install which I likely messed up and so how do you configure it?

---

### Post by sdowney717 on 2011-01-13
I have also done this

> scott@scott-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
scott@scott-desktop:~$ sudo a2enmod php5
Module php5 already enabled
scott@scott-desktop:~$ sudo /etc/init.d/apache2 force-reload
 * Reloading web server config apache2                                   [ OK ] 
scott@scott-desktop:~$ 


---

### Post by wojox on 2011-01-13
Try:

```
http://localhost
```

Your just opening the file in the first picture so it never gets parsed to the php engine.

---

### Post by sdowney717 on 2011-01-13
still gives the same return missing any php stuff

assume i dont know anything about php5
What I did was put that text example into an index.htm file in my pubic_html folder.
I dont know if that is right. I tried creating a file test.php and firefox wants to save it.

---

### Post by wojox on 2011-01-13
This is what I used to trouble shoot back when I ran Ubuntu Server [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by sdowney717 on 2011-01-13
[http://localhost/test.php](http://localhost/test.php)
that works
so I quess it is ok

---

### Post by wojox on 2011-01-13
okay, I thought you saved as index.html which is where php looks first. :)

---

### Post by sdowney717 on 2011-01-13
got it from here
Assume I know knowing about php5

[http://ubuntuforums.org/showthread.php?t=90446](http://ubuntuforums.org/showthread.php?t=90446)

you can also see if it is working by creating a php file with just
<?php phpinfo();?>
inside and load it into firefox same way.
and it gives all sorts of info

---

### Post by sdowney717 on 2011-01-13
yes, I did save it as index.htm, but it still did not return any php stuff.
only after saving as test.php then open it using

localhost/test.php did it work.

---

