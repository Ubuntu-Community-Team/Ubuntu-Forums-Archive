---
title: "[SOLVED] Codes to clean up your linux"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-27
Since i can't find any programs such as System Mechanic, CCLeaner, etc. that I had for windows, are there any terminal codes that clean up my linux from dead file links, unused icons, etc. 
I think I know that ```
sudo apt-get clean
``` cleans it, but are there any others? And if there are, what do they specifically do. Thanks in advance. :)

side-note: i know this is random, but this is one of the most friendly communities i've ever been to.

---

### Post by Zacariaz on 2008-05-27
```
sudo apt-get autoremove
```
may do a better job, I'm not quite sure how it all works...

---

### Post by sayakb on 2008-05-27
```
sudo apt-get autoremove
sudo apt-get autoclean
```Doing sudo apt-get clean deleted all packages from /var/cache/apt/archives and they would be no longer available for future use (unless you don't ever need them)

---

### Post by jrharvey on 2008-05-27
hmmmm interesting. I didnt know that linux needed cleanup programs like windows does.

---

### Post by adobrakic on 2008-05-27
--edit--
sorry, i accidentally pressed post

---

### Post by stchman on 2008-05-27
> **adobrakic said:**
> Since i can't find any programs such as System Mechanic, CCLeaner, etc. that I had for windows, are there any terminal codes that clean up my linux from dead file links, unused icons, etc. 
I think I know that ```
sudo apt-get clean
``` cleans it, but are there any others? And if there are, what do they specifically do. Thanks in advance. :)

side-note: i know this is random, but this is one of the most friendly communities i've ever been to.

Since Linux does not get as dirty as Windows you only need a few commands to keep it pretty clean.

[http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html)

---

### Post by sayakb on 2008-05-27
> **jrharvey said:**
> hmmmm interesting. I didnt know that linux needed cleanup programs like windows does.

These are not exactly cleanup programs. They just remove unnecessary packages from the apt archive folder or remove those dependencies that were installed but are no longer needed.

---

### Post by adobrakic on 2008-05-27
> **stchman said:**
> Since Linux does not get as dirty as Windows you only need a few commands to keep it pretty clean.

[http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html)

Thanks a lot, this is exactly what i needed. :]

---

### Post by stchman on 2008-05-27
> **adobrakic said:**
> Thanks a lot, this is exactly what i needed. :]

NP.

Just make sure that when you install gtkorphan it will tell you that the gstreamer plugins are orphaned.  Ignore it or you will lose the ability to play mp3 and mpeg2 video.

---

### Post by Arthur Archnix on 2008-05-27
```
sudo apt-get install localepurge
```then
```
sudo localepurge
```Be sure to select all the locales you might want to use when setting it up.

EDIT: Oh, and a lot of programs come with all sorts of languages and such. What this does is clean up all the languages you don't use, and also runs after you install or update some program. So, it'll initially clean up a huge chunk of files, then, it'll strip a little bit out of every program you install later on.

---

### Post by sayakb on 2008-05-27
You might also create a custom filter for orphaned packages in Synaptic:
Goto Settings->Filters
Press New button
Now erase the "New Filter 1" from the text area and type in "Orphaned" 
On the right side, press Deselect All
Now under "Other", **check **Orphaned.
Press OK button.

You can access this filter by Clicking *Custom Filters*(bottom left) and clicking on Orphaned. You might remove all orphaned packages.

---

### Post by adobrakic on 2008-05-27
> **LinuxIsInnovation said:**
> You might also create a custom filter for orphaned packages in Synaptic:
Goto Settings->Filters
Press New button
Now erase the "New Filter 1" from the text area and type in "Orphaned" 
On the right side, press Deselect All
Now under "Other", **check **Orphaned.
Press OK button.

You can access this filter by Clicking *Custom Filters*(bottom left) and clicking on Orphaned. You might remove all orphaned packages.

I did this and gstreamer was one of the items on the list, should i leave this installed?
and do i 'completely remove' or just 'remove'

---

### Post by sayakb on 2008-05-27
Leave it installed, you need them to play your media files..
You might remove everything else other than gstreamer..

EDIT: For anything other than gstreamer, select 'completely remove'. That would also remove the package and any config files..

---

### Post by scorp123 on 2008-05-27
> **adobrakic said:**
> Since i can't find any programs such as System Mechanic, CCLeaner, etc. that I had for windows, are there any terminal codes that clean up my linux from dead file links, unused icons, etc. What I'd suggest you here and there (e.g. once every few months?) go and take a look in the **/var/log** directory if there are any compressed log files (*.gz extension): ```
ls -al /var/log/*.gz
```

Your Linux distro will regularly move old log files into gzip (*.gz) archives ... so if you don't really need those archives anymore I'd say it's safe to get rid of them. After a year or so they can fill up a few 100 megabytes depending on what was going on on your system.

If I do that here I get this: 
```
> ls -al /var/log/*.gz
-rw-r----- 1 root   adm    2106 2008-05-25 21:09 /var/log/acpid.1.gz
-rw-r----- 1 root   adm     366 2008-05-27 01:15 /var/log/apport.log.2.gz
-rw-r----- 1 root   adm     240 2008-05-26 00:45 /var/log/apport.log.3.gz
-rw-r----- 1 root   adm     468 2008-05-25 02:19 /var/log/apport.log.4.gz
-rw-r----- 1 root   adm     453 2008-05-24 02:50 /var/log/apport.log.5.gz
-rw-r----- 1 syslog adm    2455 2008-05-18 11:42 /var/log/auth.log.1.gz
-rw-r----- 1 syslog adm   77029 2008-05-24 20:00 /var/log/daemon.log.1.gz
-rw-r----- 1 syslog adm   59355 2008-05-18 11:40 /var/log/debug.1.gz
-rw-r--r-- 1 root   root  13845 2008-05-25 21:09 /var/log/denyhosts.1.gz
-rw-r----- 1 root   adm   10478 2008-05-26 19:18 /var/log/dmesg.1.gz
-rw-r----- 1 root   adm   10517 2008-05-26 06:44 /var/log/dmesg.2.gz
-rw-r----- 1 root   adm   10450 2008-05-25 21:09 /var/log/dmesg.3.gz
-rw-r----- 1 root   adm   10429 2008-05-24 22:59 /var/log/dmesg.4.gz
-rw-r----- 1 syslog adm  235389 2008-05-23 08:54 /var/log/kern.log.1.gz
-rw-r----- 1 syslog adm  222254 2008-05-23 08:54 /var/log/messages.1.gz
-rw-r----- 1 syslog adm   50497 2008-05-27 19:02 /var/log/syslog.1.gz
-rw-r----- 1 syslog adm   20562 2008-05-26 06:50 /var/log/syslog.2.gz
-rw-r----- 1 syslog adm  159288 2008-05-25 21:14 /var/log/syslog.3.gz
-rw-r----- 1 syslog adm   34966 2008-05-24 20:01 /var/log/syslog.4.gz
-rw-r----- 1 syslog adm    1551 2008-05-18 11:40 /var/log/user.log.1.gz 
```

I cleaned it last month ... So let's see how much space those new files are occupying now: ```
> du -hs /var/log/*.gz
4.0K    /var/log/acpid.1.gz
4.0K    /var/log/apport.log.2.gz
4.0K    /var/log/apport.log.3.gz
4.0K    /var/log/apport.log.4.gz
4.0K    /var/log/apport.log.5.gz
4.0K    /var/log/auth.log.1.gz
80K     /var/log/daemon.log.1.gz
64K     /var/log/debug.1.gz
16K     /var/log/denyhosts.1.gz
12K     /var/log/dmesg.1.gz
12K     /var/log/dmesg.2.gz
12K     /var/log/dmesg.3.gz
12K     /var/log/dmesg.4.gz
236K    /var/log/kern.log.1.gz
224K    /var/log/messages.1.gz
56K     /var/log/syslog.1.gz
24K     /var/log/syslog.2.gz
160K    /var/log/syslog.3.gz
36K     /var/log/syslog.4.gz
4.0K    /var/log/user.log.1.gz
``` ... OK, it isn't much. Nontheless I don't really need those *.gz archives on my home system, so it's safe to get rid of them.

[COLOR="Red"]**_Warning:_** This command deletes all the *.gz archives in **/var/log** with super-user "root" priviledges! Please double-check if you want to execute this or not and *PLEASE* don't mistype it! ```
sudo rm -i /var/log/*.gz
```[/COLOR]

Depending on how many of those packed log files you have in /var/log you might free up a few megabytes. Not really much, I know. But still ... why keep old files around that nobody is going to look at anyway?

---

