---
title: "tomcat apache..."
date: 2008-06-27
forum: Programming Talk
---

### Post by hockey97 on 2008-06-27
ok, how could I find out what database a person has??

my friend and I want to use tomcat apache,he already has it installed by a guy he knows which also installed a database for him. I want to have the exact same stuff so we can connect to each others to update our databases.

would we just be scanning ports???

---

### Post by CptPicard on 2008-06-27
Uh... ask your friend or make him ask that other guy who installed which one it is? :confused:

---

### Post by jamesstansell on 2008-06-27
> **CptPicard said:**
> Uh... ask your friend or make him ask that other guy who installed which one it is? :confused:

If you can't do that other options are to look at the tomcat config files or log files for information.

Also you could connect VisualVM to the tomcat process to get a lot of information, but probably not as much about the database as the other options would yield you.

Another thing you could try is looking at the running processes to look for a database server.  But see below about embedded databases.  Or, if you know which file(s) the database is storing the data to there are tools to find out which process has the file open.

Finally, port scanning would be iffy, or even useless if the database wasn't listening on a port.  There are several embedded databases available, which would run right in the tomcat process, so wouldn't show up as a separate server, and probably wouldn't have a port open.

---

### Post by CptPicard on 2008-06-27
Interestingly, if a database is so well hidden that you would have to resort to something like port scanning, Tomcat and the rest of the Java platform will also probably abstract it away well enough so that you don't even need to know, perhaps apart from the connection URI format ;)

---

### Post by hockey97 on 2008-06-27
ok thanks. I guess my friend has to start searching lol.

---

