---
title: "Personal Web Servers"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by ratatak on 2008-10-26
Hi there. First of all I am new to the Linux community and to Ubuntu so I may not have the appropriate jargon down yet. I am downloading Ubuntu right now and plan to do a clean install (wipe WinXP out of existance) today. One of the things that really erks me about WinXP Home Edition is that it has no support for personal web servers. I am hoping that you guys can confirm that Ubuntu supports this feature. I know there are ways to get a PWS up on WinXP using Apache and configuring alot of files but I didn't enjoy the process and I still have a few problems keeping people away from some data. Thanks!

Edit: Also I was wondering where to go to check and see if my hardware will be supported. The last thing I want is to format harddrive, clean install, then find out I cannot use the internet :( Thank again.

---

### Post by billgoldberg on 2008-10-26
> **ratatak said:**
> Hi there. First of all I am new to the Linux community and to Ubuntu so I may not have the appropriate jargon down yet. I am downloading Ubuntu right now and plan to do a clean install (wipe WinXP out of existance) today. One of the things that really erks me about WinXP Home Edition is that it has no support for personal web servers. I am hoping that you guys can confirm that Ubuntu supports this feature. I know there are ways to get a PWS up on WinXP using Apache and configuring alot of files but I didn't enjoy the process and I still have a few problems keeping people away from some data. Thanks!

Edit: Also I was wondering where to go to check and see if my hardware will be supported. The last thing I want is to format harddrive, clean install, then find out I cannot use the internet :( Thank again.

I don't know what you mean with a PWS.

But if people think server they think Linux, so you should be good.

On your second question, that is what the live cd is for.

---

### Post by BDNiner on 2008-10-26
I would run the live CD and try out ubuntu before you install it. It boots to a working session of ubuntu running from your RAM so no changes are made to the hard disk until you decide to install it or mount you hard disk and start messing around. 

Configuring apache is going to be the same on windows as it is on ubuntu. so i don't understand your reason for trying out ubuntu.

---

### Post by ratatak on 2008-10-26
> **BDNiner said:**
> I would run the live CD and try out ubuntu before you install it. It boots to a working session of ubuntu running from your RAM so no changes are made to the hard disk until you decide to install it or mount you hard disk and start messing around. 

Configuring apache is going to be the same on windows as it is on ubuntu. so i don't understand your reason for trying out ubuntu.


Awesome. I knew about Live CD but I wasn't sure if it was a seperate download. Configuring Apache shouldn't be the same. I guess I was looking for more of an answer like "With Ubuntu you do not need 3rd party software to set up a PWS (PWS means personal web server for the first reply). I want to switch because there is no support for this with my current OS. I chose Ubuntu because I have messed around with an earlier version before and it seemed nice.

---

### Post by BDNiner on 2008-10-26
Oh ok, Apache will always be third party software but it is included or it is easy to install with almost all linux distros. Good luck setting up your server, you will be able to find plenty of help on these forums.

---

### Post by Iowan on 2008-10-26
There are a couple of web server packages "smaller" than Apache... I'll need to look around for their names, though.

lighttpd is one that I came across.

---

### Post by Xiong Chiamiov on 2008-10-26
> **Iowan said:**
> There are a couple of web server packages "smaller" than Apache... I'll need to look around for their names, though.

lighttpd is one that I came across.
I'm fond of lighttpd (pron. "lighty") myself, but it's *extremely* easy to find information about the standard LAMP stack (Linux, Apache, MySQL, PHP).

Apache is certainly not officially supported, but... do you really need official support?  I mean, if you do, you can always buy support from Canonical, I suppose.

Setting up a LAMP stack is much, much easier on Linux than Windows.  [Here]("https://help.ubuntu.com/community/ApacheMySQLPHP")'s one guide.

---

### Post by bodhi.zazen on 2008-10-26
Two links for you :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

    [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

+1 lighttpd (lighty) but in my experience there is less support than apache and there is not a ton of guides written in "english"

[http://www.debianhelp.co.uk/lighttpd.htm](http://www.debianhelp.co.uk/lighttpd.htm)

[http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html](http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html)

---

### Post by ratatak on 2008-10-26
thanks everyone for all the info. I am happily on Ubuntu right now fooling around with everything. I will check out all those links later tonight. I guess the next step is to join the programming community :P

---

