---
title: "Open source web application development."
date: 2011-04-30
forum: Programming Talk
---

### Post by ProgramErgoSum on 2011-04-30
Hi,
I would like to know, if you are a open source developer, then what would be your choice of framework to develop and deploy web applications following a work-flow ?

The answer would most likely be : it depends. :) I had been searching around quite a bit and the choices are either too many or do not seem to be 'complete'. For example, [Apache Turbine]("http://turbine.apache.org/index.html") refers to some projects which are retired, closed, etc.

I am looking at applications that cater to say banking. An application to open new accounts, debit/credit, etc.

---

### Post by WitchCraft on 2011-05-01
It depends ;-))

First, I'm not an OpenSource developer, and second, I work in a Windows-only company (although being a Linux-user myself).

So my choice is pretty obvious: Use C#/VB.NET/mono10.10/XSP4/nginx so I can reuse at home the code I write/steal from daily work.

You basically have the following choices:
1. Perl via CGI/FastCGI
2. Python + Django
3. PHP + MySQL
4. mono + XSP
5. Ruby on Rails
6. Cold Fusion
7. Java
8. Anything I don't know of or have deemed too unimportant to mention
Important things first: I don't know anything about Ruby.

Perl via CGI/FastCGI is a phase-out model, first because it uses CGI, second because Perl code is pretty unmaintainable, and third because the entire concept is quite insecure.

Python + Django if you aspire working at Google (my choice when I develop Linux only).

PHP + MySQL if you want to profit from tons of already working code.
I personally would say that PHP is more mature than ASP.NET when it comes to web development. 
On the other hand, security issues are rampant, which is a problem because Windows-using corporations won't use it because there is no system-wide update for security issues (and a lots of other issues, thank to MS for that...).
But I personally don't like MySQL, never have, because of the licensing (MySQL = Oracle now), and because it doesn't check referential constraints or datatype validity (argh, of course, that way you're faster, but...)...

The ColdFusion server-license is expensive, so it's definitely nothing for OpenSource development.
Maybe there are free ColdFusion engines for Linux, but don't ask me about the quality.

Java: Lots of codes + libraries, and cross-platform, but an archaic pain in the *** when compared to C#. 
Plus licensing - beware, it's Oracle now, they WILL TRY to make LOTS of money from it - no matter what.

Last but not least: mono + XSP
You can develop OpenSource with it if you want to.
But the definitive advantage over Perl/PHP is that you can compile your code (free of charge, !unlike PHP Zend!), which allows you to go ClosedSource with your WebApplications at any time (plus it's a lot faster and less memory-consuming than Java), if you later wanna go that way, plus it also works in the Windows world (if the code is properly written). Also with a decent obfuscator, reverse-engineering is pretty impossible (an advantage is also that it's dead-easy to reverse-engineer when unobfuscated, a definitive advantage against inexperienced competition).

Plus .NET has some of the most flexible databindings, supporting most database types with ADO.NET (on Linux too), which means no ODBC necessary, in general, but ODBC is available if you have the need to.

The only realy disadvantage with mono (besides development taking longer than in PHP) is that licensing is kind of a sword of Damocles.
Not much to fear from Novell, but basically MS can come in with a patent infringement suit at any time (against you or Novell, or a Linux distro deploying mono - for example they have patented the VB.NET 'IsNot' !operator!). 
But unlike with Java under Oracle, this hasn't happened yet. 
Probably Linux is too unrewarding for Microsoft's lawyers time - they have more profitable things to do - such as suing salesforce over "Method and concept to staple menus over each other".

---

### Post by ProgramErgoSum on 2011-05-01
Quite a thorough answer. Thanks !

I had the following thoughts:

With the (technical) problems of MySQL listed by you, what database would then be a good choice ? I have never used MySQL; I have always been a IBM DB2 person.

I was hoping to hear some along the lines of J2EE as I do have some (limited although) experience with J2EE. My 'choice' was to consider JBoss as the server and then use technologies around it. But, then you mention the issues with Java.

I had to laugh at this !

> Python + Django if you aspire working at Google 

Work for Google...sure! Perhaps as the tea boy. :LOL:

---

### Post by SeijiSensei on 2011-05-01
> **WitchCraft said:**
> PHP + MySQL if you want to profit from tons of already working code.  I personally would say that PHP is more mature than ASP.NET when it comes to web development. 
On the other hand, security issues are rampant, which is a problem because Windows-using corporations won't use it because there is no system-wide update for security issues (and a lots of other issues, thank to MS for that...).

PHP itself is pretty darn secure.  The applications people write can be insecure, but that's true of most any web application that doesn't have effective controls over input.  Many of the most widely used web-facing applications, like this forum for instance, are written in PHP.  Overall I'd claim PHP's security has been much more tested in real-life situations on the Internet than anything written in ASP or maybe even .NET.

I don't have any contact with these "Windows-using corporations," but I suspect the reason for their disinterest in PHP has much less to do with security FUD than with PHP not being a Microsoft technology.  Linux distro maintainers routinely push through PHP updates, usually within a day or two of their release.  If there are problems disseminating updates for PHP on the Windows platform, that may have as much to do with the platform as the updates.

> **ProgramErgoSum said:**
> With the (technical) problems of MySQL listed by you, what database would then be a good choice ? I have never used MySQL; I have always been a IBM DB2 person.

I've used [PostgreSQL]("http://www.postgresql.org/") as a backend to PHP development for over a decade.  When I first began, MySQL was not redistributable for commercial use as it is now, but Postgres has always been [licensed]("http://www.postgresql.org/about/licence") on terms similar to BSD and MIT.  I think you'll find PG to meet most, if not all, your needs for a professional SQL database.

Here's a useful comparison grid for various RDBMS: 
[http://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems](http://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems)

---

### Post by ProgramErgoSum on 2011-05-01
> **SeijiSensei said:**
> PHP itself is pretty darn secure.
I am sure you are saying this out of your experience. However, would you like to mention any particular features that makes php inherently secure ?

I am now surprised that both SeijiSensei and WitchCraft aren't saying much about J2EE. Because it is Oracle now and not SUN any more ? Or something else ?

My goal is to be able to develop and deploy small business applications such as, running a cyber-cafe, etc. without compromising on performance, quality, etc. And, therefore, I would like to pick up a 'development path' that I can rely on for a long time than having to switch technologies regularly. Of course, one size does not fit all. But, at least, to start with, I would want to concentrate on one thing at a time.

---

### Post by Reiger on 2011-05-01
- MySQL does the whole database hog when you set the backend for your tables to InnoDB. But you can of course go with Postgres. Anyway, a database is something that is quite detached from programming language (modulo bindings). You can do PHP with Oracle DB just as you can do Java with MySQL.

C#/Java both work, both have various elaborate object <-> database mappings and the patent scare is pathetic on both counts. If you make any kind of GUI at all there is no way you are not infringing some obscure patent, in fact if you are doing any programming at all there probably is a patent covering what you are doing already.

---

### Post by LoneWolfJack on 2011-05-01
> With the (technical) problems of MySQL listed by you, what database would then be a good choice ?

There are no technical problems with mySQL. The developers just decided to do things in a certain way.

I've used mySQL, Postgre, Oracle and a few others, but I clearly prefer mySQL. Postgre is OK, and by now it has mostly caught up with mySQL in terms of speed, but this might change again with Oracle's updated InnoDB engine.

I'd call Postgre a bit more professional for various reasons, but you'll quickly find that the Postgre community is also much more hostile towards newbies. You're expected to know what you're doing.

---

### Post by directhex on 2011-05-01
> **WitchCraft said:**
> Not much to fear from Novell, but basically MS can come in with a patent infringement suit at any time (against you or Novell, or a Linux distro deploying mono - for example they have patented the VB.NET 'IsNot' !operator!). 
But unlike with Java under Oracle, this hasn't happened yet. 
Probably Linux is too unrewarding for Microsoft's lawyers time - they have more profitable things to do - such as suing salesforce over "Method and concept to staple menus over each other".

ASP.NET MVC is Free Software, including a patent grant from Microsoft.

---

### Post by ve4cib on 2011-05-01
Your standard LAMP server is pretty common for web applications: Linux, Apache, MySQL, PHP/Perl/Python.  It's standard technologies that are widely-supported and flexible enough that you can do (almost) anything with them.

I've done some web application development with C#/ASP.NET, and it generally seems to work.  Never tried it with Mono, but I assume it's mature enough that that would work too.  And don't worry about all the patent-related FUD around Mono; it's not an issue, despite how loudly people like to beat their chests about it.

Personally I'd lean towards PHP, MySQL, and Apache, with the odd Python CGI script when necessary.  No particular reason other than that's what I'm used to.


One thing I will mention that hasn't come up yet: client-side aspects of your web applications.  Obviously the standard is HTML+Javascript, but if you really wanted to you could use Flash (or Flex), Silverlight (ew), or whatever else.

I'm going to be amazingly orginal and advise using HTML and Javascript.  Specifically, I'm going to suggest you take a look at [ExtJS](http://dev.sencha.com/deploy/ext-4.0.0/docs/).  It's a Javascript framework that contains everything you ever really need for a web application: floating panels, nice-looking buttons, tree views, file browsers, dynamic stores that can be used to pull data from a DB and manipulate it on the client, etc...

ExtJS is basically designed as an object-oriented library for JS, with extensible "classes" for all the various widgets and whatnot.  It's also designed to work across browsers, so it will look and act the same in IE, FF, Safari, Chrome, Opera, etc...  It's also [free to download](http://www.sencha.com/products/extjs/download/) (GPLv3), or you can pay for a license that allows closed-source development.

---

### Post by slavik on 2011-05-01
Perl + CGI is not the only way to write web apps in Perl.

---

### Post by myrtle1908 on 2011-05-01
> **ve4cib said:**
> I'm going to be amazingly orginal and advise using HTML and Javascript.  Specifically, I'm going to suggest you take a look at [ExtJS](http://dev.sencha.com/deploy/ext-4.0.0/docs/).  It's a Javascript framework that contains everything you ever really need for a web application: floating panels, nice-looking buttons, tree views, file browsers, dynamic stores that can be used to pull data from a DB and manipulate it on the client, etc...

ExtJS is basically designed as an object-oriented library for JS, with extensible "classes" for all the various widgets and whatnot.  It's also designed to work across browsers, so it will look and act the same in IE, FF, Safari, Chrome, Opera, etc...  It's also [free to download](http://www.sencha.com/products/extjs/download/) (GPLv3), or you can pay for a license that allows closed-source development.

+1 for ExtJS on the client side.  Fantastic product.  Been using it since v1.  Great for corporate world and widget heavy web based applications.

For me it's JEE (on Tomcat or any other JEE servlet container) together with a custom (in-house) data access layer and ExtJS on the client (with countless custom in-house widgets).  Servlet container simply sends and receives JSON incl. ExtJS screen definitions, grid data specs etc.  It's a cakewalk.

---

### Post by ve4cib on 2011-05-02
I've used ExtJS with C#/.NET on the server.  JSON plays amazingly well with that.  We had a library that seamlessly turned C# objects into JSON objects to send to the client and vice-versa.  Worked like a charm.

I've also used ExtJS for some strictly client-side "applications" that used Google Maps and similar public JS services.  It's probably overkill for that sort of use, but it's very easy to set up.

---

### Post by ProgramErgoSum on 2011-05-02
Many thanks, everybody, for all your response. I am going to do some more exploration and reading before I ask more questions.

---

### Post by WitchCraft on 2011-05-06
> **ProgramErgoSum said:**
> Many thanks, everybody, for all your response. I am going to do some more exploration and reading before I ask more questions.

Sorry, I'm responding a bit late:

On the database side, you have the following choices:
- Oracle
- Sybase
- MySQL
- PostGre SQL
- FireBird
- SQlite

My personal favourite is FireBird.
The reasons are as follows (and in this priority):
1. You can delete the table/view/procedure SQL create code, leaving only FB bytecode, which is much harder to reconstruct (though possible given enough effort).
2. It works perfectly in an embedded environment on Windows, Linux and Mac. You can plug in an embedded database into a fully-fledged Firebird server at any time, and you do not need to make any changes at all before doing so. It has native drivers (unlike the jet mess with MS-Access), and it works fine with many users.
3. It is fast. It's faster than PostGre in most things. It's slower than MySQL in many things, but that's because Firebird checks constraints, datatype validity (date/time for example). 
4. As an embedded database, it has much more functionality than SQlite.
5.  It's using the InterBase Public License, which is far more liberal than for example the MySQL license.
6. Paging is dead-easy: SELECT FIRST <n> SKIP <m> * FROM <tablename>


Sybase:
Took me two entire days to get it working on Laptop1, and I never got it working on Laptop2. Then, I couldn't use the old Sybase drivers to connect to the database using mono. Some new .NET drivers are available from Sybase via support contract, but for that you have to pay a lot. In other words: it's crap. 

Oracle:
Needs to much RAM for my old development computer, so it's a no-go. Otherwise it would be fine.


MySQL: Already said I don't like it and for what reasons.

PostGre SQL: Cool solution, BSD license is excellent, used to be a bit slow (has changed), and now has Geospatial support. Would be my choice if only they had developed a lightweight embeddable standalone component, too.


SQlite:
Superfast, embeddable solution. Unfortunately, that speed is gained by omitting features, just like in MySQL. Doesn't really work with multiple-concurrent write-access. If you want to plug the database in a real server (for multiple-concurrent write access), you need to redesign the database for another database system (=complete rewrite). Last issue makes it definitely a no-go.




On Java:
It's basically the predecessor of .NET.
As such, .NET is a SUPERSET of Java. 
Which means you can easily port Java code to .NET, but .NET will be pretty unportable to Java...
Interoperability from Java to native code is far more difficult, though possible.

Java is more solid when you look at it's future:
Java is now developed by Oracle (which seems to be doing fine), while Novell (which owned SuSe, which owned Ximian, which developed mono) has been bought by Attachmate corporation, which have in turn laid-off US-based Linux/mono-coders just recently, because they reorganize the entire company with the headquaters and operations of SuSe being now again in Nürnberg, Germany.

Also, Java is more mature than mono, because it was developed cross-platform, while Microsoft developed .NET with Windows in mind, leaving all portability issues to the mono-team.

Also, Java developers have a slight tendency to be better paid than .NET developers.

---

### Post by slavik on 2011-05-06
6. Paging is dead-easy: SELECT FIRST <n> SKIP <m> * FROM <tablename>

try:

select * from table
limit 1, 10

1 = first row
10 = number of items

yes, paging is difficult.

Java: Lots of developed application servers, no Windows required (anyone running production code on mono is a moron). Actual enterprise specifications for Java. JMX is awesome.

---

### Post by directhex on 2011-05-07
> **slavik said:**
> Java: Lots of developed application servers, no Windows required (anyone running production code on mono is a moron). Actual enterprise specifications for Java. JMX is awesome.

[Lots of morons then](http://gamrreview.vgchartz.com/sales/17805/the-sims-3/)

---

### Post by WitchCraft on 2011-05-07
> **slavik said:**
> 
select * from table
limit 1, 10


Oh, you mean: 
```

SELECT FIRST 1 SKIP 10 * FROM table 

```
;-)

> **slavik said:**
> 
yes, paging is difficult.

:lolflag:

It really depends on the database system.
I know PostGre can do the same with limit + offset.
The point is, there are some DB systems where paging is quite "difficult" 
(MS-SQL would be such a case).
```

WITH Example AS (
SELECT 
    Row_Number() OVER (ORDER BY last_name, first_name, age) AS page_nr 
    ,table.*
FROM Table
) 
SELECT * FROM Example 
WHERE page_nr BETWEEN 1 AND 10

```
Now try a distinct on that (ms-sql can only do distinct on ALL columns, and if you page, this includes the row number, which is ALL DIFFERENT of course...)



And IMHO, the simplicity of paging is a good way to judge a database system (because you need to do it much).
The other good way is the availability/simplicity of pivot tables (cross-tabulation).

(See here for example)
[http://stackoverflow.com/questions/5469897/how-to-transform-a-datatable-to-a-reportingservice-like-matrix](http://stackoverflow.com/questions/5469897/how-to-transform-a-datatable-to-a-reportingservice-like-matrix)

Of course, scalability and speed are to be considered too, **IF** you work on a large-scale project (which probably is THE strong point of MySQL).

> **slavik said:**
> 
Java: Lots of developed application servers, 

You only need one - one that works.

> **slavik said:**
> 
no Windows required. Actual enterprise specifications for Java. 
JMX is awesome.

Certainly, for dedicated Linux-only servers/webapplications, Java works better.

I already said I do it because that way I can reuse the code I use at work. 

(
And to keep it cross-platform with windows focus 
[it's 80 % of the market]
).

But if you actually look at configuration GUIs, you'll notice that .NET has some definitive advantages (in how the GUI looks and feels, because that's all a user sees).

Plus you don't need windows to develop with mono.
MonoDevelop has reached a point where you can do it on Linux (for web-development).

It still has some annoying bugs to work-out, but overall, it's great. 

And the one point I would point out is that interop with native libraries is great (X11/etc.).


> **slavik said:**
> 
(anyone running production code on mono is a moron)

Thank you. You've certainly made your opinion clear.

But my experience is that once you got a project working on Linux, it's actually pretty stable.

If you want a challenge, try writing an Excel/Word/OpenOffice-file with Java on Linux (with a FOSS solution).

With mono, you can even do that:
[http://epplus.codeplex.com/](http://epplus.codeplex.com/)
(the library as is needs exactly one correction [stream flush instead of dispose] to work on Linux).

or docx:
[http://docx.codeplex.com/](http://docx.codeplex.com/)

or odf/ods for openoffice:
[http://opendocument4all.com/content/view/13/29/](http://opendocument4all.com/content/view/13/29/)

etc.


So please enlighten me with a reason.
Last time I checked, mono was just as free as Java.

PS:
BTW: You might like this one:
[http://www.ianquigley.com/A75_New_features_of_VS2012_revealed.html](http://www.ianquigley.com/A75_New_features_of_VS2012_revealed.html)

---

### Post by Pynalysis on 2011-10-11
Python + Django + ExtJS is a nice combination worth trying out.

---

