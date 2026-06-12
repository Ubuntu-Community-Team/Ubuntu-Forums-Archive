---
title: "python remote database connection"
date: 2007-05-05
forum: Programming Talk
---

### Post by braddcadd on 2007-05-05
Hi all, I am learning python and wonder if I can connect to a mySQL database server hosted by my hosting service (bluehost).   The script just hangs with no response.

Disclaimers: 
[LIST]
[*]I'm not sure what a port is, nor how to use it. 
[*]I have a link that will get me phpmyadmin on the bluehost server.  The format of the link is like this: [http://AA.BB.CC.DD:YYYY/3rdparty/phpmyAdmin/index.php](http://AA.BB.CC.DD:YYYY/3rdparty/phpmyAdmin/index.php)
[*]Notice I removed the ip numbers :)
[*]I am on a laptop that is behind a firewall (linksys router).
[*]Bluehost forums say something about being whitelisted.  Not sure what this means either.
[/LIST]
```

import MySQLdb
[B]myDB = MySQLdb.connect(host="AA.BB.CC.DD", port=YYYY, user="**********", passwd="*****************")
[/B]cHandler=myDB.cursor()
cHandler.execute("SHOW DATABASES")
results=cHandler.fetchall()
print "========================="
for items in results:
	print items[0]

```

---

### Post by AdamG on 2007-05-05
You're doing pretty well so far. The problem is most likely that when you connect via phpMyAdmin, the PHP process is on BlueHosts's own servers; when you're connecting via your script, your IP address probably isn't being accepted. You'll need to go into your hosting settings, find the MySQL settings, and just set the accepted hosts to be a wildcard - Variously a %, *, or other charachter. It should be documented there.

---

### Post by steve.horsley on 2007-05-07
Your code looks right to me. But if your ISP has any sense at all, they won't allow just anyone to connect to their database. You will probably have to talk to them and get them to add you to their list of IP addresses that are allowed to talk to their database server (such a list is called a whitelist, as opposed to a blacklist which would list people who are not allowed). This may be doubly difficult if you have a dynamic IP address.

---

