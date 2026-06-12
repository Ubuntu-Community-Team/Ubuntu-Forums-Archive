---
title: "Need a basic run down with PostgreSQL"
date: 2008-04-16
forum: Programming Talk
---

### Post by Dr Small on 2008-04-16
I just read on Slashdot that MySQL is going closed source, so I want to dive in with PostgreSQL.

So, a few basic questions, for anyone out there that could possibly answer them.

[LIST=1]
[*]Is the syntax the same as MySQL? ... I assume not.
[*] Does it have a control panel like PhpMyAdmin?
[*] Are there any basic examples for connecting and querying for Php?
[/LIST]

I plan to look through the repositories and see what all packages I would need for my server, to get this thing up and working.

Thanks,
Dr Small

---

### Post by pmasiar on 2008-04-16
1.) Syntax of PostgreSQL is mostly standard SQL - like Oracle and most othere databases. 

But are you sure that MySQL going closed is not just a joke? Sun made Java GPL recently, and closing MySQL would 100% kill it. Buying MySQL is defense move against Oracle, IMHO.

---

### Post by Dr Small on 2008-04-16
Wether it is, or isn't, I would still like te setup PostgreSQL for the fun of it, and to give me something else to learn. By the way, I read the Slashdot entry here:
[http://developers.slashdot.org/article.pl?sid=08/04/16/2337224](http://developers.slashdot.org/article.pl?sid=08/04/16/2337224)

So, I have the following packages installed:
postgresql-8.2
phppgadmin

Now I can access PhpPgAdmin, but have run into a slight problem.
I am trying to login to PhpPgAdmin, and can not login with any credentials... All of this is new ground to me, so I am steadily reading manuals and such, but have still yet to find out a "default" login, or even how to set it up to do so.

Dr Small

---

### Post by themusicwave on 2008-04-16
If you read the article you'll see it's not too dire(I know no one reads them on slashdot) here is the link [http://jcole.us/blog/archives/2008/04/14/just-announced-mysql-to-launch-new-features-only-in-mysql-enterprise/]("http://jcole.us/blog/archives/2008/04/14/just-announced-mysql-to-launch-new-features-only-in-mysql-enterprise/")

Anyways, MySQL has had 2 versions for awhile now.  The community one which is open source and the enterprise one you have to buy licenses to use.  The community one is only available to open source products, so for while now if you wanted to build a commercial closed source application you had to buy a license.

I know this because I looked into using it for a system and found I would have to buy each customer a $500 license to use it since the project was closed source and commercial(GASP! my company chose this)

What they are doing is adding features only to the Enterprise version and not to the community one.  They don't detail what features, and there is nothing to stop the community from implementing them themselves.

So before you go to crazy take a deep breath and wait and see.

I prefer Postgres anyway, I use it at work on the above mentioned closed source application(GASP!) so I enjoy the BSD license.

As long as you use standard SQL statements and nothing specific to MySQL you should be able to use just about any database.

---

### Post by themusicwave on 2008-04-16
I can;t remember the login, I usually change it at install time. 

Try username postgres with no password.

---

### Post by Dr Small on 2008-04-16
> Login disallowed for security reasons.
Maybe also I should mention, that I am connecting to the postgres server (in PhpPgAdmin) from another computer on the network.

(The postgreSQL server is on my headless server...)

Dr Small

---

### Post by Dr Small on 2008-04-16
Ok, I finally got in.
Had to run:
```
sudo su postgres -c psql template1
postgres=# ALTER USER postgres WITH PASSWORD 'password';

```

Now I can login.
Will have to play with this all again tomorrow, as I have to go to bed now :D

Dr Small

---

