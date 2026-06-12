---
title: "folder permissions"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by Juan_Bonnett on 2015-01-23
Hello there!

I'm a web developer. I'm currently working with LAMP.

I developed a web application where you can manage uploads (upload them, modify the files and delete them)

Every upload process creates a new folder inside "/var/www/html/myapp/uploads"

What is happening is:

The folder is created succesfully, the files are uploaded successfully too. BUT,  I can't delete them... The NEW folder appear with a padlock, and my PHP application can't delete it nor me using the file explorer.

I need to know how can I exactly do this:

[B]Set permissions to */var/www/html/* so every NEW folder and file in there can be deleted, modified, executed by me as Ubuntu User and my Web Application.

[/B]I know you can do something like: "sudo chmod 777 /var/www/html/" but when a new folder is created it will be created with the padlock and I can't do anything to it .

Any ideas? thank you beforehand!

---

### Post by TheFu on 2015-01-23
First - don't allow a web-app to create directories that are direct parents of the application itself. This is dangerous.
Create a data subdirectory and have all the new files/directories created under there.

Ok - now that is done, the questions.
a) what userid runs your webapp? Check the process table with **ps -eaf**.
b) what are the file and directory owner/group and permissions for the directory where new directories are created?  use **ls -al /path/to/direcotry**
c) has the php.ini file been modified to allow delete?

Please do not tell us what the answers are - SHOW US USING the commands and output. For folks new to linux, they often misinterpret the output.  Copy/paste the output please.

---

### Post by Juan_Bonnett on 2015-01-23
Hello! Thanks for replying!

OK my answers are:

a) I don't know, how can I know? You mean my username?
b) www-data, and my ubuntu user already belongs to that group. With php I use the function mkdir("foldername", $permission = 0777);
c) My app works perfectly on the remote server and I haven't modified anything :/

---

### Post by whitesmith on 2015-01-23
Regardless of initial permissions, changes can be made with sudo. That's one of its key uses. For example, if you want root and only root to be able to read and write a file, then you could do:```
sudo chmod 700 /var/www/html
```in which case the ordinary file html could be modified solely by root. Many examples could be cited. Try```
man chmod
``` for more information. You could also try```
apropos chmod
```Directory access can also be so modified.

[EDIT] The utility is deceptively simple to use but getting proper end results is not. Again, look at the post by TheFu and think about questions he raises before doing or changing anything.

---

### Post by TheFu on 2015-01-23
> **Juan_Bonnett said:**
> Hello! Thanks for replying!

OK my answers are:

a) I don't know, how can I know? You mean my username?
b) www-data, and my ubuntu user already belongs to that group. With php I use the function mkdir("foldername", $permission = 0777);
c) My app works perfectly on the remote server and I haven't modified anything :/

I've updated the prior answer with more details.
If this server isn't setup to be exactly the same as that "remote server"  the fact that anything works there means nothing.  ISPs cannot run a stock setup for shared hosting, it isn't efficient.  They have to customize the virtual hosting a bunch using the same 

A basic understanding of file and directory permissions is critical to understanding basic Linux security. It applies to devices too - the keyboard, mouse, monitor, partitions, hdds, modem, network cards ... all are just files and access is controlled via file permissions.  Best to work through a tutorial (google will find many) to solidify your knowledge.

---

