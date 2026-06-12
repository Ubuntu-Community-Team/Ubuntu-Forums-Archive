---
title: "Problem installing Xampp"
date: 2013-10-19
forum: Programming Talk
---

### Post by ML7rcEx on 2013-10-19
I am runnng Ubuntu 13.10 and wanted to get started with PHP. So i downloaded the file xampp-linux-1.8.2-2-installer.run
I then opened a terminal and as root went to my Downloads folder and typed: chmod +x xampp-linux-1.8.2-2-installer.run
Finally, still in a terminal and as root i typed: ./xampp-linux-1.8.2-2-installer.run

Could someone please tell me where i have gone wrong trying to install xampp.

---

### Post by ML7rcEx on 2013-10-20
Oh the fool that i am, lol. Was trying to install wrong version of Xampp on Ubuntu 13.10. Xampp-linux-x64-1.8.3-1-installer.run installed like a dream and without anyone's help!

---

### Post by Lars Noodén on 2013-10-20
Welcome.  

If you're running Linux and not Windows on your machine you might want to look at LAMP instead.  

Like all other packages (and metapackages) on Ubuntu it is available in the package repository and can be installed by a click or two.  Look in the Software Center or Synaptic if you want the graphical installer.  If you appreciate the shell, then you can use apt.

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Using the package manager will save you a lot of hassle and headache.  Among other things it handles dependencies and updates for you *automatically* so you won't be stuck running apps with known security holes or spend a lot of work chasing package statuses.  Installing from the XAMPP site, you will have to do all that manually, including getting notified of an update.  Further XAMPP puts things in the wrong places, so it will be harder to get help and in at least one case, installs a redundant app that conflicts with what is already installed on the system.  

Try using the package manager, if you are on Ubuntu, you'll like it.

---

### Post by ML7rcEx on 2013-10-20
Alas, i have already installed xampp-linux-x64-1.8.3-1-installer.run but will have a look all the same. Thanks Lars

---

### Post by Lars Noodén on 2013-10-20
Ok.  The XAMPP site ought to come with a warning label. ;)  Use it for a while.  But consider revisiting the question when it is time to add modules (to Apache2 or PHP) or time to update.  

Some people have called the package management system, Debian/Ubuntu's in particular, the best thing that Linux has contributed to computing.  I would tend to agree with them on that.

---

### Post by ML7rcEx on 2013-10-20
Hey Lars need some help with this lamp-server!

---

### Post by Lars Noodén on 2013-10-20
Ok.  Once Apache2 is installed, it gets started automatically and will get restarted automatically whenever you reboot.  The big thing to start with is usually editing the web pages.  By default, you get one virtual host with Apache2 and the default location for the vhost's web pages is /var/www.  If you are the only user of that machine it is enough to take ownership of that directory and then you have write permissions.

```

sudo chown ml7rcex /var/www

```

If you are sharing with others, then group permissions are needed instead.

---

### Post by Lars Noodén on 2013-10-20
Also, here is the server guide.  For Apache2 it covers starting and stopping installed modules and where the configuration file is:

[https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html)

There's not too much to worry about with MySQL, from the system administration point of view:

[https://help.ubuntu.com/12.04/serverguide/mysql.html](https://help.ubuntu.com/12.04/serverguide/mysql.html)

And with PHP5 and Perl 5, you will find the modules in the Ubuntu package repository, if they are not already installed.

---

### Post by willazilla on 2013-10-27
I agree about the warning label! The Apache Friends are now bundling all of their downloads with Bitnami, which adds another layer of completely irrelevant complexity.

---

