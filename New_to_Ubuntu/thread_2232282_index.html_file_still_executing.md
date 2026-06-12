---
title: "index.html file still executing"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by joseph32 on 2014-06-30
Hi,

For some reason the index.html file that I removed from ~/var/www is still executing when I type in my IP into the browser's address bar.

I did make sure to restart apache2. I also deleted the full folder var/www/html and created it again, and the this ghost file is still executing..

---

### Post by yancek on 2014-06-30
What do you have in the /etc/apache2/httpd.conf file for Document Root?  The "~/var/www" indicates your user home directory contains a /var/www directory?

---

### Post by nerdtron on 2014-07-01
Have you tried resetting/clearing the cache on your web browser?

---

### Post by joseph32 on 2014-07-01
Thanks nerdtron, that got it..That sure was annoying. As a side note, why is this even allowed? I understand that there is proper security for cookies, history, etc., but it just seems so insecure.

---

### Post by nerdtron on 2014-07-01
Nah..it isn't really allowed. It's just a feature of modern web browsers to cache a webpage you visit so that the page will load faster the next time you visit it. It is really browser related and happens on firefox, chrome, opera and IE.

---

