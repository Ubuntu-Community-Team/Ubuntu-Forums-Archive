---
title: "expect timeout"
date: 2012-12-03
forum: Programming Talk
---

### Post by conradin on 2012-12-03
Hi all, 
I am working on a project that accesses an FTP server. The server times out faster than I would like and I have to keep logging in. Its sort of a nuisance. 

So I want to put a conditional statement in an expect script that reloads the ftp connection when the message: "421 Connection timed out."
appears. 
the problem is that I am in an interactive mode when I also want to have the script wait for the timed out message. 

Heres some code that  fials at the conditional statement:
```


#!/usr/bin/expect

proc connect {} {
spawn ftp
expect ">"
send "open 130.111.46.77\n"
expect ":"
send "User\n"
expect "Password:"
send "SomePassword\n"
expect ":"
}
interact

if {expect "421 Connection timed out."}
{
send "exit\n"
expect "$"
send "connect\n"
}

```
what am I doing wrong?

---

