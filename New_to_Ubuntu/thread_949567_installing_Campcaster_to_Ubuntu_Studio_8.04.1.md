---
title: "installing Campcaster to Ubuntu Studio 8.04.1"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by boob577 on 2008-10-16
Hello to all

I am very new to Linux. I am trying to install Campcaster to Ubuntu Studio.
I have managed to get the three packages listed in the repository. 
They are:
Cmapcaster-Libs, Campcaster-Station, Campcaster-Studio. 
Campcaster-Libs installed correctly but the other two did not.
When I "Mark For Installation" and then choose "Mark". 

These are the errors:
campcaster-station:
 Depends: libboost-date-time1.33.1  but it is not installable
 Depends: libicu34  but it is not installable
 Depends: libicu34  but it is not installable or
 	libicu36  but it is not installable

campcaster-studio:
 Depends: libboost-date-time1.33.1  but it is not installable
 Depends: libicu34  but it is not installable
 Depends: campcaster-station but it is not going to be installed
 Depends: libicu34  but it is not installable or
 	libicu36  but it is not installable

Under "Software Sources" all are check except "Source Code"
Under "Third Party Software" I have added "http://code.campware.org.ubuntu dapper main.

This is a fresh install, with all the updates done.

I am at a loss figuring out what I must do next or where I have gone wrong.

Please make any reply as simple as you can.
I am an Windows XP senior, who is trying to set this up for a friend.
Thanks in advance. 
Bob

---

### Post by LowSky on 2008-10-16
par tof the issue is the  repo you added, its for Ubuntu Dapper, which is no longer supported and many of the files Cmapcaster needshave been replaced with newer version that campcaster might not be able to use try using the Fiesty or debian etch repos
[http://www.campware.org/en/camp/campcaster_news/722/](http://www.campware.org/en/camp/campcaster_news/722/)

---

### Post by boob577 on 2008-10-16
Thanks for the suggestion LowSky but I still get the same errors.

Bob

---

### Post by Randem on 2009-08-18
Has anyone had any success installing Campcaster on Ubuntu other that Dapper?

I am having similar troubles with Jaunty where Campcaster is reporting cppunit errors.  See **[this post]("http://ubuntuforums.org/showthread.php?t=1243266")** for details.

---

### Post by metatecque on 2009-11-12
Yes, I have campcaster successfully running on 8.04.latest ...

Using the development environment instructions found here...

[http://trac.campware.org/campcaster/wiki/DevelopmentEnvironment](http://trac.campware.org/campcaster/wiki/DevelopmentEnvironment)

This is the latest stable development version...

And I can say it is very stable on that distro..

If you have questions #campcaster on freenode is a good place for answers

---

