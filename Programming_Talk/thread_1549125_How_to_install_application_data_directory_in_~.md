---
title: "How to install application data directory in ~"
date: 2010-08-09
forum: Programming Talk
---

### Post by danwsc on 2010-08-09
Hi,

I'm trying to write an application that makes use of a number of files stored in a application data directory.  At the moment I've put the data directory in ~/.myapp/$USER.default/data
The things is that if my application is installed by say dpkg -i, then it would need superuser privilege so I would need to do 
$ sudo dpkg -i ......

Only problem is that once I use sudo, the $USER becomes root and the $HOME becomes /home/root, not the /home/user that my application would look in once it is running.

I've gone through some of the earlier posts and there is one quite similar but I guess I'm too new to Linux to figure out the solution from the replies.  I saw someone refer to XDG_DATA_HOME but when I
$echo $XDG_DATA_HOME

I get only a blank and further, won't the user name also change to root once I use sudo?

Please help.  This problem has held my work back for quite some time.

Thanks in advance.

---

### Post by nvteighen on 2010-08-09
The usual approach is the following:

1. You only install application data that is going to be used for the application regardless of who the user is. When the program is installed system-wide, this data usually goes either to /etc or /var, depending on what it is (configuration files or cache-like stuff, respectively).

2. Data that's user-specific is usually generated somehow when the program's started for the first time by a certain user. If the data is small, you can insert the default settings in the source code itself... if it's long, the usual approach is to have a default system-wide version at /etc that's copied to ~ and things are set up that way that the local version always overrides the system-wide one (e.g. /etc/bashrc vs. ~/.bashrc).

That way, you solve all the issues you mentioned.

---

### Post by danwsc on 2010-08-09
Thanks a lot!
 
Regards.

---

### Post by danwsc on 2010-08-10
Just thought of something ... 
 
So what happens for uninstall?  postrm could take out the directories put in during postinst, but not those that were copied to the user home unless there was a record somewhere?
 
Regards.

---

### Post by nvteighen on 2010-08-10
> **danwsc said:**
> Just thought of something ... 
 
So what happens for uninstall?  postrm could take out the directories put in during postinst, but not those that were copied to the user home unless there was a record somewhere?
 
Regards.

If you look at your home, you'll sure find a lot of configuration data lying around for applications you've uninstalled. It is annoying in most cases, but it can also be useful for keeping data that you might recover when reinstalling the program (e.g. you're installing a new GNU/Linux distro and you have a separate /home partition... you'll have to reinstall applications, but the user configuration will be still there).

---

