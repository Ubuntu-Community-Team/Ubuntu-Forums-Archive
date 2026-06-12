---
title: "Help Setting up Apache server."
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2008-08-12
I'm getting started with apache server and have already hit a roadblock. I can't seem to get a site set up right or apache configured or anything much beyond installing apache. Where do I go from here?

---

### Post by Thelasko on 2008-08-12
Ironically, Microsoft made a video about how to do this a while back.  They claim it's more difficult to do it in Ubuntu than in Windows but I'll let you decide for yourself.

[Ubuntu]("http://download.microsoft.com/download/E/D/D/EDD40B84-7889-4B7F-9EEE-D9D690751DB2/Linux_avi.wmv")
[Windows]("http://download.microsoft.com/download/E/D/D/EDD40B84-7889-4B7F-9EEE-D9D690751DB2/Windows_Perl_PHP.wmv")

---

### Post by Thelasko on 2008-08-12
P.S. I hear [XAMPP]("http://en.wikipedia.org/wiki/XAMPP") is even easier to setup.

---

### Post by Cypher on 2008-08-12
Install Apache with
```

sudo apt-get install apache2

```
This will create the directory /var/www for your HTML documents, the directory /etc/apache2 for your configuration and other directory for the Apache files that you shouldn't need to worry about.

Installation should cause the Apache services to start up, you should now be able to point Firefox to [http://localhost](http://localhost) and get the message "It Works!".

Depending on what you want to do with Apache, you might want to instal PHP, MySQL and other services.

There are numerous documents detailing installing LAMP and I've done it too many times to remember, so tell us what you exactly did and we get you past your roadblock..

---

### Post by Dr Small on 2008-08-12
> **Thelasko said:**
> P.S. I hear [XAMPP]("http://en.wikipedia.org/wiki/XAMPP") is even easier to setup.
+1 for XAMPP.
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by Cypher on 2008-08-12
XAMPP is a great tool for getting Apache/MySQL/PHP up on Windows, but in Ubuntu it'd be better to stick to the files in the Ubuntu repos. Getting Apache/MySQL/PHP up in Linux is well documented and also you benefit from getting the necessary updates from the repository..

---

### Post by Dr Small on 2008-08-12
> **Cypher said:**
> XAMPP is a great tool for getting Apache/MySQL/PHP up on Windows, but in Ubuntu it'd be better to stick to the files in the Ubuntu repos. Getting Apache/MySQL/PHP up in Linux is well documented and also you benefit from getting the necessary updates from the repository..
Not necessarily, as php5 from the repositories do not have support for php5-gd library, which basically means, you can't have php display images with the gd library. I found that XAMPP has this already and is very simple to install and setup, not to mention, to secure.

---

### Post by Gravidar on 2008-08-18
I find myself in the same position.
I've followed several different LAMP installation guides and the result is the same. MySQL doesn't work with PHP. Can someone please point me in the direction of a LAMP install guide that includes getting MySQL to work with PHP5 or be kind enough to post the instructions here?
All I've been able to find out ([here]("http://nz.php.net/manual/en/faq.databases.php#faq.databases.mysql.php5"))  is that PHP5 is no longer bundled with the libraries needed for MySQL with a very unhelpful comment saying > "Unix users, at least the ones who know what they are doing, tend to always build PHP against their system's libmyqlclient library..."
Not being one of those who know what they're doing, I'm stuck :(

Error messages I'm getting are:
php-mysql.so is not loaded - I've added extension=php-mysql.so to php.ini but the is no such file anyway, at least now I know why.
And phpmyadmin says "Cannot load mysql extension. Please check your PHP configuration."

Your help is greatly appreciated.

Running 8.04.1 Server in VMWare Player

EDIT: resolved by rebuilding LAMP server with ```
sudo tasksel install lamp-server
``` on a clean Ubuntu install - wish I'd found that 3 days ago.

---

### Post by john test on 2008-08-18
The advantage of xampp is that it comes preconfigured and ready to rock and roll with apache, mysql, php5 and proftp.  all I did was download and untar and do /opt/lampp/lampp start and I had an apache server up and running.  I didn't actually do a web page I just downloaded phpbb2 and untarred it into the directory tree loaded the forum into the database and I had a forum up and running in a couple of days.
Thing is the apache server just untarred and started to work on fuss no muss

---

### Post by indytim on 2008-08-18
<opinion> It doesn't get much easier than:
$sudo tasksel

-select the LAMP -
-sit back and relax'
-enjoy-
</opinion>

:)

IndyTim

---

### Post by hyper_ch on 2008-08-18
if you want an advanced setup (apache, mysql, php, nameserver, multi-site hosting, control panel) just follow the "Perfect Howtos" from [http://www.howtoforge.com](http://www.howtoforge.com)

It's all copy'n'paste (well, most of it) ;)

---

