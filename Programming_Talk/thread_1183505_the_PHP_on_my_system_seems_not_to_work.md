---
title: "the PHP on my system seems not to work"
date: 2009-06-10
forum: Programming Talk
---

### Post by 10ghost on 2009-06-10
I just installed PHP on my system some few weeks ago and after installation i tested it to confirm that it had been installed properly . IT actually worked well that day but some few days ago i tried it again but a simple hello world didnt seem to work.

i would say i am new to ubuntu but i dont know if i am to start up anything before it would work or is there something i need to do first or any way i can use to confirm it is still working? 

Is there any tutorial that can help me to learn to use screem and quanta plus  ?I also need this badly because i am kind of having difficulties using it so far. 
thanx for your anticipated cooperation.
linux for life
long live *ubuntu

---

### Post by hessiess on 2009-06-10
put a file containing

```

<?php
phpinfo();

```

into /var/www then browse to [http://localhost/filename.php](http://localhost/filename.php)

---

### Post by 10ghost on 2009-06-10
I have done what you said but it seems not to work
it displays a blank web browser and tells me to open with quanta plus

---

### Post by 10ghost on 2009-07-02
hi readers,
i had this problem some time ago but the problem is yet to be solved.
Is there anything one must do anytime one turn on his system to start up php,apache,and phpMyAdmin.
Because after installing the trio they all worked on the first day but after then it seems not to work.
Is there way i can use to solve this problem ?

---

### Post by 10ghost on 2009-07-02
hi viewers,
Thanx a million 
i just tried it now and it worked.
i hope it does not stop suddenly again.

---

### Post by Tibuda on 2009-07-02
> **10ghost said:**
> I have done what you said but it seems not to work
it displays a blank web browser and tells me to **open with quanta plus**
How have you installed apache?

You need at least three packages: [apache2, php5 and libapache2-mod-php5]("apt:apache2,php5,libapache2-mod-php5"). If you have these packages, you'll be able to run any php script under /var/www if you open your browser in [http://localhost](http://localhost).

To use MySQL you need also [php5-mysql and mysql-server]("apt:php5-mysql,mysql-server"), and for PostgreSQL you need [php5-pgsql]("php5-pgsql,postgresql"). Your choice.

EDIT: I see you've solved it when I was typing this reply. Sorry.

---

### Post by 10ghost on 2009-07-06
sorry about this readers.
I observed that the php works only when i am connected to the internet.
Is there any special reason for this 
or i am the one that is not doing the right thing?

---

### Post by credobyte on 2009-07-06
LAMP works in offline mode ! For Firefox, uncheck [COLOR=Blue]Work Offline[/COLOR] ( can be found in the main menu under [COLOR=Blue]File[/COLOR] ) and you'll be fine :)

---

### Post by 10ghost on 2009-07-06
@credobyte
It worked but i decided to adjust the php file and add some new lines to the file .
This was not reflected on the web browser when i decided to launch it.
What could be the problem this time?

---

