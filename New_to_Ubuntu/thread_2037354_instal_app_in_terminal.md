---
title: "instal app in terminal"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by itzAltaf on 2012-08-04
I am brand new to ubuntu :)
i installed ubuntu on virtual machine
i want to instal xampp/lampp on it
i downloaded it from official site of apache..the package is in tar.gz  format
i have saved this on desktop
now i want to know whioch command should i give to Terminal to instal this package
thanks

---

### Post by Bufeu on 2012-08-04
Unpack the .tar.gz-file, and you've got an executable installer to run.
[http://www.devshed.com/c/a/Administration/How-to-Install-XAMPP-on-Ubuntu-Linux/](http://www.devshed.com/c/a/Administration/How-to-Install-XAMPP-on-Ubuntu-Linux/)
[http://daksh21ubuntu.blogspot.se/2012/01/how-to-install-xampp-in-ubuntu.html](http://daksh21ubuntu.blogspot.se/2012/01/how-to-install-xampp-in-ubuntu.html)

---

### Post by thek3nger on 2012-08-04
You can also use a PPA

```

sudo add-apt-repository ppa:upubuntu-com/xampp
sudo apt-get update
sudo apt-get install xampp

```

---

### Post by itzAltaf on 2012-08-04
when i put this command in terminal it gives me error
sudo tar xvfz xampp-linux-1.8.0.tar.gz -C /opt
i have saved the xampp file on my desktop

plz help me


[ATTACH]222235[/ATTACH]

---

### Post by itzAltaf on 2012-08-04
guys i have never used linux...plz help me from basic point of view

---

### Post by itzAltaf on 2012-08-04
> **thek3nger said:**
> You can also use a PPA

```

sudo add-apt-repository ppa:upubuntu-com/xampp
sudo apt-get update
sudo apt-get install xampp

```


bro wot is PPA...and how to use

---

### Post by steeldriver on 2012-08-04
n/m - see Cheesemill's instructions below[]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Cheesemill on 2012-08-04
Ignore all of the instructions above for installing XAMP, and also there is rarely any need for downloading files from websites like you have done with Apache.
You should just install the default LAMP stack using the standard Ubuntu installation method. Just open a terminal and type:
```
sudo apt-get install lamp-server^
```This will install Apache, MySQL and PHP for you from the standard Ubuntu repositories.

---

### Post by itzAltaf on 2012-08-04
all process done
now plz tell me where to put/save php script file to check the local host

---

### Post by itzAltaf on 2012-08-04
I am unable to save copy paste any file in FILE SYSTEM folder in my OS...plz help me how to do this

---

### Post by Bufeu on 2012-08-04
> **itzAltaf said:**
> when i put this command in terminal it gives me error
sudo tar xvfz xampp-linux-1.8.0.tar.gz -C /opt
i have saved the xampp file on my desktop

plz help me


[ATTACH]222235[/ATTACH]
You must *cd* to your Desktop. Should work with *cd ~/Desktop* or just *cd Desktop*, then run the command again.

---

### Post by itzAltaf on 2012-08-04
> **Bufeu said:**
> You must *cd* to your Desktop. Should work with *cd ~/Desktop* or just *cd Desktop*, then run the command again.


Man i have done with ur method...but now if i open local host xampp/lampp server page doesnot open

---

### Post by Bufeu on 2012-08-04
> **itzAltaf said:**
> Man i have done with ur method...but now if i open local host xampp/lampp server page doesnot openWell, on the screenshot you took, your current directory was **~**, not **~/Desktop**.

---

### Post by itzAltaf on 2012-08-04
and plz tell me how to take ownership of file system

---

### Post by itzAltaf on 2012-08-04
> **Bufeu said:**
> Well, on the screenshot you took, your current directory was **~**, not **~/Desktop**.


fresh screen shot
now plz tell me how to take owner ship of file system

[ATTACH]222249[/ATTACH]

---

### Post by gandaran on 2012-08-04
[http://setupguides.blogspot.pt/2012/04/install-lamp-in-ubuntu-1204.html](http://setupguides.blogspot.pt/2012/04/install-lamp-in-ubuntu-1204.html)

---

### Post by itzAltaf on 2012-08-04
> **gandaran said:**
> [http://setupguides.blogspot.pt/2012/04/install-lamp-in-ubuntu-1204.html](http://setupguides.blogspot.pt/2012/04/install-lamp-in-ubuntu-1204.html)


i have installled xampp.....plz tell me how to acces xampp server
from [http://localhost](http://localhost)   its shows something else
where is control panel???

---

### Post by Bufeu on 2012-08-04
> **itzAltaf said:**
> fresh screen shot
now plz tell me how to take owner ship of file system

[ATTACH]222249[/ATTACH]```
sudo usermod -a -G www-data <your user name>
sudo chgrp -R www-data /var/www
sudo chmod -R g+w /var/www

```
Log out and log in again... should work.

---

### Post by Bufeu on 2012-08-04
> **itzAltaf said:**
> i have installled xampp.....plz tell me how to acces xampp server
from [http://localhost](http://localhost)   its shows something else
where is control panel???[http://freshtutorial.com/add-gui-xampp-control-panel-ubuntu/](http://freshtutorial.com/add-gui-xampp-control-panel-ubuntu/)

---

### Post by gandaran on 2012-08-04
> **itzAltaf said:**
> i have installled xampp.....plz tell me how to acces xampp server
from [http://localhost](http://localhost)   its shows something else
where is control panel???
open web browser with right IP
[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp)

---

### Post by gandaran on 2012-08-04
> **Bufeu said:**
> [http://freshtutorial.com/add-gui-xampp-control-panel-ubuntu/](http://freshtutorial.com/add-gui-xampp-control-panel-ubuntu/)
this control panel is for xampp, I believe OP installed lamp server from software center?

---

### Post by Bufeu on 2012-08-04
> **gandaran said:**
> this control panel is for xampp, I believe OP installed lamp server from software center?Ah, my bad. :)

---

### Post by itzAltaf on 2012-08-04
> **Bufeu said:**
> ```
sudo usermod -a -G www-data <your user name>
sudo chgrp -R www-data /var/www
sudo chmod -R g+w /var/www

```Log out and log in again... should work.


thanks man...this is a great forum
thumbs up

---

### Post by itzAltaf on 2012-08-04
> **Cheesemill said:**
> Ignore all of the instructions above for installing XAMP, and also there is rarely any need for downloading files from websites like you have done with Apache.
You should just install the default LAMP stack using the standard Ubuntu installation method. Just open a terminal and type:
```
sudo apt-get install lamp-server^
```This will install Apache, MySQL and PHP for you from the standard Ubuntu repositories.

> **gandaran said:**
> this control panel is for xampp, I believe OP installed lamp server from software center?

gandaran bro i followed the method mention by cheesmill
and then i also installed xampp downloaded form the apache site

Now plz guide me to access xampp server as i acces in windows

---

### Post by Scott Harrison on 2012-08-04
If you're new to Ubuntu, I really suggest you find the time to read [this eBook]("https://launchpad.net/ubuntu-manual/precise/precise-release/+download/Getting%20Started%20with%20Ubuntu%2012.04.pdf") from cover to cover. It will fill you in on the details you need to know how Ubuntu works. Especially if you're used to a Windows environment.

---

### Post by gandaran on 2012-08-05
> **itzAltaf said:**
> gandaran bro i followed the method mention by cheesmill
and then i also installed xampp downloaded form the apache site

Now plz guide me to access xampp server as i acces in windows
sorry for the late reply, look it's not good to have both installed as it may conflict if both apache servers are running, I recommend you choose what you really want and remove the other! xampp is easier to configure but is used mainly for local testing, or if you want the real thing then it's the lampp server from software center!
when following instructions ensure they are the correct ones for xampp or ubuntu lampp. 
this one should get you running xampp
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

