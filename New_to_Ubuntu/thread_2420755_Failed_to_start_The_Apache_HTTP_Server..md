---
title: "Failed to start The Apache HTTP Server."
date: 2019-06-10
forum: New to Ubuntu
---

### Post by grenic on 2019-06-10
Good afternoon,

Is someone able to please help me fix my Apache web server.

[IMG]https://cdn1.imggmi.com/uploads/2019/6/10/fb555cd94fb3fe3a5959e3d3dad71729-full.png[/IMG].

I tried to uninstall Apache and deleted a few files which you can see are missing above. What is the easiest way to fix this?

---

### Post by dino99 on 2019-06-10
Have you read that related thread ?  [https://ubuntuforums.org/showthread.php?t=2420608](https://ubuntuforums.org/showthread.php?t=2420608)

---

### Post by SeijiSensei on 2019-06-10
First, backup whatever configuration files you created in /sites-available/, then reinstall Apache.

Running "apachectl configtest" will diagnose any errors in those configuration files. Also take a look at the log files in /var/log/apache2, particularly error.log.

---

### Post by grenic on 2019-06-20
I did follow the article as listed in your comments. I had apache2 installed, tried to uninstall it which I seem to have done succesfully. I have tried reinstalling apache2 of which has started up with an error.

[IMG]https://i.imgur.com/xXR8w1y.png[/IMG]

---

