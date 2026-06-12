---
title: "Trouble with PHP"
date: 2009-03-20
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-03-20
what do i need to run php on my machine?

i have apache installed and php5 and all that stuff, but when i try and open a .php file in firefox it asks me what to open it with...

---

### Post by hastur on 2009-03-21
hi,

you need to open the file "trough the apache server" :
- the server files are located in /var/www/
- you can access your http server at "http://localhost/"

try this adress in firefox, apache should have put some html test file : if you see a list of file, your server is not running (launch it in services menu) otherwise you should see a html page telling you the server is running.

now you can open a php file with firefox using apache server, for example :
/var/www/test/index.php
will be accessible at :
[http://localhost/test/index.php](http://localhost/test/index.php)

---

### Post by Tibuda on 2009-03-21
Have you installed [libapache2-mod-php5]("apt:libapache2-mod-php5") package?

Also make sure you are trying to open the files by the server in [http://localhost](http://localhost), as suggested by hastur. You can also enable the userdir module, so files under /home/$USER/public_html are available in http://localhost/~$USER. To enable it, run this in the terminal:
```
sudo a2enmod userdir
```
And restart the apache service
```
sudo service apache2 restart
```

---

### Post by jimi_hendrix on 2009-03-21
i am using xampp btw

i rebooted lamp, after making sure that module is installed and php5 is installed, no difference

---

### Post by s.fox on 2009-03-21
Hi,

I just set up XAMPP following [this]("http://ubuntuforums.org/showthread.php?t=223410") guide.  You need to be using localhost.

Hope the link helps you out.

---

### Post by jimi_hendrix on 2009-03-21
fixed the problem

after i unistalled apache, the process was still running, so xampp apache didnt start

---

