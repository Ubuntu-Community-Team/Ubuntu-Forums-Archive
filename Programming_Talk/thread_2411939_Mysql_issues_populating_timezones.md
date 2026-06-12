---
title: "Mysql issues populating timezones"
date: 2019-02-05
forum: Programming Talk
---

### Post by barroncm on 2019-02-05
[COLOR=#000000]Not sure this is the correct place to post this but,[/COLOR]
[COLOR=#000000]I am having issues with getting mysql to populate timezone files.[/COLOR]

[COLOR=#000000]I have tried everything listed here: [/COLOR][https://dev.mysql.com/doc/refman/5.7...fo-to-sql.html]("https://dev.mysql.com/doc/refman/5.7/en/mysql-tzinfo-to-sql.html")
[COLOR=#000000]however when I input [/COLOR][COLOR=#0077AA]mysql_tzinfo_to_sql[/COLOR][COLOR=#000000][COLOR=#000000] ([/COLOR][/COLOR][I]tz_file tz_name) (obviously inputting the correct files and path)

mysql drops to another line for more input.

Im sure there is something small that I either dont know about or missed in the instructions.

Any help would be great![/I]

---

### Post by spjackson on 2019-02-06
> **barroncm said:**
> [I]mysql drops to another line for more input.
[/I]
It sounds like you are typing mysql_tzinfo_to_sql within mysql. You are supposed to run it from the command line (bash).

---

### Post by slickymaster on 2019-02-06
Closed. Duplicate [here]("https://ubuntuforums.org/showthread.php?t=2411939")

Please don't start duplicate threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

