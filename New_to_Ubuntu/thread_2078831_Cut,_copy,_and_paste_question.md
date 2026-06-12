---
title: "Cut, copy, and paste question"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by goniophoto guy on 2012-10-31
Hello all,
Total noobie here.  I've read tons of articles on how Linux <> Windoze and I get it.   I've got my puter set for dual boot until I start thinking Linux and I figure the best way to get there is to just get in over my head.

I'm working on Ubuntu 12lt with apache2 and php5.  It took some time to learn the different file system locations of everything but I think I'm getting it.  I'm trying to work on developing my website in Ubuntu. Usually in windows I use cut and paste in my apache httpd folder and then test  using localhost.   I've noticed that Linux will not allow this on root.  I've also noticed that Linux is heavily command line driven. While this is more powerful and probably safer too I find it's too slow to be productive. How do I cut and paste on root or is my problem I'm still thinking in windows.....? Please help. Some help on how to unlock root or how to redirect apache to my home folder or what's the best Linux way would help too. I'm a little lost, I've noticed the apache.conf file is totally different from windows. Thanks for any help and don't assume I know anything Linux.

---

### Post by evilsoup on 2012-10-31
I *think* you're using 'root' to refer to a terminal (the window you're using to type in commands). To copy and paste in a terminal window, you have to use ctrl+shift+c and ctrl+shift+v (ctrl+shift+x to cut, I think).

I'm afraid I don't know anything about apache, so I can't help you with that.

---

### Post by alphacrucis2 on 2012-10-31
> **goniophoto guy said:**
> Hello all,
Total noobie here.  I've read tons of articles on how Linux <> Windoze and I get it.   I've got my puter set for dual boot until I start thinking Linux and I figure the best way to get there is to just get in over my head.

I'm working on Ubuntu 12lt with apache2 and php5.  It took some time to learn the different file system locations of everything but I think I'm getting it.  I'm trying to work on developing my website in Ubuntu. Usually in windows I use cut and paste in my apache httpd folder and then test  using localhost.   I've noticed that Linux will not allow this on root.  I've also noticed that Linux is heavily command line driven. While this is more powerful and probably safer too I find it's too slow to be productive. How do I cut and paste on root or is my problem I'm still thinking in windows.....? Please help. Some help on how to unlock root or how to redirect apache to my home folder or what's the best Linux way would help too. I'm a little lost, I've noticed the apache.conf file is totally different from windows. Thanks for any help and don't assume I know anything Linux.

If you are trying to paste files into the httpd folder from nautilus (gui file manager) then that will not work as it doesn't have the access rights. You could run nautilus as root I suppose but be careful. You would do that by entering the terminal command:

```
gksu nautilus
```

It will prompt for your password and then run nautilus with super user privileges. Then you will be able to paste the files but take extreme care not to blow away any system files or folders.

---

### Post by mcduck on 2012-11-01
If youa re just using the AOPache on your computer for testing and development, and it's not an actual production server, the easiest way in my opinion is to configure Apache to sue a directory in your home as the document root. That allows you to easily create and edit the files inside your home, as your  own user, without having to deal with permissions (apart from maing sure Apache has read permissions of the files).

The configuration files for web sites for Apache are in /etc/apache2/sites-available, and what you'd want to do is make a copy of the "default" site configuration, rename it ("mysite", for example), change the document paths to point to a location in your home (/home/*yourusername*/WWW, for example), and then run "sudo a2dissite default" to disbale the default site, followed by "sudo a2ensite *mysite*" to enable the new configuration. After that you might need to run "sudo service apache2 restart".

Ubuntu's server guide has pretty good docuymentation about enabling, disbaling and configuring Apache, I really recommend taking a look there as well: [https://help.ubuntu.com/12.10/serverguide/httpd.html]("https://help.ubuntu.com/12.10/serverguide/httpd.html")

---

### Post by COMECON on 2012-11-01
You can also change the **htdocs** folder permissions. On a "real" server I shouldn't do that, but on a testing localhost...
```
$ sudo chmod -R 777 /path/to/htdocs
$ sudo chown -R yourusername /path/to/htdocs
```
Then you should be able to cut, copy and paste on the htdocs folder through Nautilus or the Terminal, with your account.

---

