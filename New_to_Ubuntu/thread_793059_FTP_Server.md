---
title: "FTP Server?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by GPearce on 2008-05-13
Hi There
I've installed Ubuntu Desktop 8.04 onto a spare pc, with a view to using it as a home deployment system to test some of my coding. I've got apache, php mysql and all that playing perfectly, and I've got SSH from the main laptop (when I'm done, the old laptop won't be used too much through its own desktop), but I can't see how to setup ftp. All I want is a single login to my /var/www folder that I can use to move files to and fro - is this possible? If so, how, in dummies terms? :p

Thanks!!! ;D

---

### Post by Cypher on 2008-05-13
You can install a FTP server with
```

sudo apt-get install proftpd

```
You would login using your regular username/password and that will put you into your home directory and not the /var/www directory. The user that has access to the /var/www directory isn't usually allowed to login.

You could use a "user directory" for your testing, by doing
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 restart

```
Then create the userdirectory in your home directory with
```

cd ~
mkdir public_html

```
Put your files in there and access this directory through the browser with http://<machine name/ip/localhost>/~<username>

---

### Post by GPearce on 2008-05-13
> **Cypher said:**
> You can install a FTP server with
```

sudo apt-get install proftpd

```
You would login using your regular username/password and that will put you into your home directory and not the /var/www directory. The user that has access to the /var/www directory isn't usually allowed to login.

You could use a "user directory" for your testing, by doing
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 restart

```
Then create the userdirectory in your home directory with
```

cd ~
mkdir public_html

```
Put your files in there and access this directory through the browser with http://<machine name/ip/localhost>/~<username>
Okay, is there any way just to set apache to look in /home/george/public_html ? Nobody else will be using the computer (:

Thanks!

---

### Post by Cypher on 2008-05-13
Sure..the file **/etc/apache2/sites-available/default** has the "DocumentRoot /var/www" line. You can change that to "DocumentRoot /home/george/public_html"..

---

### Post by GPearce on 2008-05-13
Thank you so much. It's all working perfectly now. I much appreciate your help.

---

### Post by hyper_ch on 2008-05-13
I'd just installed openssh-server and used ssh/sshfs/scp for doing that... I would not have setup a ftp server.

---

