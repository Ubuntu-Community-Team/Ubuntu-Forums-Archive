---
title: "Git - FTP gvfs issue"
date: 2017-06-23
forum: Programming Talk
---

### Post by sir-requiem on 2017-06-23
I'am trying to use an ftp gvfs mount in combination with git 


The problem is that every time i try to clone the repository to my gvfs mounting point 
the git command breaks after successful creation of the project folder and .git folder.

The actual project files are not copied and i get:


user@PC: cd /run/user/1000/gvfs/ftp:host=IP/modules

user@PC: /run/user/1000/gvfs/ftp:host=IP/modules$ git clone https_repository_addr
Cloning into 'roccoroles'...
Segmentation fault (core dumped)

creates the project and .git folder




I think the problem is created by some user right issues.
Running as root makes it worse:

user@PC: /run/user/1000/gvfs/ftp:host=IP/modules$ sudo git clone https_repository_addr
fatal: could not create work tree dir 'roccoroles'.: Permission denied

user@PC: /run/user/1000/gvfs/ftp:host=IP/modules$ sudo -s
root@PC: /run/user/1000/gvfs/ftp:host=IP/modules$ git clone https_repository_addr
fatal: could not create work tree dir 'roccoroles'.: Permission denied

creates nothing and just breaks




I also get an error when i'am running nautilus as root and try to connect and display the folder 

user@PC: gksu nautilus
In nautilus entering [ftp://IP/](ftp://IP/) into the address field, results in:

This location could not be displayed.
You do not have the permissions necessary to view the contents of “IP”.



The visited location is /run/user/1000/gvfs/ftp:host=IP/modules again.



I would love to use git with my gvfs mountpoint. 


Thanks for your help in advance!  :)

---

### Post by TheFu on 2017-06-23
Welcome to the forums.

gvfs and ftp aren't normal file systems.  Expecting them to behave like a Unix/Linux file system is a complete failure.  Local permissions (your desktop) have ZERO to do with remote permissions (the FTP server).

I have lots of other issues with what you are attempting.  I wouldn't do it, but perhaps someone else is willing to help with a useful solution?

Just because something seems possible doesn't make it a good idea.

I would use standard git commands over ssh for everything you are attempting. I wouldn't put anything on a plain FTP server (that is a personal security choice).

---

