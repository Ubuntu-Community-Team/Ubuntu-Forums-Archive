---
title: "Remote MySQL query problem"
date: 2007-11-06
forum: Programming Talk
---

### Post by Khao on 2007-11-06
Hey there,
I'm having a lot of difficulties executing a query on my web host from my personal server at home.
I can compile and run a program in C that connects to the local MySQL server on my comp but when I try to connect to the MySQL on my website by changing host, username and password it doesn't work. I was wondering if there's anything special I have to add to the code for it to work or something to do
OR 
if it was easier to just connect to my website with a socket and run a PHP query on my website (with parameter, either GET or POST) and if it's more simple please tell me what's the query I have to send when connected to my website because I already know how to connect, just not whats the header i should send.
Thanks!

---

### Post by kebes on 2007-11-06
> **Khao said:**
> when I try to connect to the MySQL on my website by changing host, username and password it doesn't work.

Do you get some kind of error message?

There are many things that could cause it to "not work", including:
1. The MySQL port on the remote machine is closed (or a firewall or router between you and that machine is blocking the port for security reasons).
2. The remote MySQL instance runs on a non-standard port
3. The MySQL user account you are using doesn't have access to the database you are trying to query.
4. The MySQL user account you are using has access to the database, but only via localhost connections.
5. The connection details are wrong (domain name, password, etc.).
etc.

If you can SSH to the remote machine, you can try establishing an SSH connection and tunnel the MySQL traffic through that connection. This will at least allow you to confirm that MySQL is working on the remote machine (and that the username/password are valid).

If that works you can then check the MySQL settings on the remote machine, and see what permissions have been set for that user...


As I said there are many things that could go wrong so any additional information you have would help figure out where the problem is...

---

### Post by aks44 on 2007-11-06
I had (apparently) the same kind of problem writing a C++ CGI.

On my development comp it worked fine, but on my web host I just had blank pages (and I really mean blank, Content-Length was 0).


It turned out that I didn't have the same version of libmysqlclient.so that my web host had.

What happened is that my CGI couldn't even load since it was linked to libmysqlclient.so.15 (IIRC) while my host provided libmysqlclient.so.14 (which I found out by asking them).

I went to mysql.com, downloaded the debian package for the correct version corresponding to my host configuration (5.0.14) and for "releases" I now link explicitely against libmysql.so.14 instead of the default libmysqlclient.so which is symlinked to version 15.


Not sure it is your case, but since you mentioned C I figured this may be related. Hope this helps.



EDIT: Duh... forget about that, I misread your post. I was speaking about C (or C++) CGIs developed & tested locally, then uploaded to a host.

Looks like your web host doesn't allow remote TCP MySQL connections (firewalled or Unix socket only?).

---

### Post by Khao on 2007-11-06
Omg that's ridiculous.. problem solved I looked at my host's wiki and it said that in order to allow access from outside you have to put in your IP in the "allowable hosts" for that user..

---

