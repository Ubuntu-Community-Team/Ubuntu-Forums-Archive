---
title: "Permissions problem!"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by bloodymind on 2008-10-07
Hello,
I'm a php developer
I have installed LAMP
and I got the www directory located in /var/www/
root is the owner of /www/ and myuser is the owner of a file inside of it called /computek/

I've logged in as root and changed the permissions of dirs and files and when i click on "apply permissions to enclosed files" nothing happens
and noone can read the files on those directories neither myuser nor root

and permissions don't wanna change!

I've also tried the terminal way:
sudo chmod 777 /var/www/
and
sudo chmod 777 /var/www/

nothing works :( !

any help will be very appreciated!

Thanx!

sorry but i've discovered that i have to go back to my user and change permissions from it beacause myuser is the owner of the dir

---

### Post by Thelasko on 2008-10-07
If you solved the problem please go up to "thread tools" and click "mark thread solved."

Thanks

---

### Post by jerome1232 on 2008-10-07
You can actually change where apache looks for the default website (so that you don't have to mess with permisions on somethign outside your /home)

This is a guide on how to get apache to look at a folder of your own choosing
[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

---

### Post by handydan918 on 2008-10-07
+1 to putting the files inside your home, but also, have you tried using ```
chmod -R
``` to change files recursively?

---

### Post by Paul41 on 2008-10-07
> **handydan918 said:**
> +1 to putting the files inside your home, but also, have you tried using ```
chmod -R
``` to change files recursively?

So to expand on this it would be...

```
sudo chmod -R 777 /var/www
```

and that would change the permissions of all files and directories inside /var/www

---

### Post by jerome1232 on 2008-10-07
Yes that would make everything under /var/www readable/writable by every user on the system. (which isn't truly desired if this is a production system I would suggest trying that guide I linked)

---

### Post by bodhi.zazen on 2008-10-07
> **jerome1232 said:**
> Yes that would make everything under /var/www readable/writable by every user on the system. (which isn't truly desired if this is a production system I would suggest trying that guide I linked)

+1

I suggest you take a little time to understand permissions rather then changing the permissions to 777, especially on a server.

Permissions : [uhelp]community/FilePermissions[/uhelp]

Server guide : [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Apache : [https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

---

### Post by handydan918 on 2008-10-07
+1 again.

---

