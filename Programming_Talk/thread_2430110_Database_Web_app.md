---
title: "Database Web app"
date: 2019-10-28
forum: Programming Talk
---

### Post by GirishSharma on 2019-10-28
Hello,

I am having some experience of development of database web apps in Microsoft Visual Studio using VB.NET.  Now, I have realized that I have spoiled my life and career in non-sense MS tech which :
1.Don't have security
2.Don't have good and easy documentation for developer
3.Buggy error messages
4.Memory Hunger / Resource enemy
5.Poor Support
6.Idiot Forums
7.List goes on....

So, I am looking similar environment in Ubuntu which have drag and drop feature of controls for development of web and desktop apps like Visual Studio. Kindly suggest IDE which :

1.Supports Drag and Drop control
2.Visual Basic support (I don't know VB in Ubuntu...!!)
3.Free
4.etc.

---

### Post by slickymaster on 2019-10-28
*Thread moved to **Programming Talk**.*

---

### Post by TheFu on 2019-10-28
I've never heard of any Unix environment like that, except Delphi, which is dead.
Every DB webapp I've written used code and for the last 10+ yrs, ORMs.  There are some shortcuts if you don't need security and have a simple 1-table CRUD webapp - that can be done in about 15 lines of code with some frameworks like Dancer [http://advent.perldancer.org/2011/2](http://advent.perldancer.org/2011/2), probably others too.  Just depends on the language used which frameworks are available.

For creating webapps, I use vim as my editor of choice. This is because Unix/Linux is the IDE for any programming language. No need for some huge, bloated, application.  [https://sanctum.geek.nz/arabesque/series/unix-as-ide/](https://sanctum.geek.nz/arabesque/series/unix-as-ide/)  This has been how Unix applications were developed for many decades.

---

### Post by sdsurfer on 2019-12-10
I think you're likely to have to use a VM or Wine to find a way to develop VB or .net in Linux/Ubuntu. These are proprietary MS languages. Technically you could in something like NetBeans and tweak it to fit, but it would be similar to using a super powered text editor.

---

### Post by TheFu on 2019-12-10
> **juniors331 said:**
> Why not VS code? By the way, it has a lot of extensions, which allow to manage with some specific databases ...

Why not use some software from Microsoft?  Because I remember the last 30 yrs and what Microsoft has done.  The question for me is why would I trust MSFT?

*"Those who don't know history are doomed to repeat it.&#8221;*

Writing direct SQL is so, so, 1990s.  By using ORMs, created by really smart people, we application devs don't need to worry as much about optimizing queries. The ORM handles that.  We do need to follow reasonable DB design techniques, however.  It handles escaping all SQL statements, supporting all the popular DBMS,  allows for graceful upgrade/downgrade methods to the DB schemas.  I wouldn't want to manually do that stuff again.  In the late 1990s, I wrote my own cross-DBMS upgrade/downgrade tool. We used it to manage the DB versions were I worked internally and for all clients. It worked on 12 platforms, including MS-Windows.

I work remotely, a lot, on servers that don't have any GUI libraries.  Vim doesn't care.  vim allows remote editing using rsync or I can just mount the remote file system using sshfs if I don't want to put my tools there.  Most of the time, I'll just ssh into the server and code directly on it. Clients like to see that. Gives them a feeling of ownership and it doesn't matter to me.

There are DB-centric tools like Toad, if you want to spend money.

---

### Post by SeijiSensei on 2019-12-10
Most web apps on the Linux platform use a combination of PHP, Perl, or Python to code the application, and database systems like MySQL or PostgreSQL on the backend. This site is written in PHP; DK what database it uses. WordPress uses PHP and MySQL. I write in PHP and largely use PostgreSQL on the back end.

I don't know of any visual development tools for this environment. I write all my code in a standard text editor.

---

