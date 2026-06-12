---
title: "Cannot find LAMP"
date: 2014-10-28
forum: New to Ubuntu
---

### Post by flex567 on 2014-10-28
I just installed LAMP and I ran it when the instalation was over. But now I don't know how to find it(lamp) and run it. I cannot find it with dash and ```
locate lamp
``` returns too many results?

---

### Post by pissedoffdude on 2014-10-28
What do you mean by LAMP?  Are you talking about the LAMP stack?  Those are individual components, usually (L)inux (A)pache (M)ySQL (P)HP

---

### Post by flex567 on 2014-10-28
yes, but how can I run main window(control panel), from which I can go into phpmyadmin, turn on mySql...

---

### Post by yancek on 2014-10-28
I don't know what 'main window' you are referring to, you don't need anything else to turn on mysql.  If you do want phpmyadmin, you need to install it separately as it is not part of LAMP, see the link below:

[https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04)

---

### Post by mastablasta on 2014-10-29
for that you need to install a server GUI.

if you are used to cPanel have a look at zPanel. Otherwise there are Zentyal, Ajenti, Webmin and a few others available.

but you do not need any of those if you installed LAMP stack on a desktop. just install the components. apache (your website) should be reachable via [http://localhost](http://localhost), while data is otherwise in /var/www

what are you trying to do? if you are just using this for some testing or let's say to develop a website I found it easier to use Virtualbox and ready images for that found at turnkey Linux or Bitnami stack. 

but if you want to setup your own webserver then I suggest you dig into command line resources and learn at least some basics. then if you are a GUI guy like me just install one of the web GUI I mentioned earlier. for a webserver I suggest you give Ajenti a try.

---

### Post by nerdtron on 2014-10-29
> **flex567 said:**
> I just installed LAMP and I ran it when the instalation was over. But now I don't know how to find it(lamp) and run it. I cannot find it with dash and ```
locate lamp
``` returns too many results?

What command did you use to install the LAMP stack?

> yes, but how can I run main window(control panel), from which I can go into phpmyadmin, turn on mySql... 
Unless your install included phpmyadmin, you can't have a webgui for it.

Services will run by default but if your to stop/start them, you can follow the convention:
```
sudo service mysql start
sudo service apache2 start
```

---

### Post by flex567 on 2014-10-29
phpmyadmin is installed in LAMP.  There is a control panel.

> If you installed it as root (using sudo  or the CLI installation), you will need to go to the destination  directory that you configured during the installation process and run  this command:
  sudo ./manager-linux*.run

---

### Post by yancek on 2014-10-29
> phpmyadmin is installed in LAMP

I'm not sure if you are still having a problem and if so what it is but phyMyAdmin is not part of LAMP and needs to be installed separately.  It's just a GUI interface for php/mysql and how to install it is shown in the link posted above as well as the link posted below:

[https://help.ubuntu.com/10.04/serverguide/phpmyadmin.html](https://help.ubuntu.com/10.04/serverguide/phpmyadmin.html)

---

### Post by flex567 on 2014-10-30
What is the difference between GUI interface for php/mysql and phyMyAdmin?

---

### Post by mcduck on 2014-10-30
nothing? As stated above, phpmyadmin is a graphical interface for MySQL (accessible through your browser). 

It's not a standalone graphical program you could launch from your desktop menus, though, and it also doesn't deal with any other server settings than your MySQL databases. If you wanted something that gives access to all your web server stuff, then follow mastabla's advice and install zpanel, for example. However having such tool isn't requred, all your server applications will work happily without, it's just a question how you prefer configuring things. (my recommendation would be to just read through Ubuntu's official server guide and do the configurations you need manually, you'll have much better idea about what's going on your server that way)

---

