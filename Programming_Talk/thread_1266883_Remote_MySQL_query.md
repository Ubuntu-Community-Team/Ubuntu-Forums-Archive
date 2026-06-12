---
title: "Remote MySQL query"
date: 2009-09-15
forum: Programming Talk
---

### Post by Nevon on 2009-09-15
Once a day I need to update a plain text file with the result of an SQL query. The MySQL database is on another server, so I need to connect remotely. This should be pretty simple with bash.

```
echo "SELECT pname FROM applications WHERE status = 1" | /usr/bin/mysql -u$USERNAME -p$PASSWORD -h$HOST $DATABASE_NAME > outfile
```

Doing this locally (omitting the -h option) works just fine, but whenever I try to do it remotely I get:

```
ERROR 2005 (HY000): Unknown MySQL server host 'MY.MYSQL.SERVER.com' (1)
```

The server works fine, as all my websites make use of it, and they're OK. Am I doing something wrong, and if so, what?

If you have any other way of doing this via a script that can be run by a cronjob, please let me know. All I need is to get the result of the query in a plain text file with each result on its own line.

---

### Post by januzi on 2009-09-15
That mysql server could work on sockets, it could work on different port or it could allow communication only with local users.
You could use:
wget [http://that_server.com/path/get_data.php](http://that_server.com/path/get_data.php) > outfile

---

### Post by bogdan.veringioiu on 2009-09-15
Hi.

Did you set properly the variables ($HOST, etc) before running the script?
Try to inspect them before running the script:
echo $HOST

Cheers

---

### Post by Nevon on 2009-09-15
The command worked beautifully when I ran it from my web hotel (not the same server as the MySQL server), so I guess there's something that I haven't configured correctly on my own computer.

Anyway, it works, so I'm happy.

---

