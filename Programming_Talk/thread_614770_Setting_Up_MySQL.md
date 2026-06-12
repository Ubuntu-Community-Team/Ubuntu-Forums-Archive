---
title: "Setting Up MySQL"
date: 2007-11-16
forum: Programming Talk
---

### Post by FrOzeN89 on 2007-11-16
I just got Apache/php working fine and now I want to add MySQL so I can work with it locally. I've installed libapache2-mod-auth-mysql, mysql-admin, and mysql-query-browser. I've never worked with MySQL before except through a CPanel on a website I used to have.

What do I have to do so I can login to MySQL Admin/Query Browser using "localhost"?

Thanks. :)

---

### Post by Kadrus on 2007-11-16
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Here's a link...it's a guide..see the SQL part

---

### Post by FrOzeN89 on 2007-11-16
Sweet, just followed the guide and it worked perfectly. Thanks! :)

---

### Post by Kadrus on 2007-11-16
Glad to help :)

---

### Post by harakiri1976 on 2007-11-19
Hello!


I want to learn [COLOR="Red"]mysql[/COLOR] but I'm having problems:(
I've followed[COLOR="Lime"] Dapper's tutorial above[/COLOR] and installed all correctly. I've tested my [COLOR="Red"]http://localhost/[/COLOR] with a [COLOR="Red"]test.php[/COLOR] and everything is working fine. I can add [COLOR="Red"].php[/COLOR] files to my [COLOR="Red"]/var/www/[/COLOR] and accessed them (view them) using Firefox.
The problem is [COLOR="Red"]mysql[/COLOR] :( I don't know how to use it and How To Start It:( I'll be more specific. If I type [COLOR="Red"]mysq and TAB[/COLOR] on the Shell you can see what I've have:

[COLOR="Red"]Code: [/COLOR]

[COLOR="Blue"]nuno@nuno-desktop:~$ mysql
mysql                       mysql_fix_extensions
mysqlaccess                 mysqlimport
mysqladmin                  mysqlmanager
mysqlbug                    mysqlreport
mysqlcheck                  mysqlshow
mysql_client_test           mysql_tableinfo
mysql_client_test_embedded  mysqltest_embedded
mysqldump                   mysqltestmanager
mysqldumpslow               mysqltestmanagerc
mysql_explain_log           mysqltestmanager-pwgen
mysql_find_rows             mysql_waitpid[/COLOR]

..then, If I try to access mysql I get this error:

[COLOR="Red"]Code:[/COLOR]

[COLOR="Blue"]
nuno@nuno-desktop:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/COLOR]

I don''t know if this is not the way we can start with [COLOR="Red"]mysql[/COLOR] using command line options. Or, If I need to configure [COLOR="Red"]Apache[/COLOR] for the mysql to function correctly. 
I can see that my[COLOR="Red"] /etc/apache2/httpd.conf[/COLOR] is an empty file. I don't know if it helps but I've just "sniffed" those files.

[COLOR="Red"]Code: [/COLOR]

[COLOR="Blue"]
nuno@nuno-desktop:/etc/apache2$ ls
apache2.conf  envvars     mods-available  ports.conf       sites-enabled
conf.d        httpd.conf  mods-enabled    sites-available[/COLOR]

If you please tell me some possible clues about it. 
Thanks!

---

### Post by LaRoza on 2007-11-19
Try:

```

mysql -uroot -p


```

---

### Post by harakiri1976 on 2007-11-19
LaRoza, thanks!... but same problem :(

code:

[COLOR="Black"][SIZE="2"]nuno@nuno-desktop:/etc/apache2$ mysql -uroot -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2[/SIZE][/COLOR])

---

### Post by LaRoza on 2007-11-19
You have to start it.

---

### Post by harakiri1976 on 2007-11-19
[COLOR="Blue"]LaRoza[/COLOR], I'm sorry!

(stupid me!)

...now, I didn't type any password and I guess I did it!! :)
Now I must learn how to "configure" and use MySQL:)

Thanks!
[COLOR="Blue"]
Code:[/COLOR]

[COLOR="Red"]nuno@nuno-desktop:/etc/apache2$ mysql -uroot -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 5
Server version: 5.0.38-Ubuntu_0ubuntu1.1-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> [/COLOR]

Guess it's working! :)

---

### Post by LaRoza on 2007-11-19
You can type your password right after the -p if you want. Make sure there are no spaces between the p and password.

---

### Post by harakiri1976 on 2007-11-19
Hmm didn't work .. the pass!:(


[COLOR="Blue"]nuno@nuno-desktop:~$ mysql -uroot -p[COLOR="Red"]***********[/COLOR]
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[/COLOR]

the [COLOR="Red"]***********[/COLOR] being my password...



PS: Love your Python Tutorials/links/page etc etc.

---

### Post by LaRoza on 2007-11-19
> **harakiri1976 said:**
> Hmm didn't work .. the pass!:(


[COLOR="Blue"]nuno@nuno-desktop:~$ mysql -uroot -p[COLOR="Red"]***********[/COLOR]
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[/COLOR]

the [COLOR="Red"]***********[/COLOR] being my password...

PS: Love your Python Tutorials/links/page etc etc.

The password must have been wrong.

Which link do you like? The first one, or the second one? The first is my own wiki, devoted to the learning of many languages on all platforms, the second is pmasiar's wiki, who often posts after me with reference to his own wiki after I recommend mine. My wiki does link to his internally, but I supposed I could save him the time by having a direct link in my sig. Glad it helped, whichever it was!

---

### Post by harakiri1976 on 2007-11-19
No. I tried the pass a few times:( There's something there missing...especially my ZERO knowledge in mysql. Anyway, this is a good start :)

Well, I loved both. I realized the 1st one (yours) was generic but It connected me to many Python things. That's Good!

I tried to send you a private message about it but I guess I didn't succeed. I was asking you an advice/tip about Programming the Parallel Port with Python. A guy told asked me that in an Electronics Forum a few days and I couldn't help him. He was trying to make a script to communicate with parallel port and heard that there's a script or a Module in Python already written. Asked me if anyone know. I don't! I searched and realized that there's a lot of people here doing it but in "C". but in Python... :(....hmmm guess not. The guy did some stuff in VBA and it worked well. Now he's using Ubuntu and don't want "to come back" to WINDOWS...lol

I'm collecting stuff, info, about Python. I want to learn! I love Python! It's very Powerfull! And very user friendly:)

---

### Post by LaRoza on 2007-11-19
> **harakiri1976 said:**
> 
Well, I loved both. I realized the 1st one (yours) was generic but It connected me to many Python things. That's Good!

I'm collecting stuff, info, about Python. I want to learn! I love Python! It's very Powerfull! And very user friendly:)

What happened to the private message? Did you get an error?

My wiki does have more for Python than most of the other languages, but I hope to balance it out. I am considering adding C#, but am unsure of it.

Just between us, mine is better than the other one. [noparse]:-)[/noparse]

I hope my wiki has enough Python on it for you...

---

### Post by harakiri1976 on 2007-11-19
lol...Yeah! Yours is Good! :)

No, I didn't get any error. But I don't see the Sent Message in my profile. So I am not sure the message was sent :( It's no big deal. I was just asking if you know about the parallel port to send me a Tip. 

I collected a lot of Python Books. Dive into Python is very Good! And "Beginning Python from Novice to Professional" from Apress is a very good one too ;)

---

### Post by LaRoza on 2007-11-19
Sorry, I don't know anything on that topic.

I save the sites and books to my hard disk, so I have a large local collection now. It helps that the Python site gives the complete documentation and everything else as a single download, most useful.

-EDIT Did you see the Python and MySQL section? It may interest you.

---

### Post by harakiri1976 on 2007-11-19
Ok Thank You anyway ;)

I saw your opinion in my threads about being PRO Python. And as I am "starting" it was nice to hear your opinions and other people's opinion.

I did very small (tries) scripts in Python using Windows a long time ago. But I gave up because I hadn't time. :S Now I'm pretending to start from scratch ;)


Best Regards!


and... Thanks! ;)

---

### Post by LaRoza on 2007-11-19
> **harakiri1976 said:**
> Ok Thank You anyway ;)

I saw your opinion in my threads about being PRO Python. And as I am "starting" it was nice to hear your opinions and other people's opinion.

I did very small (tries) scripts in Python using Windows a long time ago. But I gave up because I hadn't time. :S Now I'm pretending to start from scratch ;)

Best Regards!


[http://pyserial.sourceforge.net/pyparallel.html](http://pyserial.sourceforge.net/pyparallel.html)

Found it!

By the way, you sent an email, not a personal message.

---

### Post by harakiri1976 on 2007-11-20
LaRoza, you're right! :)

Thanks man! ;)


PS: Ty for the pyParallel link :)

---

