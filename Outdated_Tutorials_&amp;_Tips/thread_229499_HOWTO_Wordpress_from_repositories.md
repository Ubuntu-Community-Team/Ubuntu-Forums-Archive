---
title: "HOWTO: Wordpress from repositories"
date: 2006-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by VirtuAlex on 2006-08-04
Wordpress from repositories howto

(!!! WARNING !!! This is "beta version". Please provide any feedback, wether it is working for you or not)

**Introduction**

It seems that many people are trying to install wordpress package from repos and expect it to work right away. In ideal world it should walk you through, or at least point you in the right direction. It is not the case though. You have to configure it yourself.

First let me note that you can install wordpress from source right into www root and have no troubles. However, in that case you have to do the updates the same way each time there is new version. On the other hand, the package from reops will be getting updates automatically, as it meant to be. If you want it this way, let's proceed.

**Installation and Configuration**

Install the wordpress package with
```
sudo apt-get install wordpress
```
or using your favorite method. Anybody could do that but not everybody know what to do next. That is the purpose of this howto.

The list of installed files you can see in the package properties in Synaptic (anybody knows how to do it from command line?):

/etc/wordpress/ - configuration files
/usr/share/wordpress/ - all the php code
/usr/share/doc/wordpress/ - documentation, you're welcome to study it

You may now want to read through /usr/share/doc/wordpress/README.Debian. It pretty much explains your options.

Next you want to connect /usr/share/wordpress to your www root. Some examples are in /usr/share/doc/wordpress/examples/apache.conf, so feel free to experiment. If you have no idea what you're doing, you may still proceed, but first check if your apache is functioning by typing [http://localhost](http://localhost) in your favorite web browser. If it is not then fix it or fix your firewall. Then make a backup your apache2.conf with
```
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak
```
run
```
gksudo gedit /etc/apache2/apache2.conf 
```
and paste the following block of code (it is just one of examples) somewhere. A good place is somewhere close to where Alias /icons is defined the similar way as we will define Alias /blog.
```
########## Without using Virtual host, hosted off /blog

Alias /blog /usr/share/wordpress
<Directory /usr/share/wordpress>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
  DirectoryIndex index.php
</Directory>
```
Save it and restart apache. If you're clueless just reboot. You should be able now to get some php error messages when you go to [http://localhost/blog](http://localhost/blog) in the web browser.

Now you are ready to run the configuration script to make a database and set up connection with something like
```
sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n *wordpress* *blog.example.com*
```
where *wordpress* will be username and the database name at the same time and *blog.example.com* you should replace with your virtual host name or just *localhost* for our example. The script would complain that
```
ln: creating symbolic link `/srv/www/localhost' to `/usr/share/wordpress': No such file or directory
```
because it expects to find your virtual host at /srv/www/ but it is okay for our example cause we did not set up any virtual hosts.

Finally go to [http://localhost/blog](http://localhost/blog) (or your virtual host) and wordpress will walk you through the rest of the setup.

**Sort of Disclaimer**

This howto is not meant to be guide to apache web server, or php, or mysql, or even guide to using wordpress. It is just guide to wordpress package as it functions in Ubuntu Dapper Drake 6.06. It may or may not work in older systems. If you have found any bugs or you want to contribute to this howto in any other way, you're welcome to post in this thread.

---

### Post by timsan775 on 2006-11-14
can the debian wordpress also do multi-logins?

how can any multi-login wordpress be enabled on dapper/edgy?

---

### Post by adamantivm on 2007-04-12
I just successfully followed this how-to on an i386 Edgy - thank you!!

Just wanted to report that in the step where you say:

> sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n wordpress blog.example.com

I had to specify bash as the interpreter instead:
> sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress blog.example.com

---

### Post by andhar on 2007-11-27
still works! thankyou.
 I also had to specify bash as the interpreter.

---

### Post by utlanh on 2010-05-16
thanks for sharing.

---

### Post by catphive on 2010-08-30
I installed from the repository on a fresh ubuntu 10.04 install, and can't get this to work quite right. I think something has broken...

The setup script tries to create an url of this form for some bizarre reason:

[http://example.com/example.com](http://example.com/example.com)

It creates a symlink from /var/www/example.com to /usr/share/wordpress

This works, but of course I don't want that URL. However, if I create a symlink  from /var/www/blog to /usr/share/wordpress, or if I create an entry in my apache config file, it no longer runs index.php when I go to the URL!

Instead what happens is the index.php file itself downloads without being preprocessed... So something about reaching the index file via [http://example.com/blog](http://example.com/blog) instead of [http://example.com/example.com](http://example.com/example.com) makes it fail to run the php.

What's even stranger is that the other php files, such as [http://example.com/wp-login.php](http://example.com/wp-login.php) work *fine*. It's just he index.php that fails!

I don't remember running into this on earlier versions of Ubuntu... Maybe a new bug in the setup script or something? has anyone else had this trouble on Ubuntu 10.04?

---

