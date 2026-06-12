---
title: "Can you have me fix error install xampp in ubuntu 14.04"
date: 2015-12-02
forum: New to Ubuntu
---

### Post by Quandz on 2015-12-02
[https://drive.google.com/file/d/0B0SRNI2xQfKqOHpUdWpVdXpfSWM/view?usp=sharing](https://drive.google.com/file/d/0B0SRNI2xQfKqOHpUdWpVdXpfSWM/view?usp=sharing)
After i install xampp , i open localhost --> localhost/phpmyadmin .
but i don't open it .

---

### Post by Lars Noodén on 2015-12-02
Welcome.  

The easy way is to remove the exotic XAMPP material from the system and then [install a regular LAMP stack](https://help.ubuntu.com/community/ApacheMySQLPHP).  Doing it the Linux way, with LAMP, has a lot of advantages.  One is that it is much easier for you to keep the tools up to date.  Another is that it is easier for people here to help you since the regular LAMP set up will have thing in the standard places. 

If you really want XAMPP instead of a normal LAMP set up then it would help to hear the use-case.

---

### Post by Quandz on 2015-12-02
so you can teach me how to remove it ??

---

### Post by Lars Noodén on 2015-12-02
Removal depends on the steps you followed to get XAMPP.  Probably everything is under /opt somewhere.  Can you point to the web page you followed?

---

### Post by Quandz on 2015-12-02
> **Lars Noodén said:**
> Welcome.  

The easy way is to remove the exotic XAMPP material from the system and then [install a regular LAMP stack]("https://help.ubuntu.com/community/ApacheMySQLPHP").  Doing it the Linux way, with LAMP, has a lot of advantages.  One is that it is much easier for you to keep the tools up to date.  Another is that it is easier for people here to help you since the regular LAMP set up will have thing in the standard places. 

If you really want XAMPP instead of a normal LAMP set up then it would help to hear the use-case.

i have seen. but i'm using ubuntu 14.04 . this to guide in ubuntu low.

---

### Post by Lars Noodén on 2015-12-02
> **Quandz said:**
> i have seen. but i'm using ubuntu 14.04 . this to guide in ubuntu low.

This guide (linked also above) for installation of the LAMP stack is for 14.04 also.  It's for 10.04 on up:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

But first it would be good to clear out the XAMPP material.

---

### Post by Quandz on 2015-12-02
[SIZE=2]i'm a newbie.I recently install ubuntu 14.04 and i want to use xampp in this OS. but i can't install it . i have some problem with it while installed. 
Please help me install it . [/SIZE]

---

### Post by arochester on 2015-12-03
"i have some problem with it while installed. "

What problems exactly?

---

### Post by Quandz on 2015-12-03
[https://drive.google.com/file/d/0B0SRNI2xQfKqOHpUdWpVdXpfSWM/view](https://drive.google.com/file/d/0B0SRNI2xQfKqOHpUdWpVdXpfSWM/view)

You can see it here!. I also remove it and reinstall , but phpmyadmin don't run :( . Can you fix for me ??

---

### Post by Quandz on 2015-12-03
> **arochester said:**
> "i have some problem with it while installed. "

What problems exactly?
[https://drive.google.com/file/d/0B0SRNI2xQfKqOHpUdWpVdXpfSWM/view](https://drive.google.com/file/d/0B0SRNI2xQfKqOHpUdWpVdXpfSWM/view)

You can see it here!. I also remove it and reinstall , but phpmyadmin don't run :( . Can you fix for me ??

---

### Post by Habitual on 2015-12-03
error graphic is
[ATTACH=CONFIG]265912[/ATTACH]

Please see [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

### Post by Quandz on 2015-12-03
> **Habitual said:**
> error graphic is
[ATTACH=CONFIG]265912[/ATTACH]

Please see [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)
Can you install for me by teamviewer?? 
I'm realy not install it :(

---

### Post by matt_symes on 2015-12-03
Hi

> **Quandz said:**
> Can you install for me by teamviewer?? 
I'm realy not install it :(

Any help offered should be kept on the forums as it helps others as well as you.

If someone can help you then they'll post the in the thread for you.

Kind regards

---

### Post by Quandz on 2015-12-03
> **matt_symes said:**
> Hi



Any help offered should be kept on the forums as it helps others as well as you.

If someone can help you then they'll post the in the thread for you.

Kind regards
I've followed your instructions but still will not run. So I need you install help

---

### Post by sandyd on 2015-12-03
> **Quandz said:**
> I've followed your instructions but still will not run. So I need you install help

Can you post the output of
```

ps aux | grep mysql
```

---

### Post by Quandz on 2015-12-04
> **sandyd said:**
> Can you post the output of
```

ps aux | grep mysql
```
[https://drive.google.com/file/d/0B0SRNI2xQfKqUkJhMTB0SVZLWkk/view](https://drive.google.com/file/d/0B0SRNI2xQfKqUkJhMTB0SVZLWkk/view)

You can see !!

---

### Post by Lars Noodén on 2015-12-04
If you don't have a pressing reason you have to use XAMPP, then LAMP is much easier to get installed and running.  As seen in the guide, it's two steps:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Mind the caret ( ^ ), it is part of the meta-package name.  

It will also be easier to maintain.

---

### Post by sandyd on 2015-12-04
=== Threads Merged===
Please do not create multiple threads on the same issue as it dilutes community effort.

Thanks!

---

### Post by sandyd on 2015-12-04
Taking a look at the MySQL path, XAMPP does not install itself there. It installs in /opt/lampp. The XAMPP MySQL may be having trouble starting because the system MySQL is running.

```

sudo service mysql stop

```

Try starting XAMPP again.

If you have issues with XAMPP, it may be better to use Ubuntu's native LAMP installation instead as Lars suggested.

---

