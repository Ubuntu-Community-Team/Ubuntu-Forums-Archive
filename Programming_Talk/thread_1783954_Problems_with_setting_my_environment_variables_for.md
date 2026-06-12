---
title: "Problems with setting my environment variables for JDBC MySQL connector"
date: 2011-06-16
forum: Programming Talk
---

### Post by skytreader on 2011-06-16
Hi all. I'm trying to use the MySQL connector for JDBC but I can't get my code to run---it keeps throwing a ClassNotFoundException for com.mysql.jdbc.Driver .

I put the mysql connector jar in /usr/import/ (I think I made the "import" directory myself as I see that C has it's own "include" directory). To make things easier, I renamed the jar file jdbc-mysql-connector.jar . Then I added the following to my PATH environment variable:

```
/usr/import/jdbc-mysql-connector.jar
```

So printenv gives me:

```
PATH=/home/chad/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/import/jdbc-mysql-connector.jar
```

(I'm aware and have tried doing a wildcard and just specify /usr/import but since there is only one jar concerned and also due to frustration, I specified the jar file itself. In short, /usr/import alone didn't work for my purpose.)

Yet even after that, java still throws a ClassNotFoundException for com.mysql.jdbc.Driver .

And as an assurance that I have the right jar for the (supposedly) right imports, I have already successfully run my code on Windows Vista.

Any suggestions?

---

### Post by r-senior on 2011-06-16
Java doesn't look for Jar files in PATH, it looks in CLASSPATH.

Either modify your CLASSPATH environment variable, or use the -cp option when you run it.

---

