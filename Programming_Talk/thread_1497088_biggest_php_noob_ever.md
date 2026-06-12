---
title: "biggest php noob ever"
date: 2010-05-30
forum: Programming Talk
---

### Post by kartabosh on 2010-05-30
hello
i have no knowledge of php at all, i'm just messing around with multiple programming languages and while trying to do something on my website i downloaded different scripts and none of them were what i wanted so i decided i want to create my own so for the last 2 weeks i kept editing the current scripts i had to understand it better 

however every time i modify it i have to upload it on my server and stuff like that, but i remember like 5 years ago the teacher showed us how we could like set up a folder in which when we put the files we could access the scripts in [http://localhost](http://localhost) or something like that
i remember vaguely something about mysql and stuff, can anyone help me?

---

### Post by simeon87 on 2010-05-30
You can install Apache with PHP and then you can indeed put PHP scripts in the website directory and it'll use those. Then you don't have to upload it each time. There are many guides on the internet on how to do this, also search for LAMP (Linux, Apache, MySQL, PHP) as this is a very common combination. You can ever install these things together (the latter three) and then you also have a MySQL database where you can store data. You'd use SQL to read/write the data.

---

### Post by kartabosh on 2010-05-30
do you know like a deb package or something?

---

### Post by xsinsx on 2010-05-30
youll just need to do this [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Can+~ on 2010-05-30
You'll need to edit the /etc/apache2/sites-available/default file, so you can have something like /home/username/www for easier editing.

And if you're in a notebook, I suggest having Apache2 turned off by default, and turn it on when you're going to use it, mostly for battery purposes. Use gnome-do to easily start the process again.

---

### Post by kartabosh on 2010-05-31
thanks i got it working
how can i set title to solved?

---

### Post by Can+~ on 2010-05-31
"Thread Tools", on the top, that dark red link.

Also, as a tip for apache2, I suggest you to put a folder on your home, and edit sites-available/default:

[HTML]	<Directory "/home/USERNAME/www">
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from 127.0.0.1
	</Directory>[/HTML]

Where "USERNAME" is your username. Also notice that I put "allow from 127.0.0.1", this will make it visible just for you from localhost, just for safety.

The advantage of having a folder directly on home, is pretty much to avoid fighting with permissions, and having it right there for work, very handy!

Also, take a look at Python Server Pages ([Package]("apt:libapache2-mod-python")), if you want to try something different, never liked php.

---

### Post by kartabosh on 2010-05-31
i read your earlier post but the link above on installing apache and everything guided me to do it, its pretty much the same as yours so i already did that, and what do you mean "Also notice that I put "allow from 127.0.0.1", this will make it visible just for you from localhost, just for safety." i don't understand that, is it visible by anyone else right now?

---

### Post by Can+~ on 2010-05-31
> **kartabosh said:**
> i don't understand that, is it visible by anyone else right now?

If you're behind a router, then everyone on your local network can see you. Try it, go to another computer on your network, get your local ip adress with ifconfig (typical Cisco LAN adress: **inet addr:192.168.1.XXX**) and connect with:

```
http://yourip:port/
```
(If port is 80 (default), then it's not required)

If you don't want anyone on your local network to see you, just do that, restrict to your own localhost address (127.0.0.1).

If you don't want anyone OUTSIDE your network to see you, if you're behind a router, you're safe.

On the other hand, if you actually want people outside your network to see your site, or send it to a friend, edit your router settings, redirect port 80 to your local address and allow everyone to see it. Then you can get your external ip and share it. Useful when you're showing someone your work. Notice that this is for just one-time link, next time you connect to your router, it will probably hand you another local address (can be worked outed setting a request IP instead of automatic DHCP), and your ISP maybe also gives you a dynamic address.

---

