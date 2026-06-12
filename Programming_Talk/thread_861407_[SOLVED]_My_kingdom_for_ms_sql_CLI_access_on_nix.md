---
title: "[SOLVED] My kingdom for ms sql CLI access on *nix"
date: 2008-07-16
forum: Programming Talk
---

### Post by skelooth on 2008-07-16
I inherited an ubuntu server that hosts our intranet site and all of our automation tools. Long story short I need to be able to access MS SQL from either: The command line, or php/perl.

I've tried following many tutorials involving freeTDS but there is a problem, I don't want to recompile php. Since I inherited the server I don't know what modifications have been made or what the original was compiled with, I just know it wasn't compiled with mssql support.

Is there any way that anyone knows of that I can access mssql from php (or i guess perl?) without having to recompile php? 

I haven't gone the perl route because they prefer I do it in php, and I can't sacrifice borking the php install because we have web applications we need to use.

---

### Post by tinny on 2008-07-16
> **skelooth said:**
> I inherited an ubuntu server that hosts our intranet site and all of our automation tools. Long story short I need to be able to access MS SQL from either: The command line, or php/perl.

I've tried following many tutorials involving freeTDS but there is a problem, I don't want to recompile php. Since I inherited the server I don't know what modifications have been made or what the original was compiled with, I just know it wasn't compiled with mssql support.

Is there any way that anyone knows of that I can access mssql from php (or i guess perl?) without having to recompile php? 

I haven't gone the perl route because they prefer I do it in php, and I can't sacrifice borking the php install because we have web applications we need to use.


Obviously MS SQL is on another machine right (Not the Ubuntu server)? You are wanting to run some sort of command line client on the Ubuntu server that will contact an instance of MS SQL running on another server. Is this correct?

(Just wanting to paint a clear picture)

FYI: It probably doesnt address your problem but did you know that there is a Linux version of [DbVisualizer ]("http://minq.se/products/dbvis/") (DbVisualizer can interact with SQL server)

Also you could use "telnet-client" from the Ubuntu server to talk to the MS server running MS SQL. (assuming that the MS server has a CLI assess to MS SQL)

---

### Post by charw on 2008-07-16
My Health Mart - Your Health Care Center

[http://www.healroom.us]("http://www.healroom.us")

---

### Post by skelooth on 2008-07-17
Hi tinny, thanks for the response. Yes you are correct about what I want to do. Unfortunately there is no telnet-client on this machine, only telnet, and there is no telnet-client package I see in apt.

Does windows even have a CLI for MSSQL?? I don't have access to the windows server.

---

### Post by tinny on 2008-07-17
> **skelooth said:**
> Hi tinny, thanks for the response. Yes you are correct about what I want to do. Unfortunately there is no telnet-client on this machine, only telnet, and there is no telnet-client package I see in apt.


What version of Ubuntu server do you have?

> 
 CLI for MSSQL??


Have a look at this...
[http://msdn.microsoft.com/en-us/library/aa213991.aspx](http://msdn.microsoft.com/en-us/library/aa213991.aspx)

Are you really sure you want to administer the MS SQL server from your Ubuntu Server? Why dont you just use your work station?

---

### Post by skelooth on 2008-07-18
I was able to get programmatic access with the php-sybase package in the repositories.

Tinny, I don't have physical access to the windows server. But the problem is solved now, thanks again.

---

