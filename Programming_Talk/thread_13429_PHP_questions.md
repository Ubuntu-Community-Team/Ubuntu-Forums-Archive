---
title: "PHP questions"
date: 2005-01-31
forum: Programming Talk
---

### Post by philip41 on 2005-01-31
A few years ago i was writing web pages in HTML, i never used the wysiwyg programes, i just used to use windows notepad, and then check them in a browser.

Now i want to get back into web design, but obviously things have moved on a bit.
I actually want to learn php.

I have found some good sources on the net, so that is not a problem. What i really need to know is, how do i set my linux box up so as i can easily see the results (test) my php efforts.

As far as i can tell, i need to install Apache ( if so which version ) also do i need to have mysql installed.

Sorry to sound such a Noob.

---

### Post by ups on 2005-01-31
You will need apache (the version doesnt really matter, but the one in synaptic is the latest i think). You can install that. MySQL is needed only if you need a database, which i think you don't initially. 

ofcourse you'll need php, and also the libapache2-mod-php4 package, for php and apache to work together properly.

---

### Post by philip41 on 2005-01-31
Thanks ups, i thought i needed these apps just needed confirmation, thanks also for the heads up on installing  libapache2-mod-php4 package .

Anything else i may need to know just let me know please.

thanks

---

### Post by philip41 on 2005-01-31
Ah just looked in Synaptic, there is Apache 1.3.33-3  A versatile, high performance HTTP server, or there is Apache2 2.0.52-ubuntu 3 next generation scalable extendable web server.

Re read above, so i will install Apache 2

---

### Post by ups on 2005-02-01
[QUOTE=philip41]Ah just looked in Synaptic, there is Apache 1.3.33-3  A versatile, high performance HTTP server, or there is Apache2 2.0.52-ubuntu 3 next generation scalable extendable web server.

Re read above, so i will install Apache 2[/QUOTE]
 yes, install apache2, it should be fine.

after the installation, you will need to place your files in the /var/www directory. then you can access them from your browser by pointing at [http://localhost](http://localhost)

---

### Post by philip41 on 2005-02-01
[QUOTE=ups]yes, install apache2, it should be fine.

after the installation, you will need to place your files in the /var/www directory. then you can access them from your browser by pointing at [http://localhost](http://localhost)[/QUOTE]

Cheers got it all going, just one thing that got was putting files in the /var/www directory, i had to go in and change user permissions, but having done that all is set up now.

Thanks for your advice.

---

### Post by DJ_Max on 2005-02-01
[QUOTE=philip41]Cheers got it all going, just one thing that got was putting files in the /var/www directory, i had to go in and change user permissions, but having done that all is set up now.

Thanks for your advice.[/QUOTE]
 Might wanna look at this, [http://ubuntuforums.org/showthread.php?p=6101](http://ubuntuforums.org/showthread.php?p=6101)

---

### Post by moonshot on 2005-07-13
I have php installed by default.  phpinfo() works fine.  The problem I have is that I want to use mysql with php.  I have mysql up and running, populated with some DBs.  My problem seems to be that I don't have support for mysql in PHP.   I never installed php, it was installed with ubuntu, so I didn't have the choice of doing a -with-mysql option.

What is the best way to go about fixing this?

Thanks much.

---

### Post by DJ_Max on 2005-07-13
Do a 
```
apt-cache search php mysql
```

Then install the package you see fit. I believe it's named php4-mysql.

---

### Post by moonshot on 2005-07-13
[QUOTE=DJ_Max]Do a 
```
apt-cache search php mysql
```

Then install the package you see fit. I believe it's named php4-mysql.[/QUOTE]

Hmm, it didn't find anything.  I varied the search a few times and couldn't find it at all.

---

### Post by DJ_Max on 2005-07-13
I found it.
```
sudo apt-get install php4-mysql
```

---

### Post by ProNoblem on 2005-07-13
A nice and tidy howto is written in the Unofficial Ubuntu starter guide, just follow the three steps mentioned there 
[indent]( Q: How to install Apache HTTP Server for HTTP (Web) Server service?  
&&  Q: How to install PHP for Apache HTTP Server?  
&&  Q: How to install MYSQL for Apache HTTP Server?)[/indent]

Link: [http://www.ubuntuguide.org/#installapachehttpserver](http://www.ubuntuguide.org/#installapachehttpserver)

And you'll be up and running in notime

---

### Post by moonshot on 2005-07-13
Quite strange...apt-get install php4-mysql doesn't work for me.  It can't find the package.

---

### Post by DJ_Max on 2005-07-13
[QUOTE=moonshot]Quite strange...apt-get install php4-mysql doesn't work for me.  It can't find the package.[/QUOTE]
 You probably have to add the extra repositories.
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by MDoten on 2005-09-22
I am using php5 and I did the *sudo apt-get install php5-mysql* and it installed it. The only problem is, the mysql commands still don't work in php. Also, when I check the phpinfo(), there is no mysql section in there. How do I fix this??

---

