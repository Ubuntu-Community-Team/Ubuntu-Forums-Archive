---
title: "XAMPP Error Message"
date: 2009-03-22
forum: Programming Talk
---

### Post by s.fox on 2009-03-22
Hi,

I just set up XAMPP following [this]("http://ubuntuforums.org/showthread.php?t=223410") guide.  I am getting some errors when starting XAMPP though :(

```

sudo /opt/lampp/lampp start
[sudo] password for ash: 
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Another FTP daemon is already running.
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP for Linux started.
ash@ash-desktop:~$ /opt/lampp/bin/mysql.server: 334: log_success_msg: not found

```

It should be pointed out that XAMPP is started and it does work.  I am just wondering about the error messages.   Can anybody help?

Many thanks,

Ash R

---

### Post by slavik on 2009-03-22
please use the repo provided packages.

sudo tasksel

select LAMP server.

---

### Post by s.fox on 2009-03-22
> **slavik said:**
> please use the repo provided packages.

sudo tasksel

select LAMP server.

Hey that fixed it.  Thank you ever so much.   I didn't realize that it wasn't using repo packages. :D

---

### Post by s.fox on 2009-03-23
Hi,  

Sorry  for the double post but...

I seem to have misplaced where I can put my files to run as localhost.   Where I used to put the files doesn't work anymore. :(

Can anyone offer any assistance?

Thank you.

---

### Post by slavik on 2009-03-23
/var/www/

or enable the user_dir mod and you can put them in ~/public_html and access them at [http://localhost/~username/](http://localhost/~username/)

---

### Post by s.fox on 2009-03-26
Hi,

I can't thank you enough.  Really I can't.  Thank you very much.

One last question.   Where is phpMyAdmin located?    I  can't see it anywhere.

Thank you for any help.

---

### Post by slavik on 2009-03-26
/usr/share/phpMyadmin, but what it does is give apache a vhost config to point it to there.

learn how to setup virtual hosts for apache, they are very useful.

---

### Post by s.fox on 2009-03-28
Thanks for the help,  

That virtual host idea looks like the sort of thing I should be doing.  I have found [this]("http://www.simplehelp.net/2008/12/16/how-to-setup-virtual-hosts-in-apache/") guide which seems  to be working.   I am about to create a pointer to phpMyAdmin but the file doesn't seem to exist.  That can't be right can it?

---

### Post by slavik on 2009-03-28
which file?

---

### Post by s.fox on 2009-03-29
Hi,

/usr/share/phpMyadmin doesn't exist.

Though I know it is installed somewhere because I have used it last week on this machine.

Thanks

---

### Post by slavik on 2009-03-29
in /etc/apache2/conf.d/ there should be a file for thr phpmyadmin vhost, see what the document root is set to.

Also, use synaptic and check if phpmyadmin is installed.

---

### Post by s.fox on 2009-04-02
Hi,

First off let me say sorry for not replying sooner.  Thanks for the help you have given me.  I remain hopeful I can get this setup soon.

You'll never guess what?  I found the original phpmyadmin install.    For some reason it wants a user name and password though.  It never wanted one before.   I had  a look at the help file says run the setup.php which is located in the opt folder.   I tried that but also get prompted for a username and password.  I tried my usual login credentials and that didn't work.  Now I don't know what to do.

I also had a look in synaptic and phpMyAdmin wasn't installed apprently.  Slightly confussed but no matter.  I installed it but I am not sure what to do now.

Can someone please advise me what to do next?

Many thanks, 

Ash R
P.S. PLease note that phpMyAdmin and phpmyadmin are deliberately typed with and without the capitals.

---

### Post by s.fox on 2009-04-07
4 day bump

---

### Post by s.fox on 2009-04-08
> **Ash R said:**
>    For some reason it wants a user name and password though.  It never wanted one before.   I had  a look at the help file says run the setup.php which is located in the opt folder.   I tried that but also get prompted for a username and password.  I tried my usual login credentials and that didn't work.  Now I don't know what to do.

**Update**

I have managed to guess the password on the original install :D.  For some reason the password was set to "".  What do I need to do next?

Many thanks,

-Ash R

---

### Post by drubin on 2009-04-08
> **Ash R said:**
> **Update**

I have managed to guess the password on the original install :D.  For some reason the password was set to "".  What do I need to do next?

Many thanks,

-Ash R

Login with root and change the default password to something more secure.  :) 

Also you might want to set up a user that has only read write permisions but not drop. just so that you can use that for playing around with with out losing your data

---

### Post by s.fox on 2009-04-08
> **drubin said:**
> Login with root and change the default password to something more secure.  :) 

Also you might want to set up a user that has only read write permisions but not drop. just so that you can use that for playing around with with out losing your data

Yes thank you for the advice.  Also thank you for the help on IRC, I would otherwise be lost. :)

---

### Post by kushykush on 2009-04-08
I have installed LAMPP under Ubuntu.  However, when I type localhost in Firefox, it takes me to the "It works" page. XAMPP orange screen does not appear.  I know "It Works" is a page a webpage inside LAMPP.  How do I get to the XAMPP screen?  When LAMPP starts it does say another instance of daemon is running.  I do not see anything under system-process that tells me anything.  Need help.

---

### Post by slavik on 2009-04-08
kushykush, please start a new thread if you are having trouble. My recommendation will be to not use XAMPP.

---

