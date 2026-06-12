---
title: "Oracle have to log in as oracle user to access sqlplus"
date: 2010-08-21
forum: Programming Talk
---

### Post by iansane on 2010-08-21
Hi,

I recently installed oracle-xe on my Ubuntu 10.04.

It took me the longest time to figure out how to log in because every how to I found said just do "sqlplus sys as sysdba".

Well, that doesn't work. I noticed after a restart that there is a new oracle user so I tried that and it works. The problem is, when I'm logged in as me and I want to use sqlplus, I have to do "su oracle" before I start.

This is not a big deal at the moment and I'm sure it's good security but what do I do when I want to write a program that uses the db? I mean I already created a new user in the db but that user can only log into sqlplus through the new Ubuntu oracle user account.

I added my account to the dba group but that didn't change anything.

Any suggestions?

Thanks

---

### Post by iansane on 2010-08-23
I just wanted to add that it appears as though there is a crude work around for making oracle work with ubuntu. When it installs it makes the user "oracle" as a custom user and puts a home path in the oracle/xe folder that even has the auto created directories for videos, documents, and pictures.

Now why in the world would I want a pictures and videos folder in the oracle directory? Looks like some of the bs I might do myself to make something work. lol

Anyway, oracles main group is dba so I added myself to the dba group but that doesn't work. Also, I've seen reference to a oinstall group in some articles about installing on linux. I don't have a oinstall group. I was hoping to be able to create a group or do something to make oracle let me log in as LOTUS (me) but it seems that the db will only allow use by "oracle" which I didn't see mentioned anywhere in any of the Ubuntu community documentation or the oracle install guide.

Thanks for any suggestions.

---

### Post by manojankk on 2011-12-03
End of the below article clearly describes about sqlplus connection
[Oracle installation on Ubuntu]("http://sqlandplsql.com/2011/12/installing-oracle-11g-on-ubuntu.html")

---

### Post by iansane on 2011-12-20
> **manojankk said:**
> End of the below article clearly describes about sqlplus connection
[Oracle installation on Ubuntu]("http://sqlandplsql.com/2011/12/installing-oracle-11g-on-ubuntu.html")

Wow old post and I just noticed the email notification while cleaning up old emails.

But thank you very much manojankk !:-)

I see the article also list the creation of all the users and groups before installing oracle. It looks like a well detailed how-to. I'll have to drag out the old pc I was using for Oracle. I kinda got side tracked with learning other things and need to get back into it while I still remember a few things.

---

