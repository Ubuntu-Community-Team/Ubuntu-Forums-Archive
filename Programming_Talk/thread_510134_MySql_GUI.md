---
title: "MySql GUI"
date: 2007-07-26
forum: Programming Talk
---

### Post by dhtseany on 2007-07-26
Hi guys / gals,

I know this has been asked before but I haven't yet found the exact option I'm looking for:

What I need is an exact (or close to) alternative for MS Enterprise Manager. I need to be able to add/remove databases, tables, rows, etc. I already have MySQL installed along with the mysql-administrator (GUI). Please also note I need it to be a GUI as I suck terribly at command line stuff.

Any help would be greatly, GREATLY appreciated. 

Thanks,

Sean

PS- If you could include the apt name too that would be super :)

---

### Post by LaRoza on 2007-07-26
phpMyAdmin

---

### Post by robgr85 on 2007-07-26
> **LaRoza said:**
> phpMyAdmin

i also recommend phpMyAdmin.

---

### Post by dhtseany on 2007-07-26
Ok heres what I did:

```
$ apt-get install phpmyadmin 
```

Everything seemed to take ok without error.

Now what? Obviously it isn't a "program" in the sense a CLI command will open it. With that being said, how to I use it?

Sean

---

### Post by dhtseany on 2007-07-26
Nevermind, I just went to a browser and tried "http://localhost/phpmyadmin" and it worked.

I'm fiddling with this now and I'll post back if this is what I'm looking for.

Thanks

---

### Post by LaRoza on 2007-07-26
I never used it before, but I am familiar with the interface.

I personally use the command line, and scripts, it is much faster. (Also I find SQL easier than a GUI)

---

### Post by vexorian on 2007-07-26
It is all about choices.

What's good about phpmyadmin is that it can also help you learn SQL since it shows you the queries it uses.

---

### Post by LaRoza on 2007-07-26
> **vexorian said:**
> It is all about choices.

What's good about phpmyadmin is that it can also help you learn SQL since it shows you the queries it uses.

So does MS Access

---

### Post by vexorian on 2007-07-26
that doesn't run on Linux, does it?

---

### Post by LaRoza on 2007-07-26
No, but it allows you to see the SQL, so the above comment was not specific to phpMyAdmin, most DBMS allow you to see the SQL.

---

### Post by DouglasAWh on 2007-10-17
> **LaRoza said:**
> No, but it allows you to see the SQL, so the above comment was not specific to phpMyAdmin, most DBMS allow you to see the SQL.

Access allows you to see bastardized SQL.

On a related note, I need a GUI that will connect to a remote server.  I've got MySQL Administrator installed, but I believe access to the SQL server can only happen through this other server called Ruby.  Does this mean I'll need to use VNC if I want a GUI?  The command line has worked great so far for the database class I am in, but now I'm doing a project database and would like to look at other options.

I did install phpMyAdmin and it looks cool.  If I install a database on my laptop, I might use it.

Access *might* run under WINE.

---

### Post by dhtseany on 2007-10-18
I assume your running Ubuntu, right? 

I believe if you setup the correct web/port forwarding you can connect to myphpadmin since it's all web-based.

I could be wrong (never tried it) but it sounds logical.

As far as Access, yes you can install it using Wine. Have fun though, it was a royal pain in the butt.

Sean

---

### Post by DouglasAWh on 2007-10-18
My experiences with WINE have been positive, but I've never tried Microsoft Word.  IE is installed, though there are some problems.  The one real pain with WINE I have is that it doesn't access my sound card.

I've got an application running through SSL.  SSH is blocked though.  I'm using TOra.  It's not really doing what I was hoping it would do, but it might be a little better than running through terminal.

---

### Post by dhtseany on 2007-10-18
Is this box running in a corporate setting or at home?

---

### Post by DouglasAWh on 2007-10-18
At home.  It's for class.

Let me clarify...the server is on campus and my laptop is at home...or wherever I take it.

---

### Post by airtonix on 2007-12-29
How come your not using openoffice base? it connects to mysql servers.

and it operates just like msaccess

---

