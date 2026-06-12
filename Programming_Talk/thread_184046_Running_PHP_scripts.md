---
title: "Running PHP scripts"
date: 2006-05-29
forum: Programming Talk
---

### Post by Simian on 2006-05-29
I have been following a very simle PHP tutorial for beginners (hello world level). I soon learnt that in order to run the scripts in the tutorial I hade to have apache installed and and run the scripts from /var/www through a browser. That sounds straght forward, but All I see on the browser (firefox) is the contents of my script.

I followed the [Apache MySQL PHP]("https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28php%29") howto on the ubuntu wiki but I eneded up with no internet conection. Not sure what I did wrong but I'm determind to get it right.

Any help or advice would be much appreciated :)

---

### Post by orlox on 2006-05-29
I just installed everything from synaptic(apache, php, mysql) and it worked right away...

---

### Post by Simian on 2006-05-29
hmm, that's what I did (three times :( )

i installed PHP 5, MySQL 5, apache 2, php-mysql, php-msqli and then some.

---

### Post by mostwanted on 2006-05-29
Run them from the path localhost/ not /var/www, otherwise they'll be served by the file-system, not Apache.

---

### Post by Simian on 2006-05-29
[QUOTE=mostwanted]Run them from the path localhost/ not /var/www, otherwise they'll be served by the file-system, not Apache.[/QUOTE]

I was. I saved them in /var/www and then entered localhost into a browser.

---

### Post by brickbat on 2006-06-02
Check that in /etc/apache2/apache2.conf you have these two lines

Addtype application/x-httpd-php .php .phtml .phtml .html
Addtype application/x-httpd-php-source .phps

If they are there, they must be uncommented.

You need to restart apache for them to take effect if you have added them.

---

### Post by mlind on 2006-06-03
install userdir extension for Apache httpd, and develop files locally, so you won't
get unneccessary permission related trouble.

```

sudo a2enmod userdir
mkdir ~/public_html

```

copy your stuff to *~/public_html* and access it using
[http://localhost/~yourusername/](http://localhost/~yourusername/)

---

### Post by David Marrs on 2006-06-03
did you install libapache2-mod-php5

---

### Post by Jethro97 on 2008-03-22
I'm having the same  problem, after using the Apache MySQL PHP howto on the ubuntu wiki i tried to run a php file i made: [http://localhost/phpfile.php](http://localhost/phpfile.php), but it gave me the script instead of the output, i've also tried everything in this post.

i'm running 7.10, and i don't know if this helps but when i type in apache2 into the terminal it returns

(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80

and when i type in php5 it hangs

Thanks for the help

---

### Post by sanderd17 on 2009-07-20
> quick dirty installation guide:

```
$ sudo apt-get install apache2 mysql-server libapache2-mod-php4 php4-mysql phpmyadmin
# phpmyadmin is not strictly necessary, but useful
# if necessary
$ sudo /etc/init.d/apache2 restart
$ sudo /etc/init.d/mysql restart
```



I used this from[ thread 43281]("http://ubuntuforums.org/showthread.php?t=43281") but just changed php4 tot php5 and it worked

---

### Post by Alias1407 on 2009-07-20
Just install LAMPP,

Linux Apache MySQL PHP Perl


It is good, it does everything for you!!

---

### Post by ebharv on 2009-07-21
> 
 				 				**Re: Running PHP scripts** 			
 			 			 		   		 		 		Just install LAMPP,

Linux Apache MySQL PHP Perl


It is good, it does everything for you!!

I agree with Alias1407. Go to the [xampp]("http://www.apachefriends.org/en/xampp-linux.html#374") site and install xampp. If you just want to do one site at a time then change the permissions on the /opt/lampp/htdocs folder and put your stuff there. If you want more than one let know because it involves changing your host file and I'm not at the house so I write it all down right now.

---

