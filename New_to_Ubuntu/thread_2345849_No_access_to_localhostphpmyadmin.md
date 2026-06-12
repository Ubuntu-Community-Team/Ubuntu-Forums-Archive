---
title: "No access to localhost/phpmyadmin"
date: 2016-12-08
forum: New to Ubuntu
---

### Post by joelrio on 2016-12-08
Hi I have a Lamp stack on Kubuntu 16.04. All seems to work fine and I have a WordPress site ongoing and now looking to move it online.

However I can't access localhost/phpmyadmin through my browser. My php install was

```
$ sudo apt-get install php7.0 php7.0-mysql libapache2-mod-php7.0 php7.0-cli php7.0-cgi php7.0-gd
```
I'm guessing that i didn't install the admin part of the php setup. Is that so?  And what to do? 

Thanks Joel

---

### Post by SeijiSensei on 2016-12-08
Did you actually install phpmyadmin?  If not, then "sudo apt-get install phpmyadmin" should solve your problem.

---

### Post by joelrio on 2016-12-08
No I didn't install phpmyadmin specifically. I wasn't sure about doing it. So OK I'll try that.
 Thanks

---

### Post by joelrio on 2016-12-08
Did that. Its installed into .etc/. 
I chose not to configure automatically as I already have database for my website. So was that a mistake?  I still cant access through my browser. How do I configure?

---

### Post by SeijiSensei on 2016-12-08
I use the command-line clients for pretty much all SQL services so I don't have much experience with phpmyadmin.  

I do think you need to have it configure itself when you install.  phpmyadmin creates another database of its own.  Without it, I don't think it can function.  I just installed it to this machine, told it to configure itself, and I get a login page at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/).  Probably your best bet is to reinstall with
```
sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin

``` 
and say "yes" when it asks if you want it to configure your database.

---

### Post by joelrio on 2016-12-08
Yes I thought so as well. I'll try again. Thanks

---

### Post by joelrio on 2016-12-09
I purged phpmyadmin. Then reinstalled via terminal.
> sudo apt-get update
sudo apt-get install phpmyadmin php-mbstring php-gettext
Then 
> sudo phpenmod mcrypt
[LEFT][LEFT]sudo phpenmod mbstring
Restarted apache, went to localhost/phpmyadmin and no joy, 404 page

A couple of things. During install mbstring and gettext were already latest packages so weren't reinstalled.
And not sure if I got the password bit right. I put in my MySql pw. at both prompts. Any ideas?

[/LEFT]
[/LEFT]
Thanks Joel

---

### Post by joelrio on 2016-12-09
I worked out that during installation, I pressed <ENTER> instead of <SPACE> to select Apache2, and  the window disappeared.
What I've done is to reconfigure phpmyadmin 
[quote]sudo dpkg-reconfigure phpmyadmin[quote]
and this time selected apache with the space bar then enter.
I now have the welcome to phpMYAdmin window. I'll have a tinker and come back to mark as solved if all good.
Thanks Joel

---

### Post by localhostphp on 2017-11-01
> **SeijiSensei said:**
> I use the command-line clients for pretty much all SQL services so I don't have much experience with phpmyadmin.  

I do think you need to have it configure itself when you install.  phpmyadmin creates another database of its own.  Without it, I don't think it can function.  I just installed it to this machine, told it to configure itself, and I get a login page at [http://localhost/phpmyadmin]("http://localhost.support/phpmyadmin")  Probably your best bet is to reinstall with
```
sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin

``` 
and say "yes" when it asks if you want it to configure your database.

You can try [http://localhost:8080/](http://localhost:8080/)

---

