---
title: "How do I install SQlite?"
date: 2006-11-19
forum: Programming Talk
---

### Post by rvickers on 2006-11-19
I intalled php5-sqlite via the Synaptic Package manager. Now what? :confused: 
Thanks

---

### Post by tribaal on 2006-11-19
"sudo apt-get install sqlite" should be what you're looking for...

Hope this helps

- trib'

---

### Post by rvickers on 2006-11-19
Thx tribaal but while you were replying, I downloaded the binary from sqlite.org and it works fine. Now to learn its syntax:-D 
Thx again for the help...

---

### Post by isthisfree on 2012-01-05
> **tribaal said:**
> "sudo apt-get install sqlite" should be what you're looking for...

Hope this helps

- trib'
WARNING - I'm a complete and utter newbie, please play nice :)

When I install sqlite as above, it doesn't download the sqlite3.h and I cannot use it when programming in C.  Up until now I've only ever used the standard libraries and am embarrassingly out of my depth.

When trying to compile I get the following error:

> sqlitetest.m:3:25: fatal error: sqlite3.h: No such file or directory

I try
```
locate sqlite.h
```
and it doesn't exist.  I know I'm doing something silly but I don't know what and it's driving me bonkers.  I can use sqlite3 at the command line, but that's not what I want it for.

---

### Post by entirely_nix on 2012-01-11
To isthisfree
You are probably looking for the development package, 
you need the libsqlite3 and the libsqlite3-dev packages:

To install them:
sudo apt-get install libsqlite3-dev

Then (on my system which is kubuntu 11.10 at least) :
sqlite3.h is at 
/usr/include/sqlite3.h

---

