---
title: "Need help with a sqlite3 script"
date: 2009-01-18
forum: Programming Talk
---

### Post by lovinglinux on 2009-01-18
I need some advice how to improve a script that lists movie trailer files from a specific folder then parse the file names as movie titles into a sqlite statement.

The code is working, but If I have too many files in the folder I could get an sqlite error due to "too long string" in the shell command.

These are some files that need to be listed:

```
Beowulf.avi
Black.August.avi
Harry.Potter.and.the.Order.of.the.Phoenix.avi
Home.Of.The.Brave.avi
In.The.Land.Of.Women.avi
Pirates.of.the.Caribbean.Dead.Mans.Chest.avi
Pirates.of.the.Caribbean.the.Curse.of.the.Black.Pearl.avi
Pirates.Of.The.Caribbean.At.Worlds.End.avi
```

This is the main command that lists these files, filter the results to remove dots and the avi extension, then add the sql statement to each result, so they can be inserted in the database. 

```
INT=$(find $1 -type f \( -name "*.avi" \) | sort | sed "/.*/s/^/insert into intro (title) values ('/g" | sed "s/\/.*\///g"  | sed "/.*/s/$/');/" | sed 's/\.avi//g' | sed 's/\./ /g')
```

where:

**$1** is the path variable parsed by a javascript function

This will produce the following output for the** $INT** variable:

```
insert into intro (title) values ('Beowulf');
insert into intro (title) values ('Black August');
insert into intro (title) values ('Harry Potter and the Order of the Phoenix');
insert into intro (title) values ('Home Of The Brave');
insert into intro (title) values ('In The Land Of Women');
insert into intro (title) values ('Pirates Of The Caribbean At Worlds End');
insert into intro (title) values ('Pirates of the Caribbean Dead Mans Chest');
insert into intro (title) values ('Pirates of the Caribbean the Curse of the Black Pearl');
```

then I run these strings with

```
sqlite3 $fmc "${INT}"
```

where:

**$fmc** is the database path parsed by a javascript function

So I' guess I'm probably missing a better way of doing this instead of using [COLOR="DarkRed"]**sed**[/COLOR] to create the strings, then put them in another sqlite command. Is there a way to use [COLOR="DarkRed"]**find**[/COLOR] directly inside a sql statement?

---

### Post by The Cog on 2009-01-18
If your problem is that INT is too long, how about generating INT as before and then doing something like
for LINE in INT ; do sqlite3 $fmc $LINE ; done
which calls sqlite3 multiple times, once per line.

---

### Post by lovinglinux on 2009-01-18
Thanks. Looks the way to go, but when I do that I get a lot of sql errors like this:

```
SQL error: near "insert": syntax error
SQL error: near "into": syntax error
SQL error: near "intro": syntax error
SQL error: near "(": syntax error
SQL error: near "values": syntax error
```

 I can't find where the problem is.

---

### Post by The Cog on 2009-01-19
Hmm. This might give a clue:
> for LINE in INT ; do echo sqlite3 $fmc $LINE ; done
and in fact, trying that showed up a mistake - I missed the $ in front if INT - try this:
> for LINE in $INT ; do echo sqlite3 $fmc $LINE ; done
then this:
> for LINE in $INT ; do sqlite3 $fmc $LINE ; done

---

### Post by lovinglinux on 2009-01-20
> **The Cog said:**
> Hmm. This might give a clue:

and in fact, trying that showed up a mistake - I missed the $ in front if INT - try this:

then this:

I forgot to mention that I saw the missing $, so the errors I have posted before were showing up using the fixed code. Now I tried the second suggestion, with the "echo" addition, but I still get errors. The errors are different, but they are still there. It seems that each word is considered a command.

---

### Post by lovinglinux on 2009-01-20
It seems that the solution is piping the results through xargs like this:

```
find $1 -type f \( -name "*.avi" \) | sort | sed "/.*/s/^/insert into intro (title) values ('/g" | sed "s/\/.*\///g"  | sed "/.*/s/$/');/" | sed 's/\.avi//g' | sed 's/\./ /g' | xargs -0 sqlite3 $fmc
```

I have found this [here]("http://www.ducea.com/2006/05/24/binrm-annoying-limitation-argument-list-too-long/")

I didn't test it with a really long argument list yet, but it seems to work pretty fine.

Thanks for your help anyway.

---

### Post by lovinglinux on 2009-01-20
Unfortunately, piping into xargs gives the same freaking error "Argument list too long"

---

### Post by lovinglinux on 2009-01-21
Finally found the solution, saving the output to a csv file with pipe separators then importing to sqlite.

```
find $1 -type f \( -name "*.avi" \) | sort | sed 's/\.avi//g' | sed 's/\./ /g' > $TMP/import.csv

sqlite3 $fmc ".import $TMP/import.csv intro"
```

where "intro" is the table name and $fmc is the database path variable

---

