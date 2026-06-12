---
title: "Help regarding SQL"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by abnordude on 2011-10-21
Hi, we just started learning SQL in our school and they use windows o'er there...
They have a software called mySQL or something like that in which we can type queries like create table <tablename>, insert into........etc.
And we'd get a table with the data that we inserted.

I was thinking whether there is any equivalent to that...

PS. I googled it but it showed me how to setup a SQL server...

But I need the one that is used in my school....

PLease help.

---

### Post by TeoBigusGeekus on 2011-10-21
I personally prefer MySQL Query Browser and MySQL Administrator.
They are both in the software centre I think - just do a search for mysql.

---

### Post by abnordude on 2011-10-21
> **TeoBigusGeekus said:**
> I personally prefer MySQL Query Browser and MySQL Administrator.
They are both in the software centre I think - just do a search for mysql.


Yes.....Thanks for the quick reply...

I downloaded the apps...
But when I start them, then I get (Uhh....)..I dunno.....They are asking me about some connections and usernames and passwords......

What do I do?

---

### Post by TeoBigusGeekus on 2011-10-21
Have you installed mysql?

---

### Post by CharlesA on 2011-10-21
I usually just use phpmyadmin, but that's probably cuz I usually run a LAMP stack instead of just an sql server.

It's asking for the login info of the database you are trying to connect to.

---

### Post by abnordude on 2011-10-21
Yes I've installed mysql....

But when I open it.....I'm getting a window that asks me the user name, password, and server hostname etc....

What should I do?

---

### Post by TeoBigusGeekus on 2011-10-21
You should put in the username and password you gave when you installed mysql.
As host, just put localhost.

---

### Post by abnordude on 2011-10-21
> **TeoBigusGeekus said:**
> You should put in the username and password you gave when you installed mysql.
As host, just put localhost.


I tried that......This is the result.....

Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Click the 'Ping' button to see if there is a networking problem.

---

### Post by TeoBigusGeekus on 2011-10-21
Is the port number 3306?

---

### Post by abnordude on 2011-10-21
> **TeoBigusGeekus said:**
> Is the port number 3306?


Yes..
It is....

---

### Post by TeoBigusGeekus on 2011-10-21
Can you give us a screenshot of what you put in the query browser's/administrator's startup screens?

---

### Post by abnordude on 2011-10-21
> **TeoBigusGeekus said:**
> Can you give us a screenshot of what you put in the query browser's/administrator's startup screens?

Here it is......

---

### Post by CharlesA on 2011-10-21
If I remember right, the user should be 'root' and the password was set during install.

---

### Post by TeoBigusGeekus on 2011-10-21
> **CharlesA said:**
> If I remember right, the user should be 'root' and the password was set during install.

^^^ This.

---

### Post by abnordude on 2011-10-21
> **TeoBigusGeekus said:**
> ^^^ This.


nope... i get the same error....

---

### Post by abnordude on 2011-10-21
if it helps, i'm using debian, not ubuntu...

---

### Post by CharlesA on 2011-10-21
> **abnordude said:**
> if it helps, i'm using debian, not ubuntu...
Same install process.

[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

---

### Post by abnordude on 2011-10-22
Finally.......
Fixed it......

Well. I hadnt installed mysql server..
After  i installed it then all was okay........

Thanks everyone for ur help...

---

