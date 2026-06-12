---
title: "Have installed Apache2 successfully but get 404 error on PHP files"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by Andy_Pearson on 2014-04-08
I want to set up a local dev environment on my laptop, which is running 12.04. 

I followed the instructions [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") and apache2 works (ie it shows me the 'it works' screen at /localhost. However when I follow the instructions and upload a test.php file I just get a 404 page. 

Any suggestions?

---

### Post by Kirboosy on 2014-04-09
Welcome to the forums! :D

Can you run the following command and post the output back here?
```
ll /usr/var/www
```
I feel that you might have a permissions issue.

Hope that helps!
~Caboose

---

### Post by neil8 on 2014-04-09
Andy, when I set up my server I was scratching my head for a few hours until I ran a port scan against it and found all ports were shut (I got the 'It works' page though). I opened up the firewall and everything was fine for me. May be worth a check

---

