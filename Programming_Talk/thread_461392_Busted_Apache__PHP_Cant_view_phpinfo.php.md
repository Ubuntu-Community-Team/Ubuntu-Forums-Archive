---
title: "Busted Apache / PHP? Cant view phpinfo.php"
date: 2007-06-01
forum: Programming Talk
---

### Post by haphappy on 2007-06-01
I have tried to set up LAMP on a working Feisty Fawn desktop, as I did not wish to start over with a server install and have to set up everything the way I have it again.

So I have apache2 set up, and if I look at that box's local IP, I get the default apache index.html page. --good so far.
But when I create a new .php document, such as phpinfo.php, place this in /var/www, it does not parse it as PHP, but prompts for an application to open/ download.

I believe I followed all instructions properly, and when following the [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla) guide I found this problem when I reached the Joomla setup portion (copy the files to /var/www/joomla, browse to [http://192.168.xx.xx/joomla](http://192.168.xx.xx/joomla)

What did I miss? Why is PHP not recognized?

---

### Post by Mirrorball on 2007-06-01
Did you install mod_php and restart your server? Also see what modules are enabled in /etc/apache2/mods-enabled.

---

### Post by bobbocanfly on 2007-06-02
i had this problem. I fixed it by removing everything in synaptic then adding it again. YOu should also clear your browsers cache.

---

### Post by haphappy on 2007-06-02
i have libapache2-mod-php5 installed, is there another mod_php module that I should have?

The contents of my /etc/apache2/mods-enabled are 

alias.load            authz_host.load  dir.load          php5.load
auth_basic.load       authz_user.load  env.load          setenvif.load
authn_file.load       autoindex.load   mime.load         status.load
authz_default.load    cgi.load         negotiation.load
authz_groupfile.load  dir.conf         php5.conf


i restarted apache still no dice.

maybe i should uninstall everything and start over, or rather purge everything so it gets rid of configuration files as well, yes? I would rather not, as I would rather find out what the problem is.

Thanks!

---

### Post by Mirrorball on 2007-06-02
Clear your browser's cache, like bobbocanfly said.

---

### Post by bobbocanfly on 2007-06-02
About the purge thing, you HAVE to do that. Everything else didnt work for me, so i purged all the configs and stuff and reinstalled everything then it worked absolutely perfectly. Its annoying to have to go through your apache configs again but its a must.

---

### Post by haphappy on 2007-06-02
yah, cleared cache, did hard reloads, etc. 

What else could it be?  Which guide should i follow if i purge everything.

---

### Post by haphappy on 2007-06-02
Well, starting over with:

sudo aptitude purge apache2 php5-mysql libapache2-mod-php5 mysql-server php5 php4 libapache2-mod-php4 mysql-server libapache2-mod-auth-mysql php5-mysql mysql-server libapache2-mod-auth-mysql php4-mysql phpmyadmin

Try, try again :)

---

### Post by bobbocanfly on 2007-06-02
That error might have come from having both PHP4 and PHP5 on the system at the same time. Might be an idea to jsut use one....

---

### Post by Deedeelo on 2007-06-07
Hi,

It's perharps too late, but I just had the same problem, I purge my applications and reinstalled them but in fact, the only problem was that my .php files where not **executable**.

that's all folks :)

---

### Post by blz on 2012-10-27
> **haphappy said:**
> Well, starting over with:

sudo aptitude purge apache2 php5-mysql libapache2-mod-php5 mysql-server php5 php4 libapache2-mod-php4 mysql-server libapache2-mod-auth-mysql php5-mysql mysql-server libapache2-mod-auth-mysql php4-mysql phpmyadmin

Try, try again :)

Thank you!! That worked for me :))

---

