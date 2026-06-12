---
title: "php search example, but firefox tries to open php file using dialog box"
date: 2011-01-13
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-13
[http://www.weberdev.com/ViewArticle/How-To-add-paging-%28Pagination%29-with-PHP-and-MySQL](http://www.weberdev.com/ViewArticle/How-To-add-paging-%28Pagination%29-with-PHP-and-MySQL)

following this, I think you create a file called Search.htm
put that text in.

create a file called Search.php, and put that text in there

then open the Search.htm, type in the search item.
when I do this firefox opens a dialog to save the file.

---

### Post by sdowney717 on 2011-01-13
Chrome downloads the file as well, so what is the problem?

---

### Post by fct on 2011-01-14
Almost certainly server configuration. Apache must have the php module correctly installed, and the MIME type for PHP files be correctly set up.

Edit: see here:
[http://ubuntuforums.org/showthread.php?t=287876](http://ubuntuforums.org/showthread.php?t=287876)

---

### Post by sdowney717 on 2011-01-14
what I got out of that was either purge everything and install lamp
or try this
> Also Confirmed:

After NUMEROUS checks, apache restarts, etc.
Quote:
sudo apt-get install php-config
did the trick!


-supernova_hq

but that file does not exist?

> scott@scott-desktop:~$ sudo apt-get install php-config 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libenet0debian1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  php-pear
Suggested packages:
  php-xml-parser php-xml-util php5-dev
The following NEW packages will be installed:
  php-config php-pear
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 363kB/397kB of archives.
After this operation, 3,011kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main php-pear all 5.3.3-1ubuntu9.2
  404  Not Found [IP: 91.189.88.30 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main php-pear all 5.3.3-1ubuntu9.2
  404  Not Found [IP: 91.189.92.166 80]
[B]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php-pear_5.3.3-1ubuntu9.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php-pear_5.3.3-1ubuntu9.2_all.deb)  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/B]
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2011-01-14
[http://www.phpbuilder.com/board/archive/index.php/t-10221911.html](http://www.phpbuilder.com/board/archive/index.php/t-10221911.html)

AddType application/x-httpd-php .php .html

[http://www.linuxquestions.org/questions/linux-server-73/apache-not-parsing-php-on-ubuntu-8-04-a-829927/](http://www.linuxquestions.org/questions/linux-server-73/apache-not-parsing-php-on-ubuntu-8-04-a-829927/)

so can i make that file since it does not exist on my system?
/etc/httpd/httpd.conf

---

### Post by sdowney717 on 2011-01-14
ok, you dont need to reinstall anything

what you do is add a single line to an empty file
in /etc/apache2/httpd.conf 
this is it, opened with gksu nautilus, then browse to file and add that line

AddType application/x-httpd-php .php .html


then restart apache2
sudo /etc/init.d/apache2 restart

and it works.
So why is that so hard, why is that not already there?

---

