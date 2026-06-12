---
title: "Best Generic Database Frontend"
date: 2011-02-18
forum: Programming Talk
---

### Post by gunksta on 2011-02-18
I'm looking for some feedback. My job requires me to regularly connect to other people's database servers. These are usually running either Oracle or SQL Server but I see a smattering of MySQL and I saw Postgres once (Yay!).

I have used the SQuirrel SQL Client for the last couple of year, but it is slowly driving me batty. I like the flexibility/dependability of using JDBC (I have a very nice collection of JDC drivers and I know how to use 'em) but I'd like to find a lighter/saner tool.

Especially with SQL Server (which is very common, unfortunately) SQuirrel is weird. It will randomly disconnect or get dropped. And then it takes forever to reload things when I exit and come back in.

My question is this -- What generic/universal database front-ends/shells are people using? Connectivity to Oracle/SQL Server are an absolute must-have. The ability to connect to MySQL/Postgres is desirable, especially for when I'm working on something at home where I get to choose the database system in use. I hate switching tools, thus I'm not looking for a 'xyz' is best for Oracle but won't connect to squat else.

I've tried using Vim's dbext but I can't seem to figure out how the heck it connects to a working ODBC connection. Nor can I get it to do a connection through anything else. Using JDBC doesn't appear to be an option with dbext but I'm not married to the idea of continuing to use JDBC. The ODBC connection does work; I use it with R all the time. But for some reason, Vim refuses to use it. 

Thoughts? If you suggest dbext -- any links on how to configure it?

---

### Post by SeijiSensei on 2011-02-18
I'm going to propose an answer that will be unpopular here -- Microsoft Access.  It will connect to everything in your list via ODBC drivers, and you can create a client database that links to tables in multiple external DBs.  While I'm pretty adept at writing SQL queries, it's often nice to be able to create a query or report graphically using Access.

I use Linux for 99% or more of my computing needs, but I haven't found anything that can compete with Access as a graphical front-end for databases.

(I don't know about JDBC, but I can't imagine there's any standard out there that cannot be connected to Access.)

---

### Post by gunksta on 2011-02-21
Brave soul, suggesting Access on the Ubuntu Forums. I have done that before, running Access in a VM, but I'd prefer a solution that doesn't involve a VM. I've been playing around with Eclipse, but have had a hard time setting it up.

---

### Post by thornmastr on 2011-02-22
> **SeijiSensei said:**
> I'm going to propose an answer that will be unpopular here -- Microsoft Access.  It will connect to everything in your list via ODBC drivers.
I use Linux for 99% or more of my computing needs, but I haven't found anything that can compete with Access as a graphical front-end for databases.

(I don't know about JDBC, but I can't imagine there's any standard out there that cannot be connected to Access.)

Please note, this is being done by ODBC not VM. 

While I am not a lover if M$, I do appreciate Access and agree with most of what Seijji<sp> said. I have found these articles to be helpful and perhaps they will help the OP.


[http://sourceforge.net/projects/mdbtools](http://sourceforge.net/projects/mdbtools)
[http://dba.openoffice.org/drivers/mdb/index.html](http://dba.openoffice.org/drivers/mdb/index.html)
[http://solyaris.wordpress.com/2007/0...iles-on-linux/](http://solyaris.wordpress.com/2007/0...iles-on-linux/)

and,
[http://www.oooforum.org/forum/viewtopic.phtml?t=75155](http://www.oooforum.org/forum/viewtopic.phtml?t=75155)
[http://www.oooforum.org/forum/viewtopic.phtml?t=41006](http://www.oooforum.org/forum/viewtopic.phtml?t=41006)
[http://www.oooforum.org/forum/viewtopic.phtml?t=39816](http://www.oooforum.org/forum/viewtopic.phtml?t=39816)

HTH,

Thorny

---

### Post by gunksta on 2011-02-22
> **thornmastr said:**
> Please note, this is being done by ODBC not VM. 

I assume you are referring to my earlier statement that I would prefer to not use a VM. On my current system, using Access requires me to use a VM. Of course, Access uses Windows' ODBC system to connect to various databases but the only way for me to (practically) use Access is to run it as a virtual machine (KVM in my case).

This is an effective solution, in that most databases include ODBC drivers for Windows and Access can then use these connections to run queries against the foreign data set, but I would like to find a tool that doesn't require me to start a Windows VM, just to run a query.

I don't even mind using tools like sqsh, but I would like to find one that is flexible enough to connect to multiple databases, so I only have to become familiar with one tool.

My workflow looks like this - I develop a few queries, to access to client data I need. Once I have a query (queries) providing the necessary info, I run these through R (using the appropriate connection RODBC, RMySQL, etc.) to actually download the data. Once the data is in R, I crunch it and do things with it. Using R as a development platform for the queries (and any stored procedures/views I need to produce) is impractical, thus my search for a better tool.

---

### Post by thornmastr on 2011-02-22
> **gunksta said:**
> I assume you are referring to my earlier statement that I would prefer to not use a VM. On my current system, using Access requires me to use a VM. Of course, Access uses Windows' ODBC system to connect to various databases but the only way for me to (practically) use Access is to run it as a virtual machine (KVM in my case).


My workflow looks like this - I develop a few queries, to access to client data I need. Once I have a query (queries) providing the necessary info, I run these through R (using the appropriate connection RODBC, RMySQL, etc.) to actually download the data. Once the data is in R, I crunch it and do things with it. Using R as a development platform for the queries (and any stored procedures/views I need to produce) is impractical, thus my search for a better tool.

My error. I thought you were looking for a tool simply to open and query the database. As I'm almost certain you are aware ODBC will let you easily attach to an Access mdb. I did not realize you needed to use the rest of Access such as the Query designer, form designer, etc. In your situation, you are absolutely correct. VM is the only route to take. I wish I had a better solution but obviously I do not.

Thorn

---

### Post by gunksta on 2011-02-22
Apparently, nobody else does either. I may just continue using SQuirrelSQL, until I can find something that works a little better.

---

### Post by StephenDavison on 2011-02-22
Unfortunately, I've never looked at SQuirrelSQL and so I don't know where you're coming from.  I have played around with Eclipse DTP some, albeit in WinXP at work, and so I might be able to help you get that working.  You might also try running TOAD under Wine:
[http://www.toadworld.com/BLOGS/tabid/67/EntryId/329/Run-Toad-Freeware-on-Linux.aspx](http://www.toadworld.com/BLOGS/tabid/67/EntryId/329/Run-Toad-Freeware-on-Linux.aspx)
I have no idea how that will work out, but I love the Windows version of TOAD for Oracle.

---

### Post by slavik on 2011-02-23
are you connecting to a database for the data or for management?

for management, there is tora, but I haven't bothered too much to get it to work with Oracle or any other DB.

For the data, there is Aquadata Studio which I used for a short while while taking a DB class.

---

### Post by gunksta on 2011-02-24
I am more interested in the data than management. 

TOAD looks interesting. I downloaded the Freeware Toad for Data Analysts. I will look at Aqua Studio too. In my wanderings, I found a tool called RazorSQL which also looks interesting.

---

### Post by gunksta on 2011-02-25
RazorSQL looks like a sweet project. It costs money, but it looks like the full version comes with drivers to read from Access files. It would be REAL slick if this is a JDBC driver that could be used by other programs too. I may have to buy it just for that single reason. I need to look at Aqua to see how it compares on the provided drivers front.

Another option that exists is emacs. Emacs wants to use osql to connect to the database and I can't find a way to change it to use something that actually exists on the linux platform. I'm not too interested in building my own custom solution based on comint.

---

### Post by gunksta on 2011-02-25
AquaData Studio is an impressive project indeed. It also costs $399 to license. There's a lot to the product, but I'm not sure it's worth that much $$$ to me.

[RazorSQL]("http://www.razorsql.com") doesn't have as many bells and whistles, but it seems to do most of what I need, and doesn't cost an arm and a leg.

I've also looked at some products made by [SQL Power]("http://www.sqlpower.ca/page/splash"). They are FOSS and, like RazorSQL and SQuirrel, they run on Java. I'm not sure if I like them as much as Razor, but they also have some reporting features that seem rather interesting to me.

---

### Post by gunksta on 2011-03-18
In the end, I decided to evaluate three tools.
- [Squirrel SQL]("http://squirrel-sql.sourceforge.net/") (FOSS)
- [Execute Query]("http://executequery.org/index.jsp") (FOSS)
- Eclipse (FOSS)
- [RazorSQL]("http://www.razorsql.com/") (Proprietary)

All four programs use JDBC drivers to connect to databases, so you can use any of these to connect to just about everything, which is an absolute necessity for me. JDBC drivers even exist for Access, although they are darned expensive. Most databases make JDBC drivers available for free and many are FOSS, which is why I tend to like using JDBC for connecting to databases.

I started off using Squirrel SQL which is, overall, a very nice product. Unfortunately, the user interface is disadvantageous for me. I spend 99% of my time working on clients' databases. Because of the high project turnover rate, my familiarity with column names/properties is often a little weak. Squirrel's interface is such that you can't see column names and types when writing queries. I tend to rely on this information to write my queries, thus Squirrel's interface was not a good fit for my needs. If you are developing against a database you know very well, this will be less of a disadvantage for you. Squirrel SQL does provide a large number of helper functions. Squirrel's text editor also has this weird tendency to ignore the space bar, resulting in a lot of SELECT*FROM statements that I have to go back and correct, which doesn't really hurt anything, but it is annoying and it slows me down. Even more frustrating was Squirrel's tendency to drop remote connections when left idle.

Execute Query is another nice product that just falls short of the mark. The text editor is much better than Squirrel's in that it always enters a space when I ask it to, on my first try. That alone is a worthy upgrade. It also provides a very nice side bar, displaying table/view/stored procedure information. Very useful, especially for me. It's a rather ugly program, with icons that look positively 1985, but I'm not going to judge a programming tool based on looks. After-all, I tend to use emacs for my other programming needs. Someday I'll teach emacs how to talk to SQL Server via freetds and I'll probably stop using all other editors. In the meantime . . . . In the end, Execute Query lost simply because it's not stable. It has a bad habit of freezing up and occasionally crashing. It seems like it has some nice helper functions, but they often cause the program to freeze or hang, making them considerably less useful. I really liked Execute Query's built in SQL format tool. It formats queries in a consistent, readable style that I really like. I would like to peel the SQL formatter out of Execute Query and use it in Razor. I'm not sure if Execute Query dropped connections when left idle. It rarely stayed running long enough to idle out. It usually hung or crashed before I had a chance to move on to something else and leave it idle.

I played around with Eclipse but decided the learning curve was too steep. I'm not a Java developer and never will be. I'm sure Eclipse is a nice product but the learning curve is similar to Emacs or Vim and the result is a much heavier tool that isn't as flexible. (Biased opinion, I know.) If I am going to invest that much time learning how to use a tool, I will spend it peering into the murky depths of emacs, not Eclipse. The SQL development workflow I came up with felt completely bastardized in Eclipse. The tools feel bolted on, and are not as integrated as I expected. There's a lot of power under the hood, but it was just too much effort. On the plus side, I'm sure it comes with a nice text editor. I suppose I should also look at netbeans and I may continue to explore different ways to use Eclipse.

In the end, I ponied up and purchased a license for RazorSQL. Unlike the other proprietary tools that folks recommended, a license for razorsql only costs $70. Not too bad. Razor SQL's interface is similar in structure to Execute Query, which I really liked. It looks a little nicer (although it is definitely a Java app) and the icons look like they are from the mid 90's rather than the mid 80's.  :)  More importantly, the text editor is fantastic and it doesn't crash or hang. It's not emacs, but it is fast, responsive and does a good job with syntax highlighting. It also manages to record ALL of my attempts to use the space bar. Setup was a piece of cake and I was up and running in no time. It keeps connections open, even when I leave it idle and it doesn't crash. It has a very flexible SQL formatting tool and once I learn how to make it replicate the results from Execute Query, I will have a very nicely configured SQL tool. The helper functions like the data import/export routines work as expected and seem pretty robust. It did choke on a CSV file that was a little more than 1G, but it had some tricky formatting problems. Most programs choked on this file and the other files I imported via Razor's import interface worked well. The dialog boxes for importing are a little complicated, but once you have done it once or twice and you know where they hide the buttons at the bottom of the dialog box, everything works as expected.

I would have preferred to settle on a FOSS option, but I just couldn't find one that seemed to meet my needs. Razor SQL is proprietary, but it seemed to be the best fit and didn't cost me an arm or a leg like some of the other suggested here.

I'm going to mark this as solved, in the hopes that someone else may find this useful.

---

### Post by eugenio11 on 2011-04-21
You can also try DaDaBIK: [www.dadabik.org](www.dadabik.org)
It's open source and supports MySQL, PostgreSQL, SQL Server, Oracle and SQLite.

---

