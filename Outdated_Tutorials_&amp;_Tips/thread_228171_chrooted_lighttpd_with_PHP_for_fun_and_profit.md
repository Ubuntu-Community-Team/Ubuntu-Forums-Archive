---
title: "chrooted lighttpd with PHP for fun and profit"
date: 2006-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by hw-tph on 2006-08-02
*This text is based on a howto on lighttpd on OpenBSD, written and posted by hex29a on openbsd.se.*

[lighttpd](http://www.lighttpd.net) is a light and fast web server. It has fast PHP execution using fastcgi and can be run on both small home servers using old or slow hardware or on big machinery at the professional hosting service. You will probably find it supports everything you want it to - and then some.

One of the greatest upsides to lighttpd is that it is easy to chroot. There are tools that help creating chroots for daemons but lighttpd is very simple since it was built for that in mind. The PHP CGI executable needs some attention though, and we will deal with that later.

***Installing the packages***
First, you need to enable the Universe repository (if you haven't done so already) and install the lighttpd package: ```
$ sudo apt-get install lighttpd
```

We will also need a PHP CGI package. In Ubuntu can select from either php4-cgi or php5-cgi packages. I am using php4-cgi but php5-cgi should work equally well by now. Install the one of your choice and then we will begin with what's interesting.

***lighttpd configuration***
The lighttpd package installs its configuration files in /etc/lighttpd. That's nice but we won't use them. Move the configuration file out of the way: ```
$ sudo mv /etc/lighttpd/lighttpd.conf /etc/lighttpd/lighttpd.conf.original
```
Then copy the default config file from /usr/share/doc/lighttpd/examples/lighttpd.conf.gz to /etc/lighttpd/ and **gunzip** (unpack) it. We will now take a look at a few values and change them to fit our purposes. First, uncomment the modules you will be using in the server.modules section. You must at least uncomment mod_fastcgi and mod_access. I recommend also using mod_redirect and mod_rewrite since it is used in so many web applications. We will be chrooting lighttpd to /var/www, so these directories are relative to that path - "/htdocs" will in fact become /var/www/htdocs. So here is the first batch of directories: ```
server.document-root        = "/htdocs/"
server.errorlog             = "/logs/lighttpd.error.log"
# Scroll down for the last one...
accesslog.filename          = "/logs/access.log"
```
Uncomment this line since it is used by the init script:```
server.pid-file            = "/var/run/lighttpd.pid"
```
Setting the chroot base is of course essential:```
server.chroot				= "/var/www/"
```
lighttpd can assume the rights of a specific user when started. In Debian and Ubuntu the default for web servers is the www-data user and the www-data group: ```
server.username				= "www-data"
server.groupname			= "www-data"
```
This part below enables the fastcgi backend. Note that if you use the php5-cgi package you will need to change the path to the executable!```
fastcgi.server             = ( ".php" =>
                               ( "localhost" =>
                                 (
                                   "socket" => "/tmp/php-fastcgi.socket",
                                   "bin-path" => "/usr/bin/php4-cgi"     # Change this if you use php5!
                                 )
                               )
                            )
```
That should be it. Wasn't so hard, now was it? :)
For reference, I have attached a working lighttpd.conf.

***Setting up the chroot***
lighttpd in itself doesn't require anything in particular to run chrooted, but PHP does, and here is where the hard work has to be done - copying the libraries that php4-cgi (or php5-cgi) needs.

First we need to set up some basic directories and permissions though:
```
$ cd /var/www
$ sudo mkdir htdocs logs tmp
$ sudo mkdir -p var/lib/php4
$ sudo chown root:www-data logs tmp
$ sudo chmod g+rw logs tmp var/lib/php4
```
The commands above create the directories and sets sane permissions on them - lighttpd needs to write its logs, and the var/lib/php4/ directory is for saving PHP sessions.

OK, so PHP then. What we will do is check what libraries the PHP CGI program uses and copy them into a directory structure that resembles the "real" root filesystem structure. The ldd command shows what libraries a program uses: ```
$ ldd /usr/bin/php4-cgi
        linux-gate.so.1 =>  (0xffffe000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7ef4000)
        libzzip-0.so.12 => /usr/lib/libzzip-0.so.12 (0xb7eee000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7ed8000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7eb9000)
        libdb-4.3.so => /usr/lib/libdb-4.3.so (0xb7ddd000)
        libgdbm.so.3 => /usr/lib/libgdbm.so.3 (0xb7dd7000)
        libbz2.so.1.0 => /lib/libbz2.so.1.0 (0xb7dc6000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7db2000)
        libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb7d83000)
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7d46000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7d33000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d11000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7d0e000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7cf2000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7c78000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7c55000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7c52000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b23000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb79f5000)        /lib/ld-linux.so.2 (0xb7f34000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb79ef000)
```
*Do the above yourself!* With the constant upgrades going on, chances are something might change so don't take my word for what libraries are needed and where they are located. First create the directories needed - libraries living in /lib should be copied to /var/www/lib, files in /usr/lib to /var/www/usr/lib...you get the idea (I hope). The "file" linux-gate.so.1 is a virtual DSO - this is no file you have to copy so just skip past it. This manual copying will likely take you a little while and is by far the most time consuming part.

When done, also copy the php4-cgi binary from /usr/bin to /var/www/usr/bin. The PHP configuration file, php.ini, should be copied from /etc/php4/cgi/php.ini to /var/www/etc/php4/cgi/php.ini in order for it to get recognized properly. If you use the php5-cgi package you will obviously need to change the paths. And yes, I know it's a lot of directories (that's why there are tools for automating this).

***MySQL***
If you want to use MySQL support in PHP (most will want this), you need to copy /usr/lib/php4/20050606/mysql.so to /var/www/usr/lib/php4/20050606/ and add this to the bottom of your /var/www/etc/php4/cgi/php.ini:```
extension=mysql.so

```As usual - if you use PHP5, change the paths accordingly.


***Finalizing and starting up***
By now you should have a fully functional lighttpd chrooted to /var/www! Either create an index file in /var/www/htdocs/ or move the original Ubuntu lighttpd index.html from /var/www into that directory and start the server: ```
$ sudo /etc/init.d/lighttpd start
```
If you did everything right (and if *I* got everything right) it should start up quickly and quietly. Check PHP functionality by using the phpinfo() function in a file: Create /var/www/htdocs/bleh.php with this content:```
<?php
    phpinfo();
?>
```
Browse to the file ([http://localhost/bleh.php](http://localhost/bleh.php)) and see how PHP is configured.

---

### Post by peanut butter on 2006-10-14
nice guide. I finally found some time to try it. it works great.:)

---

### Post by nickleus on 2007-02-13
i did everything here, for php5, but it still just says "Fail" when i try to restart or force-reload and it won't start. i'm using ubuntu 6.06, lighttpd 1.4.11, php5-cgi and postgresql 7.4. lighttpd starts fine when i don't enable mod_fastcgi, but once i do that it won't start... wish i knew how to get it to tell me what was wrong (is there some kind of verbose debug flag i'm not seeing?)

---

### Post by nickleus on 2007-02-13
i figured it out:
[http://norgesinternettforum.no/showthread.php?p=2779#post2779](http://norgesinternettforum.no/showthread.php?p=2779#post2779)
basically all that stuff above was unnecessary (at least for getting php cgi/fastcgi working...not sure about chroot-ing though), just install php5 and then run the lighty-enable-mod fastcgi then edit the 10-fastcgi.conf file with the correct bin-path... pretty simple actually...

---

