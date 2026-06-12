---
title: "What is bad about Automatix"
date: 2007-09-16
forum: Recurring Discussions
---

### Post by ajmannen on 2007-09-16
Hi, I have just used Automatix to install..stuff. but then after a quick google i saw alot of people Hate automatix..Why, have a harmed my system by using it?

---

### Post by Hospadar on 2007-09-16
Well in general it's not going to destroy your system, but it changes some files and configurations (like for example your repository list) and sometimes it does things the wrong way (not often but it can happen) and if it does happen to screw stuff up it can be really hard to fix.

So it's not necesarily going to destroy your system or anything, but it has the potential to screw stuff up in wierd ways and could be difficult to fix or roll back.

---

### Post by ajmannen on 2007-09-16
Well, it seems as ubuntu has begun to run slower, is it anny way to check my system for errors

---

### Post by Kilz on 2007-09-16
[According to the Ubuntu Technical Board]("http://mjg59.livejournal.com/77440.html") it could quite possibly break your system. I have helped lots of users in the past that have had broken systems because of Automatix. If you want to use it, at least be aware of the possible problems and that if it does happen you may have to reinstall.

---

### Post by ajmannen on 2007-09-16
I [SIZE="4"]have[/SIZE] used it, and now my system is slower, but i spent alot of time on it and don't want to re-install Ubuntu :(

---

### Post by oilchangeguy on 2007-09-16
> **ajmannen said:**
> Hi, I have just used Automatix to install..stuff. but then after a quick google i saw alot of people Hate automatix..Why, have a harmed my system by using it?

read this:
[http://www.osweekly.com/index.php?option=com_content&task=view&id=2644&Itemid=449](http://www.osweekly.com/index.php?option=com_content&task=view&id=2644&Itemid=449)

most of the people who post negative comments about automatix, have never used it. they're just stupid people repeating what they've read. and of couse as more and more stupid people repeat any thing negative, the bigger it becomes. in reality, the little damage the automatix may have caused is done during an upgrade from one ubuntu version, to another. and the best way to get the newest version is not by upgrading, but doing a fresh install. i've got automatix on two of my computers. and never had a problem. and i'm sure i'm not in the minority here. so to all of the stupid people out there who've NEVER used automatix. shut up!! and stop repeating what you've read.

---

### Post by Sef on 2007-09-16
From [Live Journal]("http://mjg59.livejournal.com/77440.html"):

> Automatix is, in itself, a poor quality package which fails to
conform to Debian or Ubuntu policy.

# Passes --assume-yes to apt-get, which will (as a result) happily
remove packages without giving the user an opportunity to
intervene. This is especially bad when removing Automatix modules -
any package that depends on one of the packages being removed will
also be uninstalled, even if the package was originally installed via
something other than Automatix!

# Has no internal dependency management. Unable to keep track of why
packages were installed, so prevents the removal of the multimedia
module because that would remove sections of other modules without
explicitly removing that module. Installing swiftfoxplugins will pull
in several plugin packages, but removing swiftfoxplugins will not
remove them even if nothing else depends on them. Also means that
package installation and uninstallation have to be manually kept in
sync - uninstall will not always remove all packages that were
installed.

# Has no concept of file tracking, so will just remove entire
directories. Makes no attempt to ensure that a user-installed version
is not already installed in the same location, so effectively assumes
that the /opt namespace belongs to it.
# Will remove Ubuntu repository packages in favour of tarballs with
no warning.

---

### Post by oilchangeguy on 2007-09-16
> **ajmannen said:**
> I [SIZE="4"]have[/SIZE] used it, and now my system is slower, but i spent alot of time on it and don't want to re-install Ubuntu :(

this is probably because you've installed many things. and these are loading at startup. this is why people blame windows for being slow. it's not the os. but all of the software designed to load at startup.

---

### Post by Kilz on 2007-09-16
> **oilchangeguy said:**
> read this:
[http://www.osweekly.com/index.php?option=com_content&task=view&id=2644&Itemid=449](http://www.osweekly.com/index.php?option=com_content&task=view&id=2644&Itemid=449)

most of the people who post negative comments about automatix, have never used it. they're just stupid people repeating what they've read. and of couse as more and more stupid people repeat any thing negative, the bigger it becomes. in reality, the little damage the automatix may have caused is done during an upgrade from one ubuntu version, to another. and the best way to get the newest version is not by upgrading, but doing a fresh install. i've got automatix on two of my computers. and never had a problem. and i'm sure i'm not in the minority here. so to all of the stupid people out there who've NEVER used automatix. shut up!! and stop repeating what you've read.


The link I posted was part of a report from the Ubuntu Technical Board, not just someone who doesnt know what they are talking about. This isnt just nay sayers but cold hard facts from someone who's job it is to look at the problems from the Technical point of view of developers.
While you may never have had problems, you must at least understand that it is possible that others have. That when it does happen, most of the time its new users without a firm grasp of troubleshooting. All because someone told them it was the way to go.

---

### Post by por100pre1 on 2007-09-16
The first time I installed Ubuntu I used Automatix. My system was slow and had issues with Azureus, Java, QuickTime format and other media formats. When I uninstalled Automatix it ended up messing my sources.list and I had to fix it manually. I reinstalled my system (because I wanted to give more hdd space) and I tried this [how-to]("http://ubuntuforums.org/showthread.php?t=413624") for Feisty. Now everything works fine, like a charm! :)

---

### Post by matthew on 2007-09-16
Please don't take this wrong, but this is a very old question that generally leads to controversy whenever it is brought up. Please feel free to use the forums search tool to find old discussions and read the myriad of opinions there. The comments above were also adequate for a basic answer to the question, so I'm going to close this thread before it degrades.

Thank you to the users who contributed good, unemotional answers. Your actions have, in no way, contributed to my decision to close this thread.

---

