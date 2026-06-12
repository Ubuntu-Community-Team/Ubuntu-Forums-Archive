---
title: "Seeking advice."
date: 2008-02-01
forum: Programming Talk
---

### Post by Vadi on 2008-02-01
I have a task at and, but really have absolutely no idea how to get started on planning, and coding this.

Here's essentially what needs to be done: I'll have x clients and a server. What I'll need to have is a text file on the server that the clients can download (and use, but that's outside the scope of this). This text file is split into sections, that if any of the sections are updated, next time the client checks the server, the newly updated sections will need to be downloaded (or the whole file, since the client will be able to deal with sorting out the section it needs, but that'll be a waste of bandwidth).

Now, the other part is that the clients are able to update sections, and export them appropriately into a text file. This text file will need to be uploaded to the server, and the server will then need to update the proper section of this "master" text file.

So that whenever other clients ask if there's an update, the server will send them the updated section, and everybody's up to date.


Now comes the implementation part - the requirements are that it must be cross-platform (or easily portable...), and preferable not too hard to deal with from my C programs.

I've been told of using svn (where the master file would be just pointing to other text files, one for each sectoin) for this, but that gets really complicated (while I can call batch/bash scripts to use svn commands for me, if an error happens, I'm a bit screwed. Unless I do pipe parsing and so on, if I understand right...), or use an CGI script that interacts with SVN on the server side and with simple socketing to my client-side C program, or just make up my own server/client side C programs that interact with files...


I really don't know on how to get started. If anyone has had any experience with this, or just a suggestion, let me know? :confused:

---

### Post by jeffus_il on 2008-02-01
I would use a SQL database like MySql, It solves all your problems of multiuser, multiplatform, locking etc, Its made for storing text, and is very standard, If you really need the file as text, the you can redirect the output of a SQL query to a text file.

---

### Post by LaRoza on 2008-02-01
Also, you should watch out for conflicts if you go the database route. It sounds like you need a database, and building a web interface for this would be easy, but transactions will be key.

(That is not MySQL's strong point, so [http://www.postgresql.org/](http://www.postgresql.org/) might be worth considering)

---

### Post by Vadi on 2008-02-01
Okay, so lets say instead of text files I'll have a DB.

But I'd still need /something/ server side and client side to work with the DB..

---

### Post by pmasiar on 2008-02-01
Maybe just a a bash script with rsync?

---

### Post by spyder0101 on 2008-02-01
Although a database would be best, your comments indicate you are not especially familiar with them.  Another option would be to have separate text files for each section instead of just one text file.

As far as how to code it, I recommend Perl.  It is, in my opinion, the best language for text processing and has a really low learning curve.

Best of luck on your project,

Spyder

P.S. You might wan to check out sourceforge or similar sites to see if there is a pre-made solution for what you need.

---

### Post by aks44 on 2008-02-01
> **Vadi said:**
> Okay, so lets say instead of text files I'll have a DB.

But I'd still need /something/ server side and client side to work with the DB..

As far as MySQL goes, a standard MySQL server does the trick server-side, and client-side you may want to wrap all the MySQL-specific code into a well abstracted (shared) library so that clients don't have to know more than server address, user name and password.

FWIW I second the database advice, it makes life very easy [COLOR="DimGray"]*(once you know how to deal with it)*[/COLOR].

---

### Post by LaRoza on 2008-02-01
Well, the client could just be a web browser. 

Note: I view the world through the eyes of a web developer and that is where my strong points are. As for the language, you can use PHP, Perl, Python and Ruby with no problems for this, as long as the server has them available. PHP is my preference and how I would do it, but that is only because that is what I do in real life.

---

### Post by Vadi on 2008-02-01
Yes, I think I'll just make several text files as spyder0101 suggested - I know how to manipulate those from C already.

One challenge is to make sure that only one person can be "working on" a section at a time. I guess I'd have to record the IP addresses - this would require a server-side program to keep things secure, right? So that anybody can't just find the file in use and get all addresses. I guess a database would be needed here.

---

### Post by LaRoza on 2008-02-01
> **Vadi said:**
> 
One challenge is to make sure that only one person can be "working on" a section at a time. I guess I'd have to record the IP addresses - this would require a server-side program to keep things secure, right? So that anybody can't just find the file in use and get all addresses. I guess a database would be needed here.

That is what a transaction is. If you use a database, you can do all of that with SQL.

---

### Post by Vadi on 2008-02-01
Okay. Any google search terms to get me started? :|

---

### Post by LaRoza on 2008-02-01
> **Vadi said:**
> Okay. Any google search terms to get me started? :|

Do you have a language in mind?

For the server and client model, you will need:

* Server (LAMPP)
* Database server (MySQL or PostgreSQL)
* Language (PHP, Perl, Python) I recommend PHP if you don't know any of the others.

You will need to be able to make a web page in XHTML, which would be rather simple.

The key is the backend, needed knowledge:

* SQL (It is standard, but each database management system has there differences, especially for transactions)
* SQL and Transactions
* SQL Injection prevention

I don't know how much you already know, so this may be a lot or very little.

---

### Post by pmasiar on 2008-02-01
Looks like you want to reimplement version control system? :-)

You may just get SNV server, SVN client for users (like Tortoise for Windows, pysvn workbench cross-platform), and checkout directory with files. They can use any editor they like, even edit different areas of the same files, and changes are merged OK. You will get edit conflict only if they edit same part of text, and even then it is not too hard to resolve (and nothing is lost).

---

### Post by Vadi on 2008-02-01
Very little.

I already have a shared hosting plan, and they got mysql, postgresql, php, and everything else I've needed so far in there. I also have ssh access to the server.

Sql injection I know off too. Nasty things.

I'm not sure I need XHTML - I'm not dealing with browsers here. The client-side programs are just console based (they actually deal with other programs). 

I won't have any difficulties parsing the files client-side or managing them on the server (if I can write a C programon there). The hard parts are transmitting the files back and forth, and making sure that only one client is editing a part at a time :|

Edit: Yes, it does sound very similar to a revision control system like SVN. But integrating that proved a bit difficult - keep in mind that I need to care about Windows here too :/. And all of this should be as transparent to the users as possible.

---

### Post by LaRoza on 2008-02-01
> **Vadi said:**
> Very little.

I already have a shared hosting plan, and they got mysql, postgresql, php, and everything else I've needed so far in there. I also have ssh access to the server.

I won't have any difficulties parsing the files client-side or managing them on the server (if I can write a C programon there). The hard parts are transmitting the files back and forth, and making sure that only one client is editing a part at a time :|

I don't know what your client is like, a browser is the most universal.

If you have that part handled, then it makes it easier.

You can have C on the server, the SQL will handle the transactions.

---

### Post by Vadi on 2008-02-01
The client would simply be a C program. I do need a way to download files from the program though.. hm.

---

### Post by LaRoza on 2008-02-01
> **Vadi said:**
> The client would simply be a C program. I do need a way to download files from the program though.. hm.

A browser would be an easier method...

Is this client software already written?

---

### Post by Vadi on 2008-02-01
Yep, it is. Everything client-side, save for the "locking" mechanism is completed.

I found this cURL project, going to take a look at this meanwhile.

---

### Post by popch on 2008-02-01
It seems that part of the specifications for the interactions of the clients with the server and for the treatment of the text file(s) could be implemented with HTTP or, perhaps, WEBDAV. Checking out a document, sending a new version and querying the version of a document are all covered by those protocols. Hence I assume that the code to implement the server behaviour ought to be already present in currently available servers.

Implementing a client for HTTP or WEBDAV ought not to be all that difficult, I think.

---

### Post by aks44 on 2008-02-01
> **Vadi said:**
> The client would simply be a C program. I do need a way to download files from the program though.. hm.

Again, you can do all this with a SQL client alone (the server only needs a *standard* SQL server, no additional development needed there).

MySQL provides a client-side C library that allows one to remotely access the server, Postgre surely has an equivalent library too.

As stated before, SQL transactions will take care of the clients' mutual exclusion with very simple SQL statements (as far as MySQL goes BEGIN TRANSACTION followed by SELECT *some records* FOR UPDATE will block any other client from writing those records as long as the issuing client does not COMMIT the transaction).


No need to mess with sockets, no need to reinvent the wheel... As far as I'm concerned I hardly see how record locking could be done more easily. Just my 0.02 :)

---

### Post by pmasiar on 2008-02-01
> **Vadi said:**
> 
Edit: Yes, it does sound very similar to a revision control system like SVN. But integrating that proved a bit difficult - keep in mind that I need to care about Windows here too :/. And all of this should be as transparent to the users as possible.

Not sure what do you mean. Tortoise is SVN client - plugin for Windows Exploder file manager. pysvn workbench works on both Win, Linux and Mac. Not sure what do you need to integrate. 100% work is done for you, it just works.

Tortoise looks like funny icons and is added to right-click menu. User can use any editor for editing, then upgrade/commit etc from file manager. Workbench is little less slick but easy too.

All you need is SVN server.

---

### Post by Vadi on 2008-02-01
Right, the thing is, I don't want to teach people how to use svn. At most, I'd like to have "update", a "lock <area>", and a "commit <area>" commands in my client, and that's it.

As for SQL - I'm worried about injections :/. But could still be a good starting point. Where can I find that C library?

---

### Post by pmasiar on 2008-02-01
so your problem is, too many options in right-click menu of Tortoise? And your solution is to create custom client/server version control etc?

Reinventing the whell if I ever seen one. And your wheel is not even square: it is a triangle. 

Have fun! And be worried about security of your web app! Good luck, you will need it!

---

### Post by aks44 on 2008-02-01
> **Vadi said:**
> As for SQL - I'm worried about injections :/. But could still be a good starting point. Where can I find that C library?
On Ubuntu, the MySQL client library is contained in the libmysqlclient* packages (including the -dev package).

As far as SQL injections go: you gotta know *what exactly* is an SQL injection.

Just like buffer overflows, SQL injections don't happen by themselves, they first require an incompetent programmer to enable them. ;)

As long as you correctly escape (mysql_real_escape_string, prepared statements, ...) the variable parts of your queries then you're safe. Be sure to read exactly how injections work, but believe me: they are *very* easy to avoid (just like buffer overflows and XSS) if you're only half competent and know what you're trying to avoid. :)

IMHO this category of vulnerabilities stems from the fact that way too much "programmers" (read: code monkeys) don't have a single clue about what they're doing.

---

### Post by Vadi on 2008-02-01
The main task of the program is not revision control, it's completely different. I just need revision control at 5% of the programs functionality - so getting a full-blown SVN solution won't work. Plus, I can't be expecting users to be clicking the svn update button every hour, I'd rather have it all handled by the program.

Well, that's great, thins are easy on Ubuntu. But 98% of my users are on Windows. I'll need to see if there's a similar easy solution on there.

---

### Post by aks44 on 2008-02-01
> **Vadi said:**
> Well, that's great, thins are easy on Ubuntu. But 98% of my users are on Windows. I'll need to see if there's a similar easy solution on there.

The MySQL client library is available on Windows too (IIRC it is packaged with the full-blown MySQL server download for Windows).

---

### Post by Vadi on 2008-02-01
... and my app is under 1mb. :|

Sorry, I think that's just a tad too much for this project. But thank you for the suggestions :)

---

### Post by LaRoza on 2008-02-01
> **Vadi said:**
> ... and my app is under 1mb. :|

Sorry, I think that's just a tad too much for this project. But thank you for the suggestions :)

Whats too much? MySQL? You can try SQLite, which isn't a server.

---

### Post by pmasiar on 2008-02-01
> **LaRoza said:**
> You can try SQLite, which isn't a server.

Exactly. SQLite is single user libary, and he needs multiuser server, so this is one of situation where SQLite is **bad** match.

---

### Post by LaRoza on 2008-02-01
> **pmasiar said:**
> Exactly. SQLite is single user libary, and he needs multiuser server, so this is one of situation where SQLite is **bad** match.

Well, it seems that none of what we say matches...

---

### Post by pmasiar on 2008-02-01
> **Vadi said:**
> The main task of the program is not revision control, it's completely different. I just need revision control at 5% of the programs functionality - so getting a full-blown SVN solution won't work. Plus, I can't be expecting users to be clicking the svn update button every hour, I'd rather have it all handled by the program.


pysvn library (used to build Workbench) is such cross-platform app framework. You can write any desktop app with it, and you have Workbench to look as sample code.

You of course can go with database app, and locking, and lock expirations, and overwriting data, losing data after saving over expired lock and stuff, and handle all that crap manually. But you need to write custom GUI anyway, and from your OP seems to me you already wrote your GUI in C and looking for a storage mechanism only.

Well, it is not like I would build such app, IMHO C is for libraries which needs to be efficient and it is waste of time on high-level stuff, but it is your project. Have fun.

---

### Post by scorp123 on 2008-02-01
> **Vadi said:**
>  ... So that whenever other clients ask if there's an update, the server will send them the updated section, and everybody's up to date ...  Sounds like you want this:
[http://www.ifolder.com](http://www.ifolder.com)

Or if you prefer a commercial package + support:
[http://www.novell.com/products/openenterpriseserver/file_and_storage_services.html](http://www.novell.com/products/openenterpriseserver/file_and_storage_services.html)

I read about the other suggestions here ... Frankly, why not SVN or CVS?? Those solutions are not *that* hard. :)

Of course it would help if you explained more what exactly your clients are supposed to do ... e.g. what's that file they are supposed to be working on? It would help to understand you better if you gave more details about that and would not speak about it in such cryptic and semi-mysterious terms ... :)

---

### Post by Vadi on 2008-02-01
Yeah, I really should. It's for a MUD game. The text file in question is a map. The sections are just areas of a map. While most users will just want their map up to date, there will be some that'll do mapping also. When someone wants to map, they'd "lock" an area so that nobody else can map meanwhile - I don't want to deal with having to merge areas.

And when an area gets updated by someone, all clients would download the appropriate area again. Client-side reloading of areas on the fly is already taken care of.

(now I hope you see why an SVN is overkill! Oh and I don't know anything besides C/C++ atm. Not much time to learn new languages either)

---

### Post by pmasiar on 2008-02-02
[So you want to make your own](http://sol.gfxile.net/mmorpg.html) multiuser online game: "I'm saying you shouldn't. But wait - I'll explain why. " 

Read it, and think hard. Unless you have team of seasoned pros, you are just not going to make it, and you don't. Even your first choice was C++ language, because "Not much time to learn new languages either" - so you just proved you are not at pro level. Pro will learn tool best suited for the job. C++ is for "close to the metal" system programming, not for flexible scripting of tools and libraries.

Good luck, you will need it!

BTW Python has interesting and very flexible framework for creating MMO games, Twisted. Includes chat server, client-server protocols and stuff.

---

### Post by Vadi on 2008-02-02
It's not a game either, the game is already done. This is just a mapping addon, you can say. (I'm not crazy enough to make any games on my own).

Right now I'm thinking on how to get the area "locking" done right. Out of all possible methods, I think a simple password way would be the easiest, but does anyone have any other ideas?

---

