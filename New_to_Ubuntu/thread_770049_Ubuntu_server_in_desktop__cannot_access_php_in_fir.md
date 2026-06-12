---
title: "Ubuntu server in desktop : cannot access php in firefox"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by moshazat on 2008-04-27
Hi,

im using ubuntu desktop 7.10. but currently i also tried to add server function in my ubuntu...

I already install lamp in my os... and i can view my [http://localhost](http://localhost).. at the first time i tried to create test.php and access it through firefox by going to [http://localhost/test.php](http://localhost/test.php) and it loaded successfuly in my browser.

[B]But problem begin when i tried to setup static ip..

My problem is : whenever i tried to access test.php or phpmyadmin in [http://localhost](http://localhost), the firefox will popup and ask me what to do with the php file, unlike before, the firefox will access the php and show the test.php content in the browser.
[/B]
anyone can help me? im a new in this server thing and i want to create my own server inside my box, eventhough i know the risk by i do it in purpose to test it n know the server concept :) 

i hope anyone can help me with this, and sory for my english ;) ask me if u dont understand ;)

---

### Post by ad_267 on 2008-04-27
How did you install apache and php?

Do you have libapache2-mod-php5 installed?

---

### Post by moshazat on 2008-04-27
> **ad_267 said:**
> How did you install apache and php?

Do you have libapache2-mod-php5 installed?

I install apache2 and php through terminal, by following this tutorial ; [http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100")

about libapache2-mod-php5, i already checked and it says i already have the newest version ;

moshazat@moshazat-comp:~$ sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.

---

### Post by frup on 2008-04-27
Hey you are still accessing it from the same computer right? If you are what happens if for example you try [http://127.0.0.1](http://127.0.0.1)

If you are accessing from a network computer you need to type [http://hostname](http://hostname) or the computers new static ip.

---

### Post by moshazat on 2008-04-27
> **frup said:**
> Hey you are still accessing it from the same computer right? If you are what happens if for example you try [http://127.0.0.1](http://127.0.0.1)

If you are accessing from a network computer you need to type [http://hostname](http://hostname) or the computers new static ip.

Yes im accessing it in the same computer, and when try go to [http://127.0.0.1](http://127.0.0.1), it will direct me to the index where it contain my apache2-default/ directory, phpmyadmin directory and test.php..

but the problem is, when i click to access test.php, then firefox will popup and ask what to do with the test.php... normally firefox should open test.php and show everything contain in the file. How i want to fix this so that firefox can open php file, not ask me to open with other application or download it...

---

### Post by ad_267 on 2008-04-27
And it didn't do that before you tried to set up a static IP? Then what did you do to apache or php to set up the static IP?

---

### Post by moshazat on 2008-04-27
i just set the static ip at system>administration>network.. but i think thats not the problem, i hope maybe there is a solution to make firefox can read php..

---

### Post by ad_267 on 2008-04-27
It's nothing to do with firefox. The php is all interpreted by apache and then sent to your browser as plain html. The problem is that apache is not interpreting the php file before sending it first, so it is sending the php script as is.

---

### Post by moshazat on 2008-04-27
I found the solution on how to fix so that firefox can access the test.php ;

First, i will uninstall completely libapache2-mod-php5, and install it back using synaptic.

After install the libapache2-mod-php5, the i run this command ;
> 
sudo a2enmod php5

Then ;

> sudo /etc/init.d/apache2 restart

After that, i get this reply ;

> $ sudo a2enmod php5
Password:
This module is already enabled!


Thanx :)

---

### Post by moshazat on 2008-04-27
but still i cannot access the phpmyadmin, when i click the folder, then firefox ask me what to do with the phtml... is it also mean i have same problem but different extension? 

help :D

---

### Post by ad_267 on 2008-04-28
Do php files work?

Open /etc/apache2/mods-enabled/php5.conf and make sure there is a line like this that contains .phtml

```
AddType application/x-httpd-php .php .phtml .php3
```

---

### Post by moshazat on 2008-04-28
> **ad_267 said:**
> Do php files work?

Open /etc/apache2/mods-enabled/php5.conf and make sure there is a line like this that contains .phtml

```
AddType application/x-httpd-php .php .phtml .php3
```

i already did that and it still same... but then i tried some command i found in other forum, then one of the method reminds me that the phpmyadmin/ directory need to be inside the folder which also contain my index file of webpage

then i put the phpmyadmin/ directory in the localhost/phpnuke that contain all my index.htm or index.php and database, then i can access it :)

And now i already have my own server in my desktop edition and i already released it to the world wide web instead of local network ;) i test it by asking my friend that online in the ym to get into my server, and then they actually can see my webpage which is in my computer. And i realize that i already create a server ;) maybe now i already have Linux Ubuntu Gutsy Gibbon 7.10 Desktop+Server Edition :D

Thanx u very2 much :D

---

