---
title: "apache and phpmyadmin directory"
date: 2008-08-17
forum: Programming Talk
---

### Post by smithveg on 2008-08-17
Hi, i have apache, php, and phpmyadmin installed in my ubuntu machine.

I have some problem:
1. Where is the phpmyadmin directory? I can't see it in ../var/www/
2. What is my default login for phpmyadmin? I do not have a password.

3. Where can i change the root directory to another drive, instead of ../var/www/

Please help.

---

### Post by khalil.majdalawi on 2008-08-17
you can find phpmyadmin files in "/usr/share/phpmyadmin" when installing phpmyadmin the installer will ask you which web server you have you have to chose what ever you have by space not enter button it will create everything you need to run it

---

### Post by raptor2552 on 2008-08-17
Maybe as a point of interest there is a phpmyadmin config file in /etc/apache2/conf.d that sets up the alias for phpmyadmin. No need to put phpmyadmin in your root directory where files could be tampered with.

---

### Post by smithveg on 2008-08-18
Hi, I found the apache setting. But i couldn't understand which file should i go to amend the root directory path.

My existing root dir, at ../var/www/
I want to change it to another drive D:\localhost\

Please help me again.

---

### Post by raptor2552 on 2008-08-18
I don't understand D:\localhost\ Please be more specific. Do you want to move the web root directory? Do you want to move the phpmyadmin directory? Do you want to move both?

---

### Post by smithveg on 2008-08-18
Let me clarify,

I have Windows and Ubuntu installed on my machine.
Drive D:\localhost is where i run the web application in the windows platform. And the phpmyadmin is reside in D:\localhost\phpmyadmin.

I have two platform. Now, i need the ubuntu apache using the root directory from D:\localhost, instead of ../var/www/

Also, i do hope that i can change the phpmyadmin path if i needed.

My point is to configure both platform sharing a same web server root directory.

---

### Post by raptor2552 on 2008-08-18
I don't know. For one thing the configuration files for Windows may be different. Using phpmyadmin on Ubuntu accessing a Windows install may not be possible. 

I suppose, and this is a guess, you would need to set up your virtual directory to point to whatever directory you have your Windows partition mounted on under Ubuntu.

Perhaps someone else on these forums has experience doing this. I do not. In fact the only reason I keep Windows around is to use Sony Vegas Movie Studio and even at that it runs as a guest OS under Virtualbox.

Sorry I can't help you more

---

### Post by mssever on 2008-08-18
> **smithveg said:**
> Let me clarify,

I have Windows and Ubuntu installed on my machine.
Drive D:\localhost is where i run the web application in the windows platform. And the phpmyadmin is reside in D:\localhost\phpmyadmin.

I have two platform. Now, i need the ubuntu apache using the root directory from D:\localhost, instead of ../var/www/

Also, i do hope that i can change the phpmyadmin path if i needed.

My point is to configure both platform sharing a same web server root directory.
Dunno if I understand you correctly, but I think that you want to modify Apache's DocumentRoot setting (see the apache manual for details). But you'll have to use the proper names for the directories. D:\localhost is only meaningful in Windows. For the Linux side, you'll have to call it by the name Linux uses. ../var/www is a relative path that depending on your current directory could refer to a different directory than you intend. Better to use an absolute path (such as /var/www) to avoid confusion.

---

### Post by smithveg on 2008-08-18
Thank you, raptor2552, mssever.

Probably the term i'm using confuse everyone in this thread.
I should say, i need the linux and window sharing a same DocumentRoot. So that my job will be more easy and convenient.

phpmyadmin doesn't matter. I can keep two set of phpmyadmin for windows, and linux. But, do hope the DocumentRoot can be share.

Let me search around..

---

### Post by mssever on 2008-08-19
> **smithveg said:**
> I should say, i need the linux and window sharing a same DocumentRoot.OK, that's easy. You, of course, have two separate apache installs; one on Win and one on Linux. Just set the DocumentRoot in each install to the path where you'll keep your files. Nothing complicated there.

---

### Post by smithveg on 2008-08-19
Hi, Still the same problem.
In the directory /etc/apache2/ all almost all the related file.

I cannot see anywhere that i can edit my documentroot path.
My existing/default document root at /var/www/
Any idea where can i changes this path? Which file should i go?

---

### Post by mssever on 2008-08-19
> **smithveg said:**
> Hi, Still the same problem.
In the directory /etc/apache2/ all almost all the related file.
In Ubuntu, look under /etc/apache2/sites-enabled.

---

### Post by smithveg on 2008-08-21
Oh, i saw the line of code that should i modify.

In Computer,
I have the following dir,
- CD Rom
- Filesystem
- Data Disk
- 26.3 Media

I want to point to Data Disk's 'localhost' directory.
Any ideas how can i write the path?

---

### Post by mssever on 2008-08-21
> **smithveg said:**
> Oh, i saw the line of code that should i modify.

In Computer,
I have the following dir,
- CD Rom
- Filesystem
- Data Disk
- 26.3 Media

I want to point to Data Disk's 'localhost' directory.
Any ideas how can i write the path?
I take it: a) this is the Linux side you're referring to; and b) you're using Nautilus to navigate your filesystem, not the terminal. In that case, once you've navigated to the proper directory, hit <Ctrl>L and Nautilus will display the path to the current directory. That's what you want.

---

### Post by smithveg on 2008-08-22
Oh, thank for pointing me how to get the directory path, by <ctrl> + L

I got no permission to edit the sites-enabled file.
How can i gain the admin permission to do that changes?

---

### Post by mssever on 2008-08-22
> **smithveg said:**
> Oh, thank for pointing me how to get the directory path, by <ctrl> + L

I got no permission to edit the sites-enabled file.
How can i gain the admin permission to do that changes?
Use sudo if you're working with terminal-based programs, and gksudo for graphical programs. For example, you could hit <Alt>F2 and type ```
gksudo gedit
```then use gedit's open command to open the file you want.

---

### Post by tinny on 2008-08-22
I wish more people would used [MySQL GUI Tools]("http://www.mysql.com/products/tools/") (available in the repositories), it really is a collection of superior tools.

---

### Post by mike_g on 2008-08-22
Cool, I'll check that out. I like phpMyAdmin, but HTML forms make such a sluggish interface.

---

### Post by tinny on 2008-08-22
> **mike_g said:**
> Cool, I'll check that out. I like phpMyAdmin, but HTML forms make such a sluggish interface.

If you can access your MySQL port remotely (E.g. 3306) MySQL GUI tools is sooo the way to go. :)

---

### Post by nbayiha on 2008-08-26
It can't sound silly , but i want to learn how to manage Database. so my question is 
How to get to MySQL GUI i mean i did install it but how am i suppose to run it ?
I am completely new in this domain , i succeed to install apache phpmyadmin and the rest but now the question is how to run it ?
By the way if someone can point me in a real good tuto for newbies(How to use Mysql and Php) that will be cool.

Thanks in advance.:lolflag:

---

### Post by mike_g on 2008-08-26
I havent used the MySQL GUI tools yet, but for phpMyAdmin you want to open your browser and go to this url:
```
http://localhost/phpmyadmin
```

---

### Post by nbayiha on 2008-08-26
This is what i have when i do so 
> The requested URL /phpmyadmin was not found on this server.
I just call a friend to ask me what to do and he told me that i have to configure apache but i don't know how to do so.

_Edit:_
i just try those command to link phpadmin 
```
cd /var/www/
sudo ln -s /usr/share/phpmyadmin/ phpmyadmin
```

and now when i browse this [http://localhost/phpmyadmin](http://localhost/phpmyadmin) 
i have a file that want to be downloadeded ? A php file.
What to do?
Thanks

_2Edit_ Ok i succed to configure it and now i have a problem about user name and password, how to configure them .I remember myself giving a password while installing those stuff, but i gave no username :?

The Username by default is_ root _ silly from , i should have read first. :D

---

### Post by smithveg on 2008-09-06
> **mssever said:**
> Use sudo if you're working with terminal-based programs, and gksudo for graphical programs. For example, you could hit <Alt>F2 and type ```
gksudo gedit
```then use gedit's open command to open the file you want.alter table customers add column cust_company varchar(36) after cust_id

gksudo gedit /etc/apache2/........

---

### Post by smithveg on 2008-09-06
Hi,

I have changed. the documentroot from /var/www/ to
/media/Data Disk/localhost/

Why the localhost/index.php cannot be surf in my browser.
Probably my path was wrong?

I guess that is the correct path. And this is the path i see when i <ctrl> + L in /localhost/ directory.

Any ideaS?

---

### Post by mssever on 2008-09-06
> **smithveg said:**
> Any ideaS?
First, what error did you get when you tried to browse there? Second, what error do you get in Apache's logs?

It's possible that Apache doesn't like paths containing spaces. This is just a guess, though, since I've never tried that. It's also possible that there are permissions problems. At any rate, we can only guess until you provide the information requested.

---

