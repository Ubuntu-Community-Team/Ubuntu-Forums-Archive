---
title: "mySQL for ubuntu?"
date: 2007-09-21
forum: Programming Talk
---

### Post by iangregson on 2007-09-21
Hi there,

I found mySQL for ubuntu ... here [http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=feisty&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=mysql&searchon=names&page=2&number=50](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=feisty&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=mysql&searchon=names&page=2&number=50)

my question is, if anybody can help, what is the difference between client and server..

From what i have been reading at the mySQL site... the Server and Client are both fully working DBs... but i can't figure out which one to download...

Can anyone help?

To be more specific... the machine is not a a dedicated machine but i use it for apache2, tomcat and soon to be mysql for db access..

Any advice really appreciated

thanks

Ian

---

### Post by LaRoza on 2007-09-21
```

sudo aptitude install mysql-server

```

OR

```

sudo tasksel

```
(Select LAMPP)

---

### Post by WakkiTabakki on 2007-09-21
> **iangregson said:**
> 

my question is, if anybody can help, what is the difference between client and server..

From what i have been reading at the mySQL site... the Server and Client are both fully working DBs... but i can't figure out which one to download...


"both are fully working DB:s"
Well, no actually.  The relationship between the client and the server is about the same as between a webserver (sever) and the firefox browser (client).
Without the server, actually hosting the data and "serving" connections, the client has nothing to access. And without at least one client, the server has no one to serve...

A client-server database is an DB-architecture to enable many different applications (even from different physical computers) to access the same data without risking to interfere with eachother...

So if you are going to host data you'll need the server part. If you're only planning to connect to an existing database, you'll need the client part.
If you're planning on doing both, well, you'll need both.

Hope this made it somewhat clearer...
/N

---

