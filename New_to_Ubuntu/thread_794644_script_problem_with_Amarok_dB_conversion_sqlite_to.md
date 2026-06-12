---
title: "script problem with Amarok dB conversion sqlite to mysql"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Littlehawk on 2008-05-14
I found Amarok today, and it really looks like what I am looking for in playlist management. However, I just can't get it to build a mysql database. I have mysql running fine, and I was able to overcome the Amarok coplaints about connecting to mysql. But when it goes through the build or rescan process, it results in no collection playlist being generated.

So I came across this instruction for converting the sqlite collection dtabase to mysql at [http://amarok.kde.org/wiki/MySQL_HowTo#SQLite_-.3E_MySQL]("http://amarok.kde.org/wiki/MySQL_HowTo#SQLite_-.3E_MySQL") and it has this instruction that I can't get to run correctly:

```
cd ~/.kde/share/apps/amarok && \
sqlite3 collection.db .dump | \ 
egrep -vi '^(BEGIN TRANSACTION|COMMIT|CREATE|INSERT INTO "devices")' | \
perl -pe 's/INSERT INTO \"(.*)\" VALUES/INSERT INTO \1 VALUES/' | \
mysql -u root -p amarok

```

I have sqlite3 running okay from the command line and I can execute ```
sqlite3 collection.db .dump
```
all by itself.

However, this multiline piping has me stumped. I just copied the entire five lines into the copy buffer and pasted it all at once into the terminal. It complains like this:
```
jim@ubuntu-7:~/.kde/share/apps/amarok$ cd ~/.kde/share/apps/amarok && \
> sqlite3 collection.db .dump | \ 
**bash:  : command not found**
jim@ubuntu-7:~/.kde/share/apps/amarok$ egrep -vi '^(BEGIN TRANSACTION|COMMIT|CREATE|INSERT INTO "devices")' | \
> perl -pe 's/INSERT INTO \"(.*)\" VALUES/INSERT INTO \1 VALUES/' | \
> mysql -u root -p amarok
Enter password:
```

I stopped at that point. Am I running this set of commands wrong? What is the right way to execute it?

Thanks

---

### Post by mxg01 on 2008-05-15
I wonder if the single space after the \ on the sqlite3 line is causing it. Try removing it and pasting it in again.

---

### Post by mxg01 on 2008-05-15
Yes, it's that space after the \ on the sqlite3 line. I was at work earlier with no Ubuntu but I've just tried it at home and that's the answer. Remove the space and it will work.

---

