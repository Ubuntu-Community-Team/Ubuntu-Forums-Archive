---
title: "PHP Permission Deneid Error"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by djvince23 on 2008-09-22
Hi guys! i have a problem in running php file on my ubuntu pc, my web folder is set to its default, /var/www/ once i create a php file and save it on the web root folder it woks fine, but once i place a php file or a set of php files inside it that is created on windows, it cannot be run it just displays permission denied error... how can i fix this problem? or i am just going to accept that web pages created on windows cannot be run on ubuntus apache web server!!!:)

---

### Post by Jimmyfj on 2008-09-22
Who is set to be the owner of your /var/www-folder? If root is the owner of the folder there you have the answer. To change owner of the folder run this command in a terminal:

```
sudo chown -R USERNAME:USERNAME /var/www
```

Where USERNAME is the name you use for login.

---

