---
title: "Installation of PHP (with support for ncurses)"
date: 2010-05-21
forum: Programming Talk
---

### Post by bobsta63 on 2010-05-21
Good afternoon all,

I am trying to write a console application that will be accessed by various users, I am very fluent in PHP development so my idea was to use PHP and ncurses to create a database application.

The users would SSH to the Ubuntu Server and then would be able to run the application by calling the following command:-

```
php example.php
```

Which is all fine and I know what im doing with regards to developing the app and how people could connect to the server using SSH and use the application etc.

However I am having real troubles installing PHP and ncurses together to enable the use of ncurses within PHP, I keep getting a message saying 'unkown function ncurses_init()'.

With that said obviously PHP can't access the ncurses lib etc. I see over at the CentOS forums that people can install php ncurses using YUM eg.

```
yum -i php-ncurses
```

So my queston really is....

Is there anyway I can install PHP with ncurses support with 'apt-get'??? - I've had a look but have been unable to find anything as yet.... I really hope somebody can make my day!! :)

Thank you in advance :)

Kind regards,
Bobby

---

### Post by sharath.puranik on 2010-05-21
You need the development packages of ncurses, try to search for "libncurses" in package manager, and install the package which says dev. Then try compiling by externally including the ncurses package.

i think the latest version is 5.7 something...

---

### Post by bobsta63 on 2010-05-21
> **sharath.puranik said:**
> You need the development packages of ncurses, try to search for "libncurses" in package manager, and install the package which says dev. Then try compiling by externally including the ncurses package.

i think the latest version is 5.7 something...

Sorry to seem such a n00b but how would you advise I do that?

Are you saying I should download PHP seperately and then compile PHP with the path to the ncurses path or is it simplier than that?

Could'nt I just do the following:-

```
apt-get install libncurses
apt-get install php php-common php-dev php-cli
```

Many thanks for your help so far :)

---

### Post by Bachstelze on 2010-05-21
Apparently the ncurses modules is not shipped with PHP 5.3, so if you are using Lucid, you will have to use the PECL extension:

```
sudo pecl install ncurses
```

---

