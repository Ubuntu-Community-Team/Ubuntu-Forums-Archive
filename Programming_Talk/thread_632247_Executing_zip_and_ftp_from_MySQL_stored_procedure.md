---
title: "Executing zip and ftp from MySQL stored procedure"
date: 2007-12-05
forum: Programming Talk
---

### Post by acutshall on 2007-12-05
I'm new to MySQL and Ubuntu, so I need some direction since I'm more familiar with Microsoft SQL Server.

I don't know how to execute shell commands within a stored procedure.  I need to create a stored procedure that will export data to a CSV file, zip the file and then ftp it to an address and account which are stored within a table in MySQL.  Any help?

---

### Post by CptPicard on 2007-12-05
Sounds like something you'd be better off doing with some external programming language that calls MySQL using a client library...

---

### Post by acutshall on 2007-12-05
Maybe a little of the situation would help.  The server hosting MySQL will be connected to by multiple clients running a Windows app (I know, I know!!).  Anyway, I wanted to have a client execute a stored procedure that would extract data to a file, zip the file, then send it via ftp to an address and account that's stored in MySQL.

If the stored procedure can't kick off the zip and ftp, then perhaps a script that could be set on a timer to execute periodically?  It would zip all files found in a specific directory then ftp it to the appropriate location/account.

Any suggestions?  Remember that I'm a newbie to Ubuntu/Linux.

Aaron

---

### Post by aks44 on 2007-12-05
Just wondering... I guess there are good reasons for you to push the data to a FTP, rather than pull it directly from the MySQL server whenever it is needed?

Why not just write some server-side script that will take care of that?

ie.

- call a script through HTTP instead of using FTP
- check if the data is properly cached, regenerate the cache if needed
- send the cache contents as an attachment (passthrough)


The key here being: you must download through HTTP to be able to trigger the server-side script (eg. PHP, Perl, ...).


Maybe you have specific requirements you didn't talk about, but from what you said that's how I'd do it.

---

### Post by acutshall on 2007-12-06
I guess I wasn't clear enough on the requirements.  I'm looking at two possible scripts that would be scheduled as follows:
1. Each evening, run a MySQL job that would export data to a flat file using a naming scheme that's dictated by the receiver.
2. Each Friday evening, run a script that will take the flat files generated earlier and create a zip file then send the zip file to the receiver via FTP.

Does that help?  I installed gnome-scheduler and it appears to be able to handle the scheduling part.  I know how to create the query to generate the file, but I know nothing about writing scripts that would execute a MySQL stored procedure or to perform the zip and FTP.

---

### Post by aks44 on 2007-12-06
I'm not a shell expert, but I guess this could quite easily be done using a few bash scripts and scheduling them with cron.

mysql, gzip and ftp should do the work.

---

