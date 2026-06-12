---
title: "Random Web Design Question!"
date: 2007-05-03
forum: Programming Talk
---

### Post by RMorris78 on 2007-05-03
I was just wondering if anyone with a little web design experience could help me out with something I have to put together rather hastily.  Any help or pointers would be appreciated.

I have a webserver setup already with a DynDNS domain name.  My webpage works fine.  I need to create a page for a little survey I am doing for school for about 20 people, so not a big operation by any sorts. 

The operation I am trying to do is create a page where it asks several questions with a response box for each one.  Then, I would like the user to click submit, and send the answers to me via email, if possible.  I know HTML pretty well, but I am assuming that I will need to use something like javascript to do this.

Any guidance would help!

Thanks!

---

### Post by dfreer on 2007-05-03
php would probably work better, and it doesn't require too much experience to use. make sure your server has php installed correctly (if you use the server install with LAMP you already have it), and then you can probably google for a simply script to run it. Should just need the POST/GET of HTML and a few lines of php I should think.

---

### Post by RMorris78 on 2007-05-03
thanks so much for the help, I will install lamp on the server right now. do you know of anywhere i can find a tutorial on how to do this?

---

### Post by dfreer on 2007-05-03
LAMP stands for linux apache mysql php (in the ubuntu distro, it really can mean several different things), but I'm sure you already knew that.
this guide is for 6.10, but it should work really for Dapper/Edgy/Feisty. Also, although a lot of people use this guide i wouldn't recommend it because it installs a LOT of stuff that most people do not need/use/understand, and the way I see things the more services you install the less secure your server is, ESPECIALLY if you do not know what you are doing (that being said, I probably run more things then I should myself :D ):
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

mysql install on this page (not really needed I should think for your purposes, although most how-to's will probably use it alongside of php. If you get a lot of data this could be useful but requires a bit more setup):
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4)

also here (might recommend this if you want to install mysql, and then use the above link to configure mysql and set the root password): 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_Database_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_Database_Server)

php install on this page:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP5](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP5)

---

### Post by gvoima on 2007-05-03
I usually don't program web sites/applications, but when I do I use mostly PHP and get much help from [http://www.w3schools.com/]("http://www.w3schools.com/"). There's also some little tutorials to get you going on different scripting languages.

Hope it helps :)

---

### Post by dfreer on 2007-05-03
whoa, got really confused! your two avatars look so similiar I thought it was the OP was giving himself advice! ROFL

---

### Post by gvoima on 2007-05-03
hahaha :D

well it's 6 AM here and I'm tired as *ell, people get easily confused ;)

---

### Post by RMorris78 on 2007-05-03
Ok, i have a form all ready to use and stuff, but i think i need to setup sendmail on my server or something, becuase when i submit this form, this is the error i get

[http://robmorris.is-a-geek.com/mailform.php](http://robmorris.is-a-geek.com/mailform.php)

---

### Post by haricharan on 2007-05-03
Are you sure mailform.php is in the /var/www/ directory??

---

### Post by dfreer on 2007-05-03
yeah website is up but it looks like mailform.php is not found on the server.

---

### Post by RMorris78 on 2007-05-03
ah my fault, got it figured out now thank you so much!

---

### Post by Mirrorball on 2007-05-04
For the simplest solution, you could put an email address as the form action:
```
<form action="MAILTO:someone@domain.com" method="post" enctype="text/plain">
```
When the user submits the form, his email client creates the message automatically from the form data and the user can send it to you.

---

### Post by haricharan on 2007-05-04
> **RMorris78 said:**
> ah my fault, got it figured out now thank you so much!
so what was the fault??

---

### Post by deuce868 on 2007-05-05
If you just want a survery, don't reinvent the wheel. phpESP is a decent survey app. I've used it a couple of times. 

[http://www.butterfat.net/wiki/Projects/phpESP/](http://www.butterfat.net/wiki/Projects/phpESP/)

---

