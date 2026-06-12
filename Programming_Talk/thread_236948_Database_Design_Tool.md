---
title: "Database Design Tool"
date: 2006-08-15
forum: Programming Talk
---

### Post by huggy77 on 2006-08-15
just wondering what tools you use to layout your databases...i build small programs in coldfusion and i am looking to make the switch from access to MySql...

my home office is made up of XP and Linux machines,  my contracting site is MAC and Linux.

I either need a program that will run on MAC and XP or on Linux...  

Tried out DBSKETCH so far, not bad... just looking for something that is used throughout the community...

thanks!

i am running dapper on my tux boxes, xp on windows and MAC OS 10 on my apple machines

---

### Post by kaffelars on 2006-08-15
I've used [DBDesigner 4]("http://fabforce.net/dbdesigner4/") and think it's very good. It's not open source though, but it's free (as in free beer) and runs on Linux and Windows.

---

### Post by trippyd on 2006-08-15
> **kaffelars said:**
> I've used [DBDesigner 4]("http://fabforce.net/dbdesigner4/") and think it's very good. It's not open source though, but it's free (as in free beer) and runs on Linux and Windows.

from the dbdesigner page:

The current build of DBDesigner 4 can be downloaded via the download page. DBDesigner 4 is an Open Source project and is published under GNU GPL.

Just sayin :)

---

### Post by gmclachl on 2006-08-15
I like Druid, it's Java based, so it's cross platform[sic] 

 I use it at home x86_64 Linux and at work OSX and it's nice to have a standard interface across machines. 

 [http://druid.sourceforge.net/](http://druid.sourceforge.net/)

 George

---

### Post by LordHunter317 on 2006-08-15
Pencil, Paper, emacs, and the SQL monitor.

If I have to get visual in a presentable form, I use Visio.  Every once in a while in SQL Server, I've used their diagramming tools, but they're not really very good.

---

### Post by kaffelars on 2006-08-16
trippyd: Thanks :)
Couldn't remember it when I wrote it, and didn't see the words "source code" on the download page...too early in the morning I guess ;)

---

### Post by huggy77 on 2006-08-16
THANKS FOR ALL THE POSTS! i love these forums - very helpful community...

i have dbdesigner - very nice...  Cant get it to connect yet to mysql on ubuntu but i am a super noob when in comes to mysql...  Do you guys have any recommended reading (on the net or books) on relational databases...   i know very basic relation theory from college (years ago) - trying to write better web aps, i need to up my db game!

---

### Post by bruno.braga on 2010-05-09
Just to leave an update on this thread, as it is top ranked in Google Search, and there are not many other discussions about this elsewhere. I tried hard to install DBDesigner 4 on Ubuntu 10.04 (Lucid Lynx) without success (got stuck on some of the libs, in my case [libXft.so.1]).

Then I paid more attention to the page where the DBDesigner resides: [http://www.fabforce.net/downloads.php]("http://www.fabforce.net/downloads.php"), and read that DBDesigner is outdated, and we should use MySQL WorkBench instead.

I am running on 64-bit version, so when I tried to install the latest stable release 5.1.18a-1ubu904, I ran into dependency problems: libmysqlclient15off, which is NOT available in repository.

I got it from Karmic repository (installed manually, actually, even though this is not recommended), and then the installation went smooth.

For reference, the links and the installation procedure:

```

# MySQL WorkBench has a dependency with [libmysqlclient15off], which is not
# available in Lucid, but you can get it from Karmic.

# Install the dependency first (from karmic)
# source: http://packages.ubuntu.com/karmic/amd64/libmysqlclient15off/download
wget http://mirrors.kernel.org/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb
sudo dpkg -i libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb

# Install the MySQL WorkBench (latest as of this moment)
# version info: http://wb.mysql.com/
wget http://dev.mysql.com/get/Downloads/MySQLGUITools/mysql-workbench-oss-5.1.18a-1ubu904-amd64.deb/from/http://ftp.jaist.ac.jp/pub/mysql/
sudo dpkg -i mysql-workbench-oss-5.1.18a-1ubu904-amd64.deb

```

---

