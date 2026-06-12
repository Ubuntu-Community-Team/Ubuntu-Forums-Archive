---
title: "Issues with LAMPP, rights"
date: 2007-03-24
forum: Programming Talk
---

### Post by Petar Marjanovic on 2007-03-24
Firstly, I've to tell you that my English isn't very good. But I want to try to tell you my problem.

I want to programm PHP-Scripts on Ubuntu. To show them in the browser I installed LAMPP (apachefriend.org). My htdocs-Folder path is: /opt/lampp/htdocs. You can see: It's a folder where I (as a user) don't have rights to create any files. So I opened the folder with sudo, set the rights (for make possible to create any files and folders) and created then a PHP file with the content:

[PHP]<?php print("hello ubunut-world.") ?>[/PHP]

But the output was:

```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/opt/lampp/htdocs/test.php' (include_path='.:/opt/lampp/lib/php') in Unknown on line 0
```

So i gave the file the rights 644, and it worked correctly. But it's very arduous to set always the new created files the execute-rights. In the German Wikipedia a user said to me, to go into the htdocs-folder, to put "umask 777" into the shell and it will work. But it don't work. New created files haven't stil execute-right.

Can someone tell me how to solve the issue? Otherwise if there is a German speaking user: In the [Ubuntuusers-Forum]("http://forum.ubuntuusers.de/topic/81497/") (Germany) there is a thread in German.

----------------------
I'm now trying to install the server modules (apache, php and mysql) manual. Perhaps there are less issues using the folder /var/www/.

---

### Post by Petar Marjanovic on 2007-03-24
So, I installed the modules manually. MySQL, Apache2 and PHP work correctly. But the problem is stil here:

When I create a PHP-file e.g. called test.php into the folder /var/www/ in user-mode (nautilus), the browser says again the same error. In root-mode, the same error. Just when the file have the rights as a www-data user, it works correctly.

How can I set the folder that he gives all new created and copied files the user-rights "www-data"?

---

### Post by Mirrorball on 2007-03-24
In my system, /var/www/ is set to 755 and I never had any permission problems.

---

### Post by jenhsun on 2007-03-24
Peter, check this site for some setting
[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)
It might solve your problem :)

---

### Post by Petar Marjanovic on 2007-03-24
> **Mirrorball said:**
> In my system, /var/www/ is set to 755 and I never had any permission problems.
My folder also is set to 777. I set it to 777 in root-mode. I only can put files into the folder in root-mode (when nautilus is started by sudo), and afterwards I must set all files to "www-data", because the process php5 can only compile files with rights www-data.

> Peter, check this site for some setting
[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)
It might solve your problem 
This site is not very helpful, it won't solve my problem. :(

---

### Post by jenhsun on 2007-03-24
I don't know about PHP. But ....
Is that possible you lost ; ?

So you did setup mod rewrite and apache allowoveride, right?

---

### Post by Petar Marjanovic on 2007-03-24
> **jenhsun said:**
> I don't know about PHP. But ....
Is that possible you lost ; ?

So you did setup mod rewrite and apache allowoveride, right?
No. PHP Scripts are text-files where into is the source code. This source must the process "php5" compile/execute. And new created files doesn't have enough rights to be compiled/executed.

---

### Post by Mirrorball on 2007-03-24
Why don't you install apache and php from Ubuntu's official repositories?

---

### Post by jenhsun on 2007-03-24
Peter, I do a googleing for your problem, then I found there exist so many similar questions like yours. I am not sure why you choose this package because of Perl? If you don't need perl at the beginning, you can try LAMP as your first start. 
You can use edgy to install all these packages step by step and run your php without any problem. I know that because I just tried to setup my server recently. Clean and simple.

---

### Post by nandasunu on 2007-03-24
I use lampp for my php/apache/mysql setup also. I find the simplest way to avoid all the permissions problems is to create folder with your home directory to store all your web projects (eg "www"), then go to the root directory of your htdocs (e.g. "/opt/lampp/htdocs" or "/var/www") and create a symbolic link to your "www" directory in your home folder.

You can do that in a terminal by using the following:

```
cd /opt/lampp/htdocs
sudo ln -s www /home/username/www
```

replace "username" with your username of course. I am not at home on my ubuntu machine right now so I can't test that command, I can't remember if the target for the link comes before or after.

Anyway, once that is set up you can freely edit the files from your home folder and they will show up in: [http://localhost/www](http://localhost/www). If you get permission errors with those files, make sure you have set the permissions so that other groups have read access to the files. 

This is how I locally work on my php files, I hope it helps.

---

### Post by jenhsun on 2007-03-24
> **nandasunu said:**
> I use lampp for my php/apache/mysql setup also. I find the simplest way to avoid all the permissions problems is to create folder with your home directory to store all your web projects (eg "www"), then go to the root directory of your htdocs (e.g. "/opt/lampp/htdocs" or "/var/www") and create a symbolic link to your "www" directory in your home folder.

You can do that in a terminal by using the following:

```
cd /opt/lampp/htdocs
sudo ln -s www /home/username/www
```replace "username" with your username of course. I am not at home on my ubuntu machine right now so I can't test that command, I can't remember if the target for the link comes before or after.

Anyway, once that is set up you can freely edit the files from your home folder and they will show up in: [http://localhost/www](http://localhost/www). If you get permission errors with those files, make sure you have set the permissions so that other groups have read access to the files. 

This is how I locally work on my php files, I hope it helps.

Yap, this is great. I always wonder what chmod is better for web site security.
A symbolic link might solve the problem too.

---

### Post by nandasunu on 2007-03-24
> **jenhsun said:**
> Yap, this is great. I always wonder what chmod is better for web site security.
A symbolic link might solve the problem too.

yes, I don't mess with the chmod at all on the htdocs folder.

---

### Post by Petar Marjanovic on 2007-03-26
A friend told me that I should put the user "www-data" into my user-group. Then I should put this row into the file called ".bashrc": umask 0022.

But it doesnt really work. Now a PHP-file needs just read-rights as group-user. But this right I stil should set manual.

---

### Post by Mirrorball on 2007-03-26
Why don't you try the Servers & Security forum?
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

---

### Post by Petar Marjanovic on 2007-03-26
Because I'm new here and I didn't see it. And ... btw, i don't want to start a proffesional server ... just to play with PHP, MySQL etc.

---

### Post by Mirrorball on 2007-03-26
Just install the Apache, mod_php packages in Synaptic. I never had any permission issues with them.

---

### Post by Petar Marjanovic on 2007-03-27
This packages are installed (in Synaptic):
apache2, libapache2-mod-php5

php(*.)-cgi is removed.

A new created file (in usermode) have this chmod: 600. Error:
```

Forbidden

You don't have permission to access /lala.php on this server.
```

Same file, chmod 777:
No error, but an alert: Firefox wants to download this file.

*cry*

---

### Post by Mirrorball on 2007-03-27
Are the files php5.conf and php5.load in /etc/apache2/mods-enabled/? If not, link them from /etc/apache2/mods-available/ and restart Apache.

---

### Post by Petar Marjanovic on 2007-03-28
They are not in /mods-enabled/. How can I link them? // done

Now every PHP file I can run. The problem now is, that apache2 wants to give this php-file as a download. How can I solve this?

---

### Post by Mirrorball on 2007-03-28
But it shouldn't. It's a sign that modphp is not enabled. Did you restart Apache?

---

### Post by Petar Marjanovic on 2007-03-28
sudo apache2 -k restart, I did.

I'm going to do a complet restart.

---

### Post by Petar Marjanovic on 2007-03-28
Merda. The download window doesn't come any more.

But now there's the ******** same problem!

-> look at attachment.

---

### Post by Mirrorball on 2007-03-28
:( Uninstall Apache and mod_php completely, deleting everything in /etc/apache2 and /var/www, reinstall. Sorry, I wish I knew what is wrong with your current installation.

---

### Post by Petar Marjanovic on 2007-03-30
petar@petar-desktop:~$ sudo apache2 -k start
apache2: could not open document config file /etc/apache2/apache2.conf

---

### Post by Petar Marjanovic on 2007-04-01
Nobody knows the reason?

---

### Post by oliver_21 on 2007-04-05
I am not shure if I got it now, but the main problem will be that you write your php files as a different user than apache is.
Please check (in httpd.conf) which user / group apache is.
You(the writer of php-code) should be a member of this group.
*The /etc/group files are configured with the same general format across platforms. It lists the groups that have been created on the system and who is in each group. Groups can be managed by creating new lines in the file following the convention, users can be added to an already existing group by adding the new username to the end of the other usernames or after the semicolon of the gid if there are no other members.* 
from [http://www.cae.wisc.edu/site/public/?title=linaccounts]("http://www.cae.wisc.edu/site/public/?title=linaccounts")

if it is not, then the files the php writer makes  must  have the minimum rights 0664
which look like "-rw-rw-r--" but the directory must have as minimum 0755 which looks like "drwxr-xr-x".

Another Problem could be the DocumentRoot(in httpd.conf)

---

### Post by counterpoint on 2007-04-10
I understand and sympathise with Petar's problem.  I only wish I had a solution.  For people trying to help, may I just clarify one thing - the issue is not any fundamental failure in the PHP installation or its operation.  My installation works just fine (as Petar's probably does) in normal use.  The problem is how to develop efficiently.

Dare I say it is simple on Windows?  Although I'm putting a lot of effort into building a Linux development environment, this problem is extremely frustrating.  With Windows and its lack of file permissions (in any significant sense) the following setup is no problem:

* Default installation of Apache, MySQL and PHP
* Several testing sites using vconf
* A sophisticated PHP system that includes browser based management and therefore itself installs many of the files
* An editor, or better an IDE such as Maguma Studio or Zend Studio that can access the files in the various vconf document roots and make amendments which have immediate effect on tests carried out using a browser and the local Apache
* Subversion source control applied to the PHP files that are all under the vconf document root in one or another test site.

If I've understood correctly, Petar's problem is to create this kind of setup in an Ubuntu environment (it's certainly my problem).  Why is it difficult?

There are a number of factors that work against you.  The default installation of Apache that you get by simply using apt-get install runs as the "user" www-data and group www-data.  But these do not appear in user/group management and may not be real user/group names (I don't claim to understand this in any detail).  You can't simply make yourself a member of the www-data group.  I've tried changing the user/group in Apache to my own user/group.  This works up to a point, but the implications are not all obvious and I get errors that are hard to understand or fix.  I also have another problem that will be posted separately.

A symbolic link between the Apache virtual (vconf) document root and a subdirectory off the user's home will make the files appear to show up, but does not alter the permissions.  So if they belong to www-data then unless the file permissions are very liberal, you can't edit them.

Running with very liberal permission settings such as 777 will work for a while, but if additional files are created via the browser, then these will not be 777 by default.  Also, this is an unnatural way to run the system, which may disguise problems that will occur in live deployment.

The ultimate solution appears to use some form of PHP suexec, since the web server then runs scripts as the site owner.  It is then feasible for the developer to be the site owner and have all files (old or new) created under their ownership.  This setup works fine in live use, or for testing against a remote host.  But development is slow, because every change has to be made on one version of the system, and then copied to the testing system.  

So implementing PHP suexec on the local PC would be a solution - I've shied away from doing it because attempts to make a crude and simple suexec implementation have not worked. If you're running an ISP then it makes sense to persevere and put in the effort to make PHP suexec work, as it is much the best environment for sophisticated PHP systems and (on balance) the best way to tackle the security issues of multi-site hosting.

But as a developer, I want to get on with development!  So if there is a simpler solution that will allow me to create the setup outlined above, I'd be very pleased!

---

### Post by coxy on 2007-04-10
Apologies if this has already been said but I only have the time to briefly skim the posts. If you have set the umask to 777 then you are setting the permissions to 000 when a file is created. umask works in a different way to chmod.

You subtract your umask from the permissions, I will try to explain the best I can.

umask of 777

  777
- 777
=000 permissions

umask of 022

  777
- 022
=755 permissions

That is the most basic way I can think of to explain it. If you have set a umask of 777 then that is possibly causing your problems. If I have missed the point of missing something in my fast read of the post then apologies.

---

### Post by counterpoint on 2007-04-10
That's correct, but how do you permanently set the umask for www-data?  I know how to set my own umask temporarily, but not how to set it permanently for www-data which is the Apache user.  (Am I correct in the assumption that umask is set per user?).

---

### Post by richardelima on 2012-01-07
how can i grant access to the table to actual user, being they owned by nobody:root, without having to chown the folder? (because i sync daily bases witha windows db wich changes the owner to the actual user.

---

