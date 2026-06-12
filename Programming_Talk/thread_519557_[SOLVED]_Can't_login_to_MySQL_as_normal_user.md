---
title: "[SOLVED] Can't login to MySQL as normal user"
date: 2007-08-07
forum: Programming Talk
---

### Post by RocketRanger on 2007-08-07
Hi

This may be a simple problem but I have yet to find a solution for it. I can't seem to login to the mysql client as a normal user. Here's the steps I've taken so far.

Login to mysql as root and create database tmp.
Assigned access to user like this:
GRANT ALL ON tmp.* TO usr@"%" IDENTIFIED BY "shh";

That didn't work. Next I read about changing ownership of the mysql data folder. I guessed that to be /usr/share/mysql. I shut down mysqld, changed ownership to me and restarted it again as root. Still no luck.

What am I doing wrong? I wouldn't like to run the client as root all the time, so how can i fix this?

---

### Post by Rytmis on 2007-08-07
GRANT ALL on tmp.* TO 'usr'@'localhost' IDENTIFIED BY 'shh';

MySQL considers localhost to fall outside of the wildcard %, so it needs a separate permission.

---

### Post by RocketRanger on 2007-08-07
That did it!
It seems that almost all of these problem have a simple solution which makes it all the more frustrating :)

Thank you for that one!

---

