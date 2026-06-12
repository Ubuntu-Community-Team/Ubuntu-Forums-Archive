---
title: "Help! LAMP installation problem,"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by nommo777 on 2008-08-04
Greetings to all..I am a complete noob (yes, i know this phrase has been done to death..pls bear with me.:) )today, i successfully installed ubuntu on my system, and proceeded to install apache, mysql and php5..and they all INSTALLED fine..and are working together in perfect harmony.then i proceeded too download and install phpmyadmin and it seems that the install was a success, but my problem is that i cannot access it through my browser, eg:localhost/phpmyadmin, because it has been installed somewhere else..can anyone tell me whats going on here..what is the XP 'Program Files ' equivalent in ubuntu, if any?? i am having a hard time with this FileSystemm thing.. Pls help me out guys..

---

### Post by boralyl on 2008-08-04
I just installed it via apt-get and it gets installed in /usr/local/phpmyadmin/

---

### Post by lapubell on 2008-08-04
another good tip:  if you have synaptic installed, find the package in synaptic and click it to highlight it.  Now click the properties button up top.  Then click the "Installed Files" tab and you should see every file that it installed and its directory structure.

This has helped me find many weird named linux files.

As far as your XP equalivent "Program files", linux doesn't do that.  /usr/bin is the default folder for all your executable files (for the most part), /etc is the fold for all your config files, /usr/share is where a lot of stuff goes, like fonts and icon sets and whatnot...

---

### Post by jamesrfla on 2008-08-04
I use webmin. You can get it by doing this command in terminal. ```
sudo apt-get install webmin
``` To access it type localhost:10000. I think phpmyadmin uses something like webmin like localhost:2000

---

### Post by nommo777 on 2008-08-04
thanks alot guys.. let me try it out..

---

### Post by jamesrfla on 2008-08-04
> **jamesrfla said:**
> I use webmin. You can get it by doing this command in terminal. ```
sudo apt-get install webmin
``` To access it type localhost:10000. I think phpmyadmin uses something like webmin like localhost:2000

I am sorry my information is incorrect. I wasn't sure what phpmyadmin really was. I thought it was like a web administration tool. The guys say that to access phpmyadmin you need to type in [http://localhost/phpmyadmin](http://localhost/phpmyadmin) Good luck!!

---

