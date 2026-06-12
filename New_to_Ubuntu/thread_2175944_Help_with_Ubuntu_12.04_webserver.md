---
title: "Help with Ubuntu 12.04 webserver"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by paul57 on 2013-09-22
Hello everyone, my first post here.

I have followed an online utube video [http://www.youtube.com/watch?v=SKJ55ebMcOc](http://www.youtube.com/watch?v=SKJ55ebMcOc)

This allowed me to install LAMP + Webmin + ProFTPD

No problems getting the server to work but having problems with USERS and PERMISSIONS

I'm the only user and want to access my webserver from my PC & MAC

When I create any new folders or load a CMS like Joomla I have problems writing to new folders that are created by myself or the CMS installation.

Is there a way to make it so that any new folder/files created in /var/www are always readable and writable? Or at least at a normal setting.

---

### Post by TheFu on 2013-09-22
Linux is a multi-user OS.

Different parts of the system run as different users - it is a cornerstone of security for any UNIX-like operating system. There are many, many, many good reasons why letting any user have access to /var/www is a bad idea.  You can shoot yourself in the head, if you like. Here's how:
* Add your userid to the www-data group.
* sudo chown -R {your-userid}.www-data /var/www
* sudo chmod -R g+rw /var/www
* sudo chmod g+rws /var/www
* as your-userid .... vi ~/.bashrc   then add **umask 002** to it somewhere. This assumes you use the default shell - bash.

I've never setup Joolma, so I don't know where it stores files or which user account it runs under. Modify those other directories as needed.

BTW, it would be better to setup a subdirectory under /var/www/{name-it-anything} and perform all those commands against it. Packages like apache, nginx and others will assume that /var/www is owned by www-data and might complain. It cuold become a maintenance nightmare.

Also - [almost nobody should use plain FTP anymore]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp"), sftp should be the tool of choice.

Good luck.

---

