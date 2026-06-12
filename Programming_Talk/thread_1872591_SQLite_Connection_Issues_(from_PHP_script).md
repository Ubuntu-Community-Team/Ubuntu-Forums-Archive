---
title: "SQLite Connection Issues (from PHP script)"
date: 2011-10-30
forum: Programming Talk
---

### Post by kevinharper on 2011-10-30
So I got this problem fixed:
[http://ubuntuforums.org/showthread.php?t=1872368](http://ubuntuforums.org/showthread.php?t=1872368)

Now I can connect to my db (/home/dsl/dbname) from my php scripts.

Here's my db-connect code:
```

      1 <?php
      2 require "sqlite.php";
      3 $db = "/home/dsl/dbname";
      4 sqlite_connect($db) or die("Could not connect to database");

```

This is the error I get:

sqlite_exec: SELECT * FROM sqlite_master;
sqlite_exec result:
sh: line 1: /usr/bin/sqlite: No such file or directory
sh: line 1: /usr/bin/sqlite: No such file or directory
sh: line 1: /usr/bin/sqlite: No such file or directory
Could not connect to database

What I find most disturbing about this error (file not found) is that sqlite is preinstalled on DSL!

---

### Post by Arndt on 2011-10-31
> **kevinharper said:**
> So I got this problem fixed:
[http://ubuntuforums.org/showthread.php?t=1872368](http://ubuntuforums.org/showthread.php?t=1872368)

Now I can connect to my db (/home/dsl/dbname) from my php scripts.

Here's my db-connect code:
```

      1 <?php
      2 require "sqlite.php";
      3 $db = "/home/dsl/dbname";
      4 sqlite_connect($db) or die("Could not connect to database");

```

This is the error I get:

sqlite_exec: SELECT * FROM sqlite_master;
sqlite_exec result:
sh: line 1: /usr/bin/sqlite: No such file or directory
sh: line 1: /usr/bin/sqlite: No such file or directory
sh: line 1: /usr/bin/sqlite: No such file or directory
Could not connect to database

What I find most disturbing about this error (file not found) is that sqlite is preinstalled on DSL!

So does /usr/bin/sqlite exist? Maybe it's called sqlite3?

---

### Post by kevinharper on 2011-10-31
Neither sqlite3 or sqlite<anything> exists in /usr/bin.

But sqlite 3.3.10 is installed. In fact, it comes preinstalled on DSL.

The more I think about this problem, the less I think it is a programming issue and more of a configuration/OS issue.

---

### Post by Arndt on 2011-10-31
> **kevinharper said:**
> Neither sqlite3 or sqlite<anything> exists in /usr/bin.

But sqlite 3.3.10 is installed. In fact, it comes preinstalled on DSL.

The more I think about this problem, the less I think it is a programming issue and more of a configuration/OS issue.

I had the sqlite module for python installed, but not the command line interface, it turned out. Maybe you have to install it separately too?

---

### Post by kevinharper on 2011-10-31
It looks like I'm missing PECL extensions.

I downloaded the tarball from the site but am unable to install it for one reason or another.

running "pear install sqlite" or "pear install sqlite3" tells me that the site is unreachable and that a 200 code was not returned. I pointed pear install to the tarball I DL's and it was unable to find certain files within the tarball.

Here's my issue:
I have an OLD OLD OOOOOOOOLD pc that i want to turn into a web server to run in my LAN. This PC has 64MB or ram and used to run WinMe.

DSL has pumped life back into it! But the OS has outdated software packages so updating something usually requires upgrading a whole bunch of other things. The cool thing is that it comes with a working web server and a db.

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=16;t=3036;st=5](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=16;t=3036;st=5)
The guy behind SDL says:
> 
I have re-posted php.tar.gz in the repository. It includes my simple sqlite interface library. 

The following is an ultra simple example:
From /home/dsl create a database and table
$ sqlite db
> create table addressbook(name,address,csz,phone);
> insert into addressbook values("Robert","123 Third","90210","123-555-1234");
> select * from addressbook;
> .exit

Next install php.tar.gz via the mydsl system.
Then start Monkey

Then in /opt/monkey/htdocs make a simple test.php
<?
require "sqlite.php"
$db = "/home/dsl/db";
sqlite_connect($db) or die("Count not connect to database");
$query = "select * from addressbook";
$myResult = sqlite_query($query,$db) or die("Query Failed");
$myRow = sqlite_fetch_array($myResult);
$name = $myRow["name"];
?>
<HTML>
<title>Test Sqlite Interface</title>
<body>
<? print $name; ?>
</body>
</html>

Have Fun. If you improve my library, please let me know.


So according to him, I should have been set after I installed the php package from the MyDSL repository/browser.

:( Should I reinstall and simply try again? I would go w/ puppy linux but it requires a min of 100MB of RAM.

---

### Post by kevinharper on 2011-10-31
Thanks Arndt...

I got it! :)

I thew the liveCD in there and started to look through config files because I JUST KNEW this should have all worked "out of the box"!

I looked in web server's conf files for where it references the "/usr/bin/" path... nothing. I looked for it in php's config files.. nothing. I was hoping to find it so I could comment it out, see what happened. Or maybe point it somewhere else. Then I decided to go look in sqlite's config files. I did "which sqlite" and it gave me a directory that was a couple of dirs deeper inside /usr/bin/. I simply copied the file into /usr/bin. BAHM!

I KNOW I'M ABOUT TO GET HELL FOR THAT HACK, but it works! And it is MORE THAN PERFECT for what I need! :D

Again, thanks for your time.

---

