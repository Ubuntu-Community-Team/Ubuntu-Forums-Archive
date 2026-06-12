---
title: "webfolder for each user on web server"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by dd86 on 2008-06-25
hey,
I'm quite new to linux, for a few days ago er installed my first ubuntu server 8.04, and it took some time to configure bot now it's done and it up running. :)

my question is, is it possible to give each user there own web/homepage folder, and to access it in the browser.

right now when I enter my ip in the browser it looks in /var/www ant that's fine but can I make a user and a web folder for this user like /home/newuser/www and make this users web folder accessible in my browser like newuser.myip or myip~newuser or something like that?

---

### Post by Xiong Chiamiov on 2008-06-27
You make make softlinks between the two, like so:
```

sudo ln -s /home/newuser /var/www/newuser

```
This will make a fake folder in /var/www called newuser that will take you (transparently) to /home/newuser.  Change the second line part to /var/www/~newuser if you want a tilde; subdomains take more work with rewriting rules in Apache.

---

### Post by superprash2003 on 2008-06-27
or you could try virtual hosts in apache..

---

### Post by hyper_ch on 2008-06-27
[http://httpd.apache.org/docs/2.0/mod/mod_userdir.html](http://httpd.apache.org/docs/2.0/mod/mod_userdir.html)

---

