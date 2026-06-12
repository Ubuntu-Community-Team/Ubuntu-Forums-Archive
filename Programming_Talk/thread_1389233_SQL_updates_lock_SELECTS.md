---
title: "SQL updates lock SELECTS?"
date: 2010-01-24
forum: Programming Talk
---

### Post by ThomWilhelm on 2010-01-24
Hello all,

I have a cronjob script run from a PHP script on the database server that updates a table every so often, with this code:

$resultAllTeams = mysqli_query($link, "SELECT t.teamNo, t.teamName, m.memberExpire, m.username, t.kitColorArray, m.lastOnline FROM team t LEFT JOIN manager m ON m.teamNo=t.teamNo WHERE t.bot=FALSE"); 
 
while($rowAllTeams = mysqli_fetch_assoc($resultAllTeams)) {[INDENT]     mysqli_query($link, "UPDATE friends SET teamName1='".addslashes($rowAllTeams['teamName'])."', memberExpire1='$rowAllTeams[memberExpire]', kitColorArray1='$rowAllTeams[kitColorArray]', lastOnline1='$rowAllTeams[lastOnline]' WHERE username1='$rowAllTeams[username]'"); 

    mysqli_query($link, "UPDATE friends SET teamName2='".addslashes($rowAllTeams['teamName'])."', memberExpire2='$rowAllTeams[memberExpire]', kitColorArray2='$rowAllTeams[kitColorArray]', lastOnline2='$rowAllTeams[lastOnline]' WHERE username2='$rowAllTeams[username]'");
[/INDENT]}

But then from the application server there is a:

 SELECT COUNT(*) FROM friends WHERE username1='$username' OR username2='$username'

statement in a login script that doesn't seem to be able to run whilst this cronjob is running, which can take 3-4 minutes at a time. I have other cronjobs that run update statements in a similar way with no similar problems, its just this one seems to lock the table from SELECT statements.

There is an index on the table consisting of username1 and username2.

Any ideas?

---

