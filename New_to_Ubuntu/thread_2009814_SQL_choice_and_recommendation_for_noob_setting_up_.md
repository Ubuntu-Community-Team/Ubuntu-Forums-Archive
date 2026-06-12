---
title: "SQL choice and recommendation for noob setting up the server side"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by RH9R on 2012-06-25
I've used T-sql in my work, but never had to install or setup the server side of a sql install. I've wanted to try either postgresql or mysql, but the server side setup always got in the way. 

The objective is strictly to play w/ sql on my own machine - not web service. 
 
Is there a recommended 'how-to' or tutorial on how a noob gets the client and server installed in 12.04?

---

### Post by Gone fishing on 2012-06-25
The HowtoForge howtos are pretty good in my experience have a look at

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp)

and 

[http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

The first link looks the most relevant.

---

### Post by RH9R on 2012-06-25
Much obliged, Fishing. 
 
The lamp installs seem oriented towards one wanting to publish web apps. Would it be safe to say I don't need Apache or PHP to do stand alone database work? Such that I could either uninstall Apache and PHP?

---

### Post by Cheesemill on 2012-06-25
You don't need to install Apache or PHP in the first place.
To install MySQL:
```
sudo apt-get install mysql-server
```
This will install MySQL server as well as the command line client interface. If you want a graphical application to administrate MySQL Server you can install MySQL Workbench as well:
```
sudo apt-get install mysql-workbench
```

---

### Post by SeijiSensei on 2012-06-25
I'll throw in my two-cents for PostgreSQL.  I find it much easier to administer with convenient commands like "createuser" and "createdb".  I find controlling access by editing pg_hba.conf easier than the [noparse]'user'@'host'[/noparse] business in MySQL as well.  PostgreSQL conforms to standard SQL syntax so queries you write for it export more easily to something like Oracle.  Finally you get to use a true "enterprise-class" SQL server for free.  What more could you ask for?

I've never understood the reasons for MySQL's popularity.  At one time it was claimed to be faster on SELECTs, and so better suited to high-traffic websites.  I've never built a site that was so heavily used that PostgreSQL could nor provide snappy replies.  I also think those performance advantages have narrowed over time.  Now that MySQL is owned by Oracle, it's always going to be the "little brother" to Oracle itself.  PostgreSQL competes against Oracle directly.

You can install PostgreSQL alone without Apache or PHP by running:

```

sudo apt-get install postgresql

```

If you're running Ubuntu 12.04, you'll get version 9.1 of PostgreSQL.  That will also install the command-line client "psql".  I typically do everything from the command prompt, but I'll occasionally run MS Access on Windows and talk to my PostgreSQL databases using its [ODBC driver]("http://www.postgresql.org/ftp/odbc/versions/").

---

### Post by Gone fishing on 2012-06-25
You don't need Apache and PHP, however, a lot of database work is now web related and so I thought it would be relevant.

---

### Post by RH9R on 2012-06-25
Much gratitude, all. I very much appreciate your kind help. I need to shake some rust off some skill I've not used in a while and this will help a bunch. 
 
I sure appreciate your help!

---

### Post by RH9R on 2012-06-25
Sensei, 'Just tried to install postgresl and could find nothing to indicate it installed or what to do next. Search of install instructions seemed to be for all prior versions. 'Apolgies for the ignorance, but wanted to give a non-Oracle version the first shot. If there's a good how-to for the ignorant, I'd be a good candidate. 
 
The postgresql site instructions seem to presuppose a bit more savvy user.

---

### Post by RH9R on 2012-06-25
'Trying Mysql, and install went okay, but starting the first db connection is giving me errors:
 
The 'Create New Server Instance Profile shows two radio boxes highlighted that say: "Check location of start/stop commands" and "Check Mysql configuration file"
 
"Error: /etc/init.d/mysqld start is invalid"
 
All else has been fine - just walking through the wizard. If this is familiar to anyone, I'd appreciate the kind help.
 
Many Thx.

---

### Post by gordintoronto on 2012-06-25
Did you Google: PostgreSQL tutorial

---

### Post by RH9R on 2012-06-26
Gordin, Good question. 
 
Yes, I did - skimmed through 4 that seemed like they'd be great for a more advanced user. The one I found on mysql looked about my speed, and went great until that one step on the wizard. 
 
The docs in sql workbench seem straight forward, though for now, I'm still stuck. 
 
The error msgs seem reasonably specific, but I don't have the experience yet to know where or how to check the start/stop files or config files. I'm very happy to chase the info on how to troubleshoot. 'Seems the least I can do when I ask for help.

---

### Post by Gone fishing on 2012-06-26
I wonder if this is useful it is a Mysql admin tool written in php [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php).

---

### Post by RH9R on 2012-06-26
Gone Fishing - I'm thinking the same way. I've tried using the workbench - was looking hard at pgAdminIII. Perhaps the php version might have a better go at it. That the workbench would default to start/stop commands that didn't work is a bit of a surprise. I'm not able to confirm or refute, but it seem there's alot of writing about 'upstart' (an ubuntu service mgmt piece?) vs the native mysql 'start' and 'stop' commands.

---

### Post by Cheesemill on 2012-06-26
To be honest you don't actually need to use MySQL Workbench.

I do all of my MySQL administration directly from the command line.

---

### Post by SeijiSensei on 2012-06-26
> **RH9R said:**
> Sensei, 'Just tried to install postgresl and could find nothing to indicate it installed or what to do next. Search of install instructions seemed to be for all prior versions. 'Apolgies for the ignorance, but wanted to give a non-Oracle version the first shot. If there's a good how-to for the ignorant, I'd be a good candidate. 
 
The postgresql site instructions seem to presuppose a bit more savvy user.

Last I time I installed it from the deb, it set up the server and started it up.  If you haven't rebooted since installing PG, run the command "ps ax | grep postgres".  You should see a few processes.  Another quick test is "telnet localhost 5432".  Does the server reply?  You can try restarting the server with "sudo service postgresql restart"; you should get an OK when it's running.

You can have both PostgreSQL and MySQL running on the same server since they listen on different ports, 5432 for Postgres and 3306 for MySQL.

If the server is running, try creating a database for yourself to play with.  First, you need to create a user account in Postgres that matches your Unix account.  If you log into Linux as "myusername" then you'd run

```

sudo su -
su postgres
cd
createuser myusername
[say yes creating new DBs; no to the other questions]
exit
exit

```

Now, using your own Unix account, run the command "createdb myfirstdb" to create a database called "myfirstdb".  You can now connect to that database from the command prompt with "psql myfirstdb". From here on, you'll be typing SQL commands.  \h will show you a list; \? will show you some useful psql commands.

The documentation covers the process of creating tables, populating them, and running queries.  I'd start [here](http://www.postgresql.org/docs/9.1/interactive/tutorial-createdb.html).

---

### Post by SeijiSensei on 2012-06-26
I haven't tried using OpenOffice Base in a very long time, but I turns out I'm building a fairly large PostgreSQL database and wanted to create some spreadsheet tables containing subsets of the data.  This is a pretty common task, and one I was used to doing with MS Access and ODBC.

Well, there's now a native PostgreSQL driver in OpenOffice/LibreOffice.  I decided to take the [new Mozilla OpenOffice version]("http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html") out for a spin. I purged libreoffice, added the PPA, and installed OpenOffice.  Then I followed the instructions at [http://www.openoffice.org/dba/drivers/postgresql/index.html](http://www.openoffice.org/dba/drivers/postgresql/index.html).

I went through the steps of creating a new OO database, pointed at the remote machine with a "URL" of "dbname=mydb host=myhost", entered the username, and up came my database on my remote server over the Internet.  I'll see how easy Base turns out to be to use.  In the early days it was horrible, but a long time has passed since then. If OO Base does what I need, it would help rid me of one of my few remaining reasons for running Windows.

I mention this because it offers the possibility of easily populating remote database tables from spreadsheets and CSV files.  The standard method to import data into PostgreSQL is from tab-delimited records read with the psql COPY command:

```

CREATE TABLE mytable (field1 integer, field2 varchar, etc.);
COPY "mytable" (field1, field2) FROM stdin;
123[tab]Joe
124[tab]Fred
\.

```

Creating a table from OO Base consists of defining the table characteristics in Base, highlighting the data to import in Calc, then pasting the data into the table on Base.  Pretty cool.

---

### Post by RH9R on 2012-06-27
Sensei, Thank you! Getting the server up and functional has always been the hard part. The link to the tutuorial is very much appreciated. If I can get the server side licked, that'll be the lion's share. 'Very much appreciate your kind help.

---

### Post by RH9R on 2012-06-30
Sensei, I followed the path, and indeed have a db in place. 
 
I have much to learn about the server side - like where the application lives, how to start/stop, where the db's & tables physically live. I'm plodding through the documentation. 
 
'Wanted to let you know your kind help worked like a charm. 
 
Many Thanks!

---

