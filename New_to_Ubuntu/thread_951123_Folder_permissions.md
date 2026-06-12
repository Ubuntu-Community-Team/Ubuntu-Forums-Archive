---
title: "Folder permissions"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-10-17
I am a newbie at Ubuntu I have installed 8.04 Hardy Xubuntu on my notebook system.  I am the sole user I have the user name and password for the system.  When I try to write to a folder I get permissions denied error.  I have gone to that folder in the file manager, properties and clicked on the permissions tab all the dialog boxes access, group, access, & others are greyed out how can I change these so I can change to a read write file?  All help will be greatly appreciated.

James in GA,USA

---

### Post by seuzy13 on 2008-10-17
Open a terminal and type:
[COLOR="DarkGreen"]sudo chown *yourusername* *foldername*[/COLOR]

This "should" ungrey the permissions tab. If this does not work, try
[COLOR="DarkGreen"]sudo chmod a=rwx *foldername*[/COLOR]
You may or may not need the "sudo."

---

### Post by Dr Small on 2008-10-17
Please read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by seuzy13 on 2008-10-17
He's right. Reading that article would probably help you understand better than blindly typing in commands.

---

### Post by snova on 2008-10-17
What are you trying to write to? You shouldn't be messing with system files, or putting ANYTHING ANYWHERE but in /home/<username>.

Just thought I'd check...

---

### Post by JKHinton CPBD on 2008-10-18
Maybe thats my problem I am trying to copy my web development files from my windows xp htdocs folder to /var/www/mywebfolder so they can be read from localhost in the firefox browser. I have this set up on 2 Kubuntu systems but I am not able to copy anything to this folder in Xubuntu.  Thanks to Seuzy13 but the commands didn't work,Thanks to Dr Small and snova but I still cannot open this folder for writing files.

---

### Post by beno1990 on 2008-10-18
If you're trying to add files to the web server directory, just add your account to the www-data group in the users and groups management.

---

### Post by jerome1232 on 2008-10-18
You can also change the default directory apache looks in for the site. (like something in your ~/)
[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

---

