---
title: "[SOLVED] how to get PHP and MySQL up and running with apache in linux"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by littletinman on 2008-06-02
OK, i want to dig more into the language of computing and I'm starting out with PHP and MySQL (I've already had experience with HTML). I'm using Larry Ullman's Quick pro guide, PHP and MySQL for dynamic websites, and i need to know how to install PHP, MySQL, and Apache in Linux (Ubuntu and Kubuntu) so that they work together. Help please?


LTM

---

### Post by spiderbatdad on 2008-06-02
Community docs:[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

---

### Post by Joeb454 on 2008-06-02
If you have a spare machine you can install Ubuntu Server on it (as one of the links Spiderbatdad provided says). This is how I run one of my websites :)

It's very simple, and if you're not confident with the CLI you can install a GUI anyway :)

---

### Post by mevets on 2008-06-02
The quickest way to get those up and running is to run:
```

sudo apt-get install apache2 php5 mysql-server

```
You may want to install addition packages such as phpmyadmin. Either way, I would also look at the docs posted.

---

### Post by R3VAMP3D on 2008-06-02
If you just want to quickly create a local environment for web development in PHP, installing php5, php5-mysql, mysql-server, and apache2 mostly covers it (See post above). Afterwards you'd probably want to setup the userdir module so that you can use a folder in your home directory rather than deal with symlinks and other hairy stuff.
```
sudo cp /etc/apache2/mods-available/userdir.{conf,load} /etc/apache2/mods-enabled/
``` would enable the user directories, in which you'd just create a folder called public_html and visit [http://127.0.0.1/~yourusername]("http://127.0.0.1/%7Eyourusername"). You'd have to google up on extended mysql setup though.

---

### Post by littletinman on 2008-06-02
thanks guys. this is great. Only one prob. How do i find the directories and the programs in the menu or home folder?

---

### Post by mevets on 2008-06-02
I dont exactly understand what you mean, but if you want to know how to start apache run

sudo /etc/init.d/apache2 start

You wont need to though, its started for you after you install and starts after each reboot automatically. /var/www/ is the directory apache2 serves by default.

---

### Post by littletinman on 2008-06-02
thanks man, ok, so hopefully i can be able to start programming right away. Do you know any places to go if i get stuck? my guide is geared toward a windows or mac install.

---

### Post by Joeb454 on 2008-06-02
You should also note that Apache serves index.html as the default HTML page if one isn't specified, not the home.html that IIS serves :)

---

### Post by durand on 2008-06-02
You could ask in the programming section of this forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Joeb454 on 2008-06-02
Actually I think the OP may get a little better response in the [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") section :)

---

### Post by kwacka on 2008-06-02
A step-by-step installation guide is : 'Installing LAMP On Ubuntu For Newbies'
at: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by littletinman on 2008-06-02
where is the place where i put my "first.php" file so that when i type in "http://localhost/first.php" it shows up in the browser?

---

### Post by mevets on 2008-06-02
/var/www/

---

### Post by littletinman on 2008-06-03
well since it's in the root fiel system. how to i move a file from the home folder into this folder, and will it still let me edit the file?

---

### Post by WorldTripping on 2008-06-03
Personally, and as it's a test machine and not a production enviroment, I 'chmod' and 'chown' the /var/www

Some people would (will) probably disagree with this method.

But I don't care, it's my laptop.. :)

---

### Post by WorldTripping on 2008-06-03
> **mevets said:**
> The quickest way to get those up and running is to run:
```

sudo apt-get install apache2 php5 mysql-server

```
You may want to install addition packages such as phpmyadmin. Either way, I would also look at the docs posted.

You could also use ```
sudo taskel install lamp-server
``` from the command line.

Or even use synaptic, 'Edit' menu, 'Mark Packages By Task', then select LAMP, you can even install Samba etc. from here.

That's the way I do it.

---

### Post by littletinman on 2008-06-03
so what do i put itno the terminal?

---

### Post by WorldTripping on 2008-06-03
```
sudo chmod 777 /var/www
sudo chown username:username /var/www
```

Where username is your username.

Again the rights '777' are very loose, and allow for anyone to read write and execute the file.

Again, others will argue that these are too loose. I would only use these in a test enviroment, not a live server.

There is a good chmod tutorial here:
[http://www.ss64.com/bash/chmod.html]("http://www.ss64.com/bash/chmod.html")

---

### Post by Joeb454 on 2008-06-03
I would do ```
mkdir ~/web
sudo ln -s /var/www/ ~/web
```

---

### Post by littletinman on 2008-06-03
thanks guys. I'm now doing programming away. thanks for your help. it is very apreciated!!!!!!!!!!!

---

