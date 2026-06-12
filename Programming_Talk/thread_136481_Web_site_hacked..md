---
title: "Web site hacked."
date: 2006-02-26
forum: Programming Talk
---

### Post by gheorghe_pop on 2006-02-26
Hello.
I was wondering if enyone could help me into the following issue.
I have a hebsite with a mysql database and a php script(news.php) that is reading from the database. The username and password for the mysql database is stored in a separate file(acces.php) and it is outside from the 'www' directory. 
But even so a hacker managed to modify my mysql database. 
I wonder if enyone could tell me what i'm doing wrong. Is it a bug in my scripts or is a server problem, because the webhosting provider said that it would disable my account if ths thing happened again.
Thank you!

---

### Post by spahn on 2006-02-26
Oh man,
That is scary! i have had people try to attack one of my client's sites several times over the last few days.

I am no expert, but i might suggest that you change your user info through your webhost- change the password on the account and change the filename (for the file that contains the database connection info.

Good luck- let me know when you arrive at a good solution.

---

### Post by thumper on 2006-02-26
A common hack in these situations is called SQL injection.  The often occurs when text is submitted through a page and not escaped before executing the SQL.

For example:

'update sometable set somfield=' + posted_data + ' where id=' + other_posted_data

If the posted data is not escaped, then they can hijack your SQL.  Lets say the posted_data is something like

target_value where 1=2; do some malicious updates; other commands; commit;

To get around this you need to do more checks on the posted data, and perhaps escape the input.

---

### Post by LordHunter317 on 2006-02-26
Or, far smarter, don't use the mysql driver, but use mysqli, ADODB, PEAR::DB or any other real DB driver, and parameterized queries.

---

### Post by Kurt` on 2006-02-26
[QUOTE=LordHunter317]Or, far smarter, don't use the mysql driver, but use mysqli, ADODB, PEAR::DB or any other real DB driver, and parameterized queries.[/QUOTE]
Could you elaborate on this a bit more?

I've been doing PHP/MySQL work for about 2 years now, and I've always used the mysql client library that gets built into PHP. (if that's the correct terminology)

I wasn't aware that there were other drivers available for it!

---

### Post by gheorghe_pop on 2006-02-26
Ok!
Thank you for your reply. I think I know where is the problem. I have a download counter for the download of a program. It is exactly what **thumper** said.
For example to count that if a program is downloaded i use this:
[http://minipop.org/admin/clicks.php?url=http://www.minipop.org/progs/electricform/electricform-0.0.3.linux-i686.tar.gz](http://minipop.org/admin/clicks.php?url=http://www.minipop.org/progs/electricform/electricform-0.0.3.linux-i686.tar.gz)
and in the clicks.php i update a database field.
Thank you again very much, I didn't know about sql injection.

---

### Post by LordHunter317 on 2006-02-26
[QUOTE=Kurt`]Could you elaborate on this a bit more?[/quote]Sure.  Mysqli is builtin to PHP5, and supercedes the mysql driver.  **In PHP5, mysql_* shouldn't be used in new applications, *ever***.

The others have been around sine PHP4, and rectify two majors flaws:[list][*]mysql_* doesn't support parameterized queries[*]Database indepedence[/list]

As such, they're generally far more useful.  To be clear, ADODB and PEAR::DB drive the mysql driver internally.  The point is that they provide you with a far safer interface, so they should be used instead.

---

### Post by gheorghe_pop on 2006-02-26
I read a little about sql injection. And I have a more clear way how the stuf is done. In my site the only point where I send data to a mysql querry is in the clicks.php script. and i send allways the same data. I think if i check with the **if** statement what is sent data is sent to the clicks.php script should be enought. Right?

---

### Post by Corvillus on 2006-02-26
Typically you should use a combination of both prepared statements (parameterized queries) and server side validation to avoid SQL injection exploits, among other things. You should also use positive validation (meaning, check for the kind of data you expect and reject it if it doesn't match) as opposed to negative validation (checking for exploits and allowing all other data) whenever possible, as this is more effective in preventing not only SQL injection but also various other types of attacks, as well as increasing the overall integrity of that data you're dealing with.

---

### Post by gheorghe_pop on 2006-02-28
If Ihave a website made like this:
index.php
-------------
<?php
.....
include <top.inc>
include <middle.inc>
include <bottom.inc>
...
?>

and for example i want to load in the middle of the index page let's say pageA.inc and for this I use something like:
[www.blablabla.com\index.php?pageA.inc](www.blablabla.com\index.php?pageA.inc)

Can this metod of loading a page be used by a hacker to write/change files from the server?

---

### Post by LordHunter317 on 2006-02-28
No, but it could be used to read any file Apache has access to.

**Don't do that.**

---

### Post by jerome bettis on 2006-02-28
do you guys know if this exploit is possible with JSP using the com.jdbc.mysql driver?  i use prepared statements if i'm executing the same thing a bunch of times, but for just one select i'll use a regular statement - is this really bad?

[quote=Corvillus]server side validation to avoid SQL injection exploits, among other things. You should also use positive validation (meaning, check for the kind of data you expect and reject it if it doesn't match)[/quote] 
can you explain how you do this?  my server just takes a select statment and gives the results, as far as i know it doesn't validate anything.

---

### Post by Corvillus on 2006-02-28
Well, for example using PEAR, a prepared statement query looks something like this.
[php]
$statement = $db_object->prepare('SELECT something FROM sometable WHERE somefield=? AND someotherfield=?');
$result = $db_object->execute($statement, array($somefield, $someotherfield));
[/php]
In other words, you "prepare" the database for the query by giving it the statement, with all the actual values replaced by ?s (in this case via the prepare() method). Then you execute the query by binding the parameters to the statement (in this case using the execute() method). This has a couple of advantages. The major advantage is that the database will automatically escape all of the parameters as necessary before executing the query, which provides more security against injection attacks. Another advantage is tha it also allows the database to cache the query, so if the same query gets executed multiple times except with nothing changing but the placeholders (as is often the case), the database only has to actually parse it once, lowering overhead. You can read more about PEAR's database abstraction here: [http://pear.php.net/package/DB/](http://pear.php.net/package/DB/)

As for the positive validation, that's basically just the principle of writing code to check every single piece of data that comes from outside of the application against the kind of data you expect before using it for anything, since it's possible for people to put invalid data, html tags, sql code, etc in if you don't.

---

### Post by jerome bettis on 2006-03-01
right i know about prepared statements.  it just seems pointless to use them if it's just a throw-away stmt i'm only going to use once.  in that case it's just more code and a lot messier ... but if it's going to execute a billion times it's faster.  i was asking if the extra security of prepared stmts is worth the BS of using them, as opposed to using a regular stmt.

about the validation  thing, this is not something that i have to do with the  mysql server thing, it's something that the program using mysql has to do?  sounds like a PITA unless you could put it into a nice reuseable lib.  it sounds like more trouble than it's worth for every different app using the database all the time in different ways.  am i way off?

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=jerome bettis]right i know about prepared statements.  it just seems pointless to use them if it's just a throw-away stmt i'm only going to use once.[/quote]I forget if PEAR::DB can use parameterized queries or not for a single statement.  If it can't, then you should always use prepared statements.

If it can, then it doesn't matter for a single statement.  The performance difference should be almost zero, normally.  After that, prepared statements will see massive gains.

In fact, some engines always prepare for you, even if you dont' tell them to.  MS SQL Server 2K5 is that way by default, and you have to disable it at connection time.

>  i was asking if the extra security of prepared stmts is worth the BS of using them, as opposed to using a regular stmt.Preperation doesn't add security.  Parameterized queries do.

> about the validation  thing, this is not something that i have to do with the  mysql server thing, it's something that the program using mysql has to do?Yes, it does.  It depends on your input though.  Some applications need no more validation beyond what they need to ensure their data is correct in the first place.  In many cases, just using parameterized queries is enough to stop attacks.

>   sounds like a PITA unless you could put it into a nice reuseable lib.You can't, it's domain and even application specific.

>  it sounds like more trouble than it's worth for every different app using the database all the time in different ways.  am i way off?Troublesome?  Perhaps, but correctness and security are more important than programmer inconvience.  

Depending on what applications are using the database, they maybe able to share code, or not.  It depends.

---

### Post by jerome bettis on 2006-03-01
[quote=LordHunter317]Troublesome?  Perhaps, but correctness and security are more important than programmer inconvience.[/quote] 
very true, but i'm working with a very very very very .. very large database.  300mb of comma seperated text files lol

so before every update and after every select i should check every single field?  some queries involve about 50 fields, and i'm dealing with probably several million records in 20 some tables.  that's gotta be a huge performace hit, to sit there and look at every small piece of data involved.

but i've already had a few correctness problems and that absolutely can not be tolerated ever.  security, well i'll just hope that doesn't happen to me i guess. :D

basically what i'm asking is, is there a 'nice' way to do this?  i.e. i don't want to (read: will not) sit here and say if ((field1 == valid) and (field2 == valid) ...) etc etc as it would just get rediculous after a few minutes.  this code is already big and convoluted, the last thing i want to do is make it that much worse.  each query is very differerent too, so i'm not sure i could just make a validate() function.

but then again every piece of data in here has to be correct or i might as well not bother at all :neutral:  it just seems to me like this is a problem for the sql server to deal with, just tell me if it's bad and i'll deal with it.  i don't want to check it first.

---

### Post by LordHunter317 on 2006-03-01
> **jerome bettis]very true, but i'm working with a very very very very .. very large database.  300mb of comma seperated text files lol[/quote]Tiny.  Insignificant even.

> so before every update and after every select i should check every single field?That depends on what the data is.   If for example, NULL is invalid in a field, then yes, you should be checking it before you write it to the database to avoid the error the database will throw at you.

But this doesn't have to be done in SQL (nor should it, likely).  It likely should be done at file load time: you shouldn't even be able to instaniate an object / record if the data it represents is invalid.

> that's gotta be a huge performace hit, to sit there and look at every small piece of data involved.Not especially, no.  Not if done correctly.

If this data just has to be loaded, you should your DB engine's bulk loading services to do it.  Of course, if this is MySQL or PostgreSQL, such facilities really don't exist in any useful manner.

> basically what i'm asking is, is there a 'nice' way to do this?I'm not sure what you mean by nice, but nice enough is to prevent object/record instaniation of invalid data.

>  i.e. i don't want to (read: will not) sit here and say if ((field1 == valid) and (field2 == valid) ...) etc etc as it would just get rediculous after a few minutes.Yes, that's ultimately what you have to do.  But what 'valid' means for a field may not require a check.  If a field truly can contain any arbitrary string, then there's nothing to check.

>  each query is very differerent too, so i'm not sure i could just make a validate() function.You don't validate on a by-query basis.  You validate input data.  Your code shouldn't be handling data that is invalid said:**
> it just seems to me like this is a problem for the sql server to deal with, just tell me if it's bad and i'll deal with it.It can, but that carries ramifications you usually don't want to deal with.  Moreover, some checks are largely impractical.  Checks in the database are to ensure your data is correct and consistent in the relational model.  Checks in your applications are to make sure the file you're loading is valid.

Is there some redundancy there?  Yes.  But checking hte errors from the DB is more hassle than it's worth, and your application still has to understand what the error *means* anyway.

---

### Post by gheorghe_pop on 2006-03-05
[QUOTE=gheorghe_pop]If Ihave a website made like this:
index.php
-------------
<?php
.....
include <top.inc>
include <middle.inc>
include <bottom.inc>
...
?>

and for example i want to load in the middle of the index page let's say pageA.inc and for this I use something like:
[www.blablabla.com\index.php?pageA.inc](www.blablabla.com\index.php?pageA.inc)

Can this metod of loading a page be used by a hacker to write/change files from the server?[/QUOTE]


to solve this problem i did something like this:
```
$sd=$_REQUEST['file'];
switch ($sd){
    case "template/about.tpl":
         include($sd);
         break;
    case "template/photos.tpl":
         include($sd);
         break;
    case "progs/electricform/electricform.tpl":
         include($sd);
         break;
    case "template/about.tpl":
         include($sd);
         break;
    case "template/about.tpl":
         include($sd);
         break;
     case "newsread.php":
	 include($sd);
         break;
     default:
	 include("newsread.php");
         break;

}
```

Is it OK?

---

### Post by LordHunter317 on 2006-03-05
That will work, but I still have to question why?

If you're including code dynamically, that's a likely sign of bad code design.

---

### Post by gheorghe_pop on 2006-03-05
I don't have so much experience in PHP.
Can you please tell me wich is the best method to include code dynamycaly?

Tank you!

---

### Post by LordHunter317 on 2006-03-05
My point is you shouldn't be doing that at all.

---

