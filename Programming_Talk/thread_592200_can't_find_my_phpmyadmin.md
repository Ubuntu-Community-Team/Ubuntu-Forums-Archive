---
title: "can't find my phpmyadmin"
date: 2007-10-26
forum: Programming Talk
---

### Post by Findarato on 2007-10-26
Hello everyone,
I know it's a noobish question, but I only started to use linux recently and Im having a problem accessing / finding my phpmyadmin

I followed the [http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu)
LAMP installation and saw that "Mysql Administrator" got installed with it, but also phpmyadmin. The only thing is, I have no idea where to access it, as localhost/phpmyadmin doesn't seem to work.

I guess this has to have a very easy answer, but I've been trying for 2 hours now and can't seem to find it going :(

Thanks a lot for your time

---

### Post by scxtt on 2007-10-26
try this:

sudo slocate -u
slocate config.inc.php

phpmyadmin should be located one directory up from that file ... something like /var/www/phpmyadmin and accessible via [http://localhost/phpmyadmin](http://localhost/phpmyadmin) ... i have it installed in Gentoo and Centos5, never installed mysql in ubuntu, but it can't be that different ...

---

### Post by Findarato on 2007-10-26
I have the file in three different folders (no idea why) /usr/share/phpmyadmin
/etc/phpmyadmin and
/var/lib/phpmyadmin

do I just move one of them?

---

### Post by scxtt on 2007-10-26
did you install it manually or via apt/aptitude?  my install for CentOS5 was manual (from their site) and it's in /usr/share/phpmyadmin ...

i use vhost to get **[http://phpmyadmin.centos5.localdomain](http://phpmyadmin.centos5.localdomain)** that loads it up w/o a symlink of /var/www/phpmyadmin -> /usr/share/phpmyadmin ... i'm 99% sure config.inc.php is there, you just need to make sure apache is aware of that fact ...

don't MOVE anything! :)

---

### Post by Findarato on 2007-10-26
> **scxtt said:**
> /usr/share/phpmyadmin ... i'm 99% sure config.inc.php is there, you just need to make sure apache is aware of that fact ...


and this done by editing which file? :P

---

### Post by scxtt on 2007-10-26
let's start simple, do you know if apache is working fine?  can you put a file such as /var/www/index.html w/ something like "this is a test" and use [http://localhost/index.html](http://localhost/index.html) to view it?

if so, it'd probably be as simple as:

sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin

then going to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
(keep in mind there's still some [relatively easy] phpmyadmin-specific setup involved w/ config.inc.php)

---

### Post by Findarato on 2007-10-26
my apache was working fine, only now I used this command, somehow I can't save sessions anymore. I'm getting the error:
Warning: session_start() [function.session-start]: open(/var/lib/php5/sess_30b978fd5e8e44c2e912b558d92807e2, O_RDWR) failed: Permission denied (13) in /var/www/cjonline/index.php on line 1

on my locally installed site and

Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.


when I access phpmyadmin

---

### Post by scxtt on 2007-10-26
> . . . only now I used this command . . .what command?  and what sessions are you trying to save?  there could be permission problems on /var/www/[*] - can't tell @ this point.

like i said, there's some configging left in config.inc.php for phpmyadmin ...

---

### Post by Findarato on 2007-10-26
after I used
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin I meant

I don't know where and how to edit the file though :( I looked at some config.inc.php but don't see where I should edit

sessions I was talking about are simple sessions creations:
<?php session_start();

$_SESSION['speed'] = $_REQUEST["speed"];
$_SESSION['lang'] = $_REQUEST["lang"];
header("Location: index2.php");

?>

---

### Post by Findarato on 2007-10-26
anyone? :(
now I can't only not find phpmyadmin, but my server is messed up aswell :(

---

### Post by scxtt on 2007-10-26
well all the command i gave you did was make a symbolic link that says when /var/www/phpmyadmin is "referenced" point the request to /usr/share/phpmyadmin -- don't see how that would affect anything session-related -- if you really think it could have messed something up (not possible) remove it ...

i generally edit my config.inc.php file to:
[php]<?php
/* vim: set expandtab sw=4 ts=4 sts=4: */
/**
 * phpMyAdmin sample configuration, you can use it as base for
 * manual configuration. For easier setup you can use scripts/setup.php
 *
 * All directives are explained in Documentation.html and on phpMyAdmin
 * wiki <http://wiki.cihar.com>.
 *
 * @version $Id: config.sample.inc.php 10142 2007-03-20 10:32:13Z cybot_tm $
 */

/*
 * This is needed for cookie based authentication to encrypt password in
 * cookie
 */
$cfg['blowfish_secret'] = 'PUT SOMETHING HERE'; /* YOU MUST FILL IN THIS FOR COOKIE AUTH! */

/*
 * Servers configuration
 */
$i = 0;

/*
 * First server
 */
$i++;
/* Authentication type */
$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'tcp';
$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
$cfg['Servers'][$i]['extension'] = 'mysql';
/* User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'pma';
// $cfg['Servers'][$i]['controlpass'] = 'pmapass';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = 'PASSWORD FOR MYSQL ROOT';
/* Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';

?>[/php]

---

### Post by Findarato on 2007-10-26
it seems this file is not configured on my computer.
I don't understand it though, I got :
```

/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/* Authentication type */
//$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
//$cfg['Servers'][$i]['host'] = 'localhost';
//$cfg['Servers'][$i]['connect_type'] = 'tcp';
//$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
//$cfg['Servers'][$i]['extension'] = 'mysql';
/* Optional: User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'pma';
// $cfg['Servers'][$i]['controlpass'] = 'pmapass';
/* Optional: Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';

```
at the moment.

I see the $cfg['blowfish_secret'] = 'PUT SOMETHING HERE'; /* YOU MUST FILL IN THIS FOR COOKIE AUTH!'  is missing, but if you could guide me through it it would be really nice, sorry for being a noob :(

---

### Post by scxtt on 2007-10-26
looks like 99% of it is comments, wrap it in [ php ] [ /php ] tags and you'll see a lot of orange (your post above, not the file - tho i don't see <?php ?>) ... you'll need to make it look more like mine (i.e. uncomment the important stuff), but change the things i put in ALL CAPS ...

---

### Post by Findarato on 2007-10-26
> **scxtt said:**
> looks like 99% of it is comments, wrap it in [ php ] [ /php ] tags and you'll see a lot of orange (your post above, not the file - tho i don't see <?php ?>) ... you'll need to make it look more like mine (i.e. uncomment the important stuff), but change the things i put in ALL CAPS ...

okis, did that, have it open atm, only what do I put around
cfg['blowfish_secret'] = 'PUT SOMETHING HERE'; ?

a path of some kind?

---

### Post by scxtt on 2007-10-26
i'm not sure what the point of that is, maybe some "behind the scenes" handshake-type stuff -- just put some word in  there, in l33t-speak :p like "8l0vvf15h" ;)

---

### Post by Findarato on 2007-10-26
I still get the following error:
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

---

### Post by scxtt on 2007-10-26
you'll have to check those errors in the logs it's talking about and be sure mysqld is running and the "root" account is config'd correctly (i.e. you can connect via CLI: mysql -u root -p)  ...

---

### Post by Findarato on 2007-10-26
and where might I find those logs? :)

*edit* found em, but can't open em

I checked up phpinfo() and my sessions should be saved in /var/lib/php5 only the file is empty, that normal? I know mysql is set up ok, I already used it yesterday and just before we started trying to acces phpmyadmin :P

---

### Post by Findarato on 2007-10-26
I reinstalled the whole thing (LAMP) and have the same problem again. Somehow phpmyadmin isn't accessible from localhost/phpmyadmin any ideas why?

---

### Post by scxtt on 2007-10-27
/var/lib/php/session is a directory, not a file - there would be files in that directory ... i've never had problems w/ php sessions or really even dealt w/ them - can't help there ...

w/o sitting in front of your box, i doubt i'm going to be able to effectively troubleshoot the phpadmin prob ... maybe there's some problem w/ the LAMP setup site ...

---

### Post by scxtt on 2007-10-27
i made a 7.10-server VM and let it install LAMP ... then i did **aptitude intstall phpmyadmin** and navigated to **[http://localhost/phpmyadmin](http://localhost/phpmyadmin)** -- worked fine, it even [ picked up on / used ] the **root** mysql p/w i set up during 7.10-server install ...

i'd say there's a flaw somewhere in the directions you used ... either that, or they're not compatible w/ the Ubuntu release you used ... took me under 30min to get up and running from start --> finish :D

---

### Post by u_kraze on 2007-10-28
> [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)well u can try this
i am abotu tot ry it ive got ur same problem and its a friggin headache but i still luv linux/ubuntu

---

### Post by #Reistlehr- on 2007-10-29
lol, best bet is to compile everything from source, and add phpmyadmin as an alias to the apache config file. Saves so much headache, and masks the whole permissions problem.

---

### Post by pfwd.tech on 2007-11-03
> **scxtt said:**
> let's start simple, do you know if apache is working fine?  can you put a file such as /var/www/index.html w/ something like "this is a test" and use [http://localhost/index.html](http://localhost/index.html) to view it?

if so, it'd probably be as simple as:

sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin

then going to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
(keep in mind there's still some [relatively easy] phpmyadmin-specific setup involved w/ config.inc.php)
Hi [[IMG]http://ubuntuforums.org/customavatars/avatar120471_3.gif[/IMG]]("http://ubuntuforums.org/member.php?u=120471") 			 			 				 					 					[scxtt, ]("http://ubuntuforums.org/member.php?u=120471")
I've had this problem but used your soloution and it worked.  What  does  sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin do?  Does it move the folder from one place to the next? and how did you know it was going to be /usr/share?
Thanks for the fix.  Was a life saver

---

### Post by scxtt on 2007-11-04
**ln -s** creates what's called "symbolic link" ... and "ln -s /usr/share/phpmyadmin /var/www/phpmyadmin" specifically says "anytime apache calls for /var/www/phpmyadmin, *pretend* it was a direct call to /usr/share/phpmyadmin" ... so instead of having 2 copies, or moving files around - you can say that any reference to A just points to B ... if you were to do an **ls -l** on /var/www you should see phpmyadmin 'point to' (denoted w/ an ->) /usr/share/phpmyadmin ...

i knew it was /usr/share since that seems to be a typical phpmyadmin convention, independent of Ubuntu (or any OS) ...

---

### Post by pfwd.tech on 2007-11-04
Ah thank you - I should of known that

---

### Post by jollins69 on 2009-11-05
i had this problem too. had to run 

```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

to get it to work. 

cheeeerrrrzzzz

---

