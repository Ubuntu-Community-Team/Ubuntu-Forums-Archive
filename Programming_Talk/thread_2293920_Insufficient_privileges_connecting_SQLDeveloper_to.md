---
title: "Insufficient privileges connecting SQLDeveloper to Oracle Database 11g"
date: 2015-09-08
forum: Programming Talk
---

### Post by docevil on 2015-09-08
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I'm newbie at ubuntu OS and i'm a programmer.[/COLOR]


[COLOR=#000000]I have installed Oracle 11g database, which I acces on the ubuntu terminal loggin as "su - oracle" and introducing the commands "sqlplus / as sysdba" and I can login successfully.[/COLOR]


[COLOR=#000000]But when I run my sql developer from the script .sh sqldeveloper and it show the SqlDeveloper IDE, I try to set the connection with:[/COLOR]
[COLOR=#000000]-Description: SysAdminConn[/COLOR]
[COLOR=#000000]-User: sqlplus[/COLOR]
[COLOR=#000000]-Password: "Mypassword"[/COLOR]
[COLOR=#000000]-Port: 1521(Default Port i didnt change it)[/COLOR]
[COLOR=#000000]-SID: XE(Default from Oracle 11g)[/COLOR]
[COLOR=#000000]I get an insufficient privileges connection [/COLOR][COLOR=#000000][COLOR=#000000][FONT=Times New Roman]**ORA-01031: Insufficient privileges error from SQLDEVELOPER**[/FONT][/COLOR][/COLOR]
[COLOR=#000000]Could someone tell me why is producing this problem? I have already tried user permisions on sqldeveloper files and it didn't changed anything... I add my root user to de dba group and the same happens...[/COLOR]
[COLOR=#000000]I dont know what more can I do.[/COLOR]

[COLOR=#000000]Thanks for your attention [/COLOR]:smile:

---

### Post by PaulW2U on 2015-09-08
Duplicate thread - [http://ubuntuforums.org/showthread.php?t=2293918](http://ubuntuforums.org/showthread.php?t=2293918)

Please do not start duplicate threads as they cause confusion and dilute the community's effort to help.

Closed.

---

