---
title: "what to back up?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by T2manner on 2008-10-26
I'm going to start backing up my system to get ready for a clean install of the new version of ubuntu coming out next thursday.
What should i backup?

---

### Post by ww711 on 2008-10-26
slash home.

---

### Post by SuperSonic4 on 2008-10-26
/home is always good.

I usually just do ~/.kde/share/apps/amarok
~/.mozilla

---

### Post by jerome1232 on 2008-10-26
Honestly depends on your usage of the system. I for one install alot of games to /opt, so I back that up.

Typicaly though all you need to backup is your /home. It contains all user files and settings.

---

### Post by dunkar70 on 2008-10-26
*That depends*...just what you wanted to here...I know. 

As ww711 said, you will most likely want the entire /home directory. This contains the user data and personalization for all users. Unfortunately, there are also a lot of hidden files, some of which will not be needed in your new installation.
The /etc directory contains the system-wide configuration files. If you have customized any of those files (i.e. Samba configuration) then save those as well. Try to keep the folder structure so you know where to put the files after the clean install.
If you have a LAMP installation, then dump your MySQL databases to a folder under /home and backup the /var/www folder, which is the default location for Apache web files.

If you have space, backup more than you think you need, but be selective about how you restore data to the new environment... you don't want to overwrite new configuration files with files from an incompatable version.

---

