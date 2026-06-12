---
title: "[SOLVED] localhost and phpmyadmin"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by lrigoulot on 2008-06-15
Being a total noob... Screwed up bigtime.

I am trying to make lampp server and could not access phpmyadmin so i followed some forum advice - made changes and can access it via 127.0.1.1 and it works fine but I lost my localhost.  I either get 404 or am taken to that subject in the wikipedia depending on the access method.

Sure could use some help.

Thanks,
lou

---

### Post by saj0577 on 2008-06-15
So when you type in 
[http://localhost/](http://localhost/)
what does it do.
IS it only phpmyadmin that does not work.
Have you edited your hosts file?

Saj

---

### Post by lrigoulot on 2008-06-15
if i go to [http://127.0.1.1/phpmyadmin](http://127.0.1.1/phpmyadmin) all works fine but if I try
[http://localhost/](http://localhost/) (in firefox) I am taken to the wikipedia, subject localhost.  If go to 127.0.1.1/index.php i access my site but any links referencing localhost gets me a 404.

And yes, I did try to edit my hosts file but that did not seem to work.

thanks

---

### Post by saj0577 on 2008-06-15
Whats the contents off your hosts file?

```
sudo gedit /etc/hosts

```

---

### Post by lrigoulot on 2008-06-15
127.0.0.1 site
127.0.1.1 louis-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by saj0577 on 2008-06-15
127.0.0.1	localhost

Add that to the top :)

Then 
```
sudo /etc/init.d/apache2 restart
```

Saj

---

### Post by lrigoulot on 2008-06-15
That did it!!!

Phpmyadmin works too!!

thanks,
lou

---

### Post by saj0577 on 2008-06-15
NO problem.

Please mark as thread.Thank YOu

Saj

---

### Post by lrigoulot on 2008-06-15
How do I do this?

---

### Post by saj0577 on 2008-06-15
Thread Tools at the top on top of your first post.

Mark As Solved.

Saj

---

