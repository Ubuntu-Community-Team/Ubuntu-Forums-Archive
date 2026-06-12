---
title: "A master list of config files, please"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by avalenc on 2008-10-24
So, lately, I've been cut/pasting commands to get to different config files to be able to change options in some of them.

I don't know the differences between the different kinds of config files, and I don't know what the range of files is, nor do I know where these different files are located. I've looked around on the fora, but don't see any list of them.

Is there such a thing? 

If not, could one be made here? I would really like to see:
file name
how to access it/location
what it controls
what, if anything, is absolutely dangerous to change/touch
whether or not that file is universal (across distros) or not

Thanks!

---

### Post by cairnzi on 2008-10-24
not sure if this is what your after but have a look anyway.....

[http://ubuntuforums.org/showthread.php?t=951498](http://ubuntuforums.org/showthread.php?t=951498)

---

### Post by cairnzi on 2008-10-24
apologies mate, just re-read your post,my bad LOL,ignore the link,unless you want some good basic coomand lines. again sorry, :popcorn:

---

### Post by namegame on 2008-10-24
As far as I know, there is no "master list" nor can one be made.

Each Linux distribution handles config files slightly different.

Granted, some will be common to all, but even different applications have their own config files.

Such a list would be unfeasible to create. 

However, if you want a true understanding of config files I recommend installing Arch on a separate partition or a virtual machine.

---

### Post by avalenc on 2008-10-25
Hnm, so then how do I locate a particular config file? Is there a way to derive what it's called or where it would be? (Specifically, what I'm trying/need to do is to change the users config through CLI.)

Thanks.

---

### Post by jacksaff on 2008-10-25
Most system configuration files are in /etc. The etc file may (or may not) stand for Editable Text Configuration files and is a Unix standard from many years ago.
Most application configuration files are in the hidden folders in your home directory (hidden files start with a . and are not shown by default).
Kde and gnome keep their config in obscure places that I always forget when I need them and have to google for...
To add users from the cli use the adduser program. man adduser in a terminal will give you more details.

---

### Post by hyper_ch on 2008-10-25
user-based config files are in /home/USER and mostly in a hidden directory.

system-wide config files are in /etc

---

### Post by sethvath on 2008-10-25
From the gentoo wiki: cache from google, the main wiki is down atm

[http://209.85.175.104/search?q=cache:lR1QXmgNGQsJ:gentoo-wiki.com/TIP_List_of_Configuration_Files+all+linux+config+files&hl=en&ct=clnk&cd=8](http://209.85.175.104/search?q=cache:lR1QXmgNGQsJ:gentoo-wiki.com/TIP_List_of_Configuration_Files+all+linux+config+files&hl=en&ct=clnk&cd=8)

More here
[http://news.softpedia.com/news/Linux-configuration-files-and-what-they-do-34292.shtml](http://news.softpedia.com/news/Linux-configuration-files-and-what-they-do-34292.shtml)

[http://www.ibm.com/developerworks/linux/library/l-config.html](http://www.ibm.com/developerworks/linux/library/l-config.html)

Is the arch/gentoo linux's rc.conf what you were asking for?

---

