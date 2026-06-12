---
title: "How to get started with mysql and java with jdbc?"
date: 2005-11-20
forum: Programming Talk
---

### Post by veraction on 2005-11-20
So, it there a script/how to anyplace that will tell me how to set things up? I basically just want to be able to connect to my mySQL db using jdbc. I tried some things, but always get exceptions when trying to connect.

I've tried searching, but so many threads on complicated/obscure issues.... I just want basic functionality

thanks

---

### Post by veraction on 2005-11-21
Well, I got a step further by copying the mysql connector.jar file to the jre/lib/ext directory.

But now I cannot connect to the db using the user name I created using a java program: ```
$ java Connect
caught SQLException: Access denied for user: 'java@localhost.localdomain' (Using password: YES)
```

I am able to connect to the database using that username with mysql command. And it should have privleges fro @'%' (any host), @localhost, @127.0.0.1, @localhost.localdomain..

[edit] also cannot connect as root..

---

### Post by veraction on 2005-11-21
OK, seems like I got it to work by:

[LIST=1]
[*]Deleting the user I was trying to connect with
[*]Recreating that user
[*]Adding a host for that user of % (for anyplace)
[*]Removing the localhost host (so now only has 'one host' of %)
[/LIST]

So, I suppose that the reason it didn't work befroe was that it had multiple hosts allowed for this user, i.e. localhost, localhost.localdomain, %, 127.0.0.1 and they conflicted with each other or something

---

