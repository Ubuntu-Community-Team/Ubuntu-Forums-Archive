---
title: "How do I unzip a folder with sudo to place it in rooted folders, or move the file"
date: 2015-01-29
forum: Packaging and Compiling Programs
---

### Post by hspecimen on 2015-01-29
Or how do I move the files, and what about setting them to root access only again?

In order to presumably install phpmyadmin on Ubuntu 14.04, a suggestion was made for me to unzip a folder in the system folders that require root access:

> [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

  Download phpMyAdmin from here, unzip, copy all files to /var/www/html/phpmyadmin/



I experimented with sudo mv, but I couldn't get to go.

I do not know how to do this.  I am rather inexperienced with terminal, and have only used the commands i have used.  

(apache2 is giving me a syntax error of there not being a conf file that there is supposed to be)

---

### Post by TheFu on 2015-01-29
Welcome to the forums.

Understanding UNIX processes and permissions is a key thing for system security. I don't think there is any shortcut. Learning it now will save you days, weeks, months of frustration.  It all makes sense, really. Trust me.

So - how to get the background so you are prepared to learn the file and directory permissions model?
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has recommended reading, in order.  Google only provides answers, but some level of background is required to understand those properly and no trash a system.  Blindly running chmod commands can be extremely dangerous.  So, please spend a few hours reading.

Lastly, if you want exact help, please provide exact directories and files with all permissions shown. ls -la is the command for that.

---

### Post by hspecimen on 2015-01-31
I hadn't seen that article, thanks.  Also, the following reply at a different forum was quick and to the point, I can use:

> sudo nautilus.

---

### Post by lisati on 2015-01-31
> **hspecimen said:**
> I hadn't seen that article, thanks.  Also, the following reply at a different forum was quick and to the point, I can use:
Please be careful about starting graphical applications with sudo: [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

It might be safer to unzip the file into a directory in your home folder, and if that works without problems (what if the downloaded zip file is corrupted?) you can copy the files you need to where they need to be, taking care of permissions as required.

---

### Post by TheFu on 2015-02-01
> **lisati said:**
> Please be careful about starting graphical applications with sudo.

+100! - that's a way to trade 1 problem for many others.

I recall when I was new to UNIX and file permissions were a hassle. Using root to do stuff seemed to make it all work (sudo wasn't popular), but my system was hacked a month later in just a few minutes of connection time. This was with dial-up internet and I'd connected to a government lab modem pool where I worked. 20 min and my Linux machine was completely owned.

Be careful. Very careful.  Using sudo with graphical programs can create settings in files that aren't owned by your account, so the next time you run that program, it either doesn't work at all or your settings won't save.  Plus, some very important environment variables aren't changed, so there are likely to be other difficulties.

It really is best to learn file and directory permissions and how using groups lets you have the access needed, but without going back to brute force (i.e. using sudo all the time).

---

