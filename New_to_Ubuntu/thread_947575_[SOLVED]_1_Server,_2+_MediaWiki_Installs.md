---
title: "[SOLVED] 1 Server, 2+ MediaWiki Installs"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Mr_H on 2008-10-14
I am setting up a new Ubuntu Server and would like to give my users the ability to each have their own Wiki install, if possible.

IE: UserBob has Bobs Wiki (at Mysite.com/~bob/BobsWiki
while UserCharlie has Charlie's Wiki (at mysite.com/~charlie/CharliesWiki). 

Both would be separate from each other and have nothing in common.

I know from the Server guide that setting up one MediaWiki install is not that hard, but how would one go about setting up multiple MediaWiki installations?  Is it possible to do so from the same source code (so if the MediaWiki code is upgraded, I dont have to repeat the task on each installation)?


Thanks in advance for any help/suggestions/etc, it's much appreciated.


SOLVED:  Found this website that gave me an answer: [http://www.steverumberg.com/wiki/index.php?title=WikiHelp_-_Method_Two](http://www.steverumberg.com/wiki/index.php?title=WikiHelp_-_Method_Two)

---

### Post by superprash2003 on 2008-10-14
well you could use the same zip file which you downloaded from mediawiki.. and create a new folder like bobswiki and unzip the zip file to bobswiki and run the install.html or index.html file.. but when you do the setup ensure that you dont overwrite the mysql tables ( if its uses those).. ensure that you create a seperate table..

---

### Post by a7ndrew on 2009-01-30
> would like to give my users the ability to each have their own Wiki install

Save yourself a little effort and copy give each user a copy of tiddlywiki :P

---

