---
title: "Semicolon cannot terminate the statement"
date: 2013-04-15
forum: Programming Talk
---

### Post by Newbie89 on 2013-04-15
[COLOR=#333333][FONT=Verdana]I  have succesfully compile the sqlite-amalgamation-3071300 and extract  the file.After that I compile the sqlite3.c into the SBC TS-5500.When  execute the sqlite command,it show no response with the next line,anyone  can help me solve this problem?

[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]SQLite version 3.7.13 2012-06-11 02:05:22 [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Enter ".help" for instructions [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Enter SQL statements terminated with a ";" [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]sqlite> create table artist (ID INTEGER PRIMARY KEY,Artist_name TEXT); [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]...> insert into artist values(NULL,'hong'); [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]...> select * from artist; [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]...> .quit [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]...>[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by r-senior on 2013-04-15
How strange ... I copied and pasted from your post and it worked OK. This is the standard install of SQLite on Precise (12.04).

```
$ sqlite3 temp.sqlite
SQLite version 3.7.9 2011-11-01 00:52:41
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite>  create table artist (ID INTEGER PRIMARY KEY,Artist_name TEXT); 
sqlite> insert into artist values(NULL,'hong'); 
sqlite>  select * from artist; 
1|hong
sqlite> .quit
```

Long shot: What keyboard layout and character set are you using?

What happens with the standard install version of SQLite?

---

### Post by Newbie89 on 2013-04-15
I'm also stuck...is it the problem of cross-compile?After cross compile the sqlite inside single board computer...problem occur...

---

### Post by Bodsda on 2013-04-15
I'm more surprised that it let you enter a NULL value into a primary key column. But hey-ho

---

### Post by r-senior on 2013-04-15
It looks strange I know, but that's how SQLite deals with auto generated primary keys:

[https://www.sqlite.org/autoinc.html](https://www.sqlite.org/autoinc.html)

EDIT: @OP, sorry for the slight digression. Could you provide more information about what you are trying to do?

---

### Post by Newbie89 on 2013-04-16
Usually the problem won't occur like this right?...I think maybe the method of cross-compile make it no response...Just suspect only...Do you guys know how to cross-compile the sqlite inside the single board computer TS-5500?

---

### Post by syahmicro on 2013-05-10
[COLOR=#333333][FONT=Verdana]SQLite version 3.7.13 2012-06-11 02:05:22 [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Enter ".help" for instructions [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Enter SQL statements terminated with a ";" [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]sqlite> create table tbl1(char ,int ); [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]...> insert into tbl1 values('kenneth,10); [/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]...> [/FONT];[/COLOR]
[COLOR=#333333][FONT=Verdana]...> ;[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]...>[/FONT][/COLOR][COLOR=#333333][FONT=Verdana];

i also got this problem,as u can see from that statement i just [/FONT][/COLOR]
deliberate to dump the comma at [COLOR=#333333][FONT=Verdana]'kenneth.suppose[/FONT][/COLOR]ly when there have missing character such as comma it must be show the syntax error but then when need terminate the statement i could not work.I don't what is the problem because i was tried 2 times installing sqlite on ubuntu 12.04

so from this,i would like to make another coding to fix up this problem by using c programming
but then do you all have ideas to make coding?so we can access with sqlite using this command
gcc -o file file.c -lsqlite3

in sqlite,there are having files which is header file and c files.
sqlite3.c 
shell.c

---

