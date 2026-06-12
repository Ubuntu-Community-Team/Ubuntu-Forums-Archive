---
title: "sqlite problem"
date: 2008-09-02
forum: Programming Talk
---

### Post by mister_pink on 2008-09-02
Hi,

Hopefully this is just a quick one, and roughly in about the right place. Basically I want to run a couple of sqlite commands from a shell script. At the moment I'm trying:
```

sqlite3 $2 ".separator '\t'; .import $1 tablename";

```
And I get an error: "unknown command or invalid arguments:  "separator". Enter ".help" for help"

It works fine if I do just the separator bit, but then if you import in a separate command the separator is set back to default. So basically all I need to know (I hope) is what I should have in there instead of that ";" which I'm trying to use to separate the commands.

Thanks in advance.

---

### Post by winch on 2008-09-02
sqlite meta commands shouldn't be terminated with a semicolon. I don't know what you should use when separating them when passed as a sql string.

One work around would be to use the -separator option instead of setting it in SQL.

```
$ sqlite3 --help
Usage: sqlite3 [OPTIONS] FILENAME [SQL]
FILENAME is the name of an SQLite database. A new database is created
if the file does not previously exist.
OPTIONS include:
   ...
   -separator 'x'       set output field separator (|)
   ...

```

```

sqlite3 -spearator '\t' $2 ".import $1 tablename"

```

You can also stick the meta commands you want run every time sqlite3 starts in ~/.sqliterc

---

### Post by mister_pink on 2008-09-02
Just tried it and it doesnt seem to work - it seems to litterally just set the output separator not the input one. It complains that my data is only one column as it finds no delimitors. Could just save the file using pipes to delimit it instead I suppose...

---

### Post by forger on 2008-09-02
I think \t is not recognized as a tab character.. You could use any other characters, i.e. ',' (comma)
What are you exactly trying to do? Perhaps:
```
sqlite3 -column file "select * from yourtable;"
```
> 
$ sqlite3 -column ubuntu-packages.db "select package,architecture,task from packages limit 10;"
amarok      amd64         kubuntu-desktop
amarok-xin  amd64         kubuntu-desktop
debootstra  all                          
dia-common  all           edubuntu-deskto
dia-gnome   amd64         edubuntu-deskto
dia-libs    amd64         edubuntu-deskto
dvd+rw-too  amd64         ubuntu-desktop,
gftp-commo  amd64                        
gftp-gtk    amd64                        
git-core    amd64                        

---

### Post by forger on 2008-09-02
You could also use tr to replace the "|" character with tab, example:

```
sqlite3 ubuntu-packages.db "select * from packages where package = 'git-core' limit 1;" | tr '|' '\t'
```
> 10	git-core	devel	dapper	dapper-backports	main	amd64	amd64	optional	7180	Gerrit Pape					1:1.5.4.5-1~dapper1	cogito (<< 0.16rc2-0), git-completion	git-completion	libc6 (>= 2.3.4-1), libcurl3-gnutls (>= 7.15.0-1), libexpat1 (>= 1.95.8), zlib1g (>= 1:1.2.1), perl-modules, liberror-perl, libdigest-sha1-perl, cpio		patch, less, rsync, curl, ssh-client	git-doc, git-arch, git-cvs, git-svn, git-email, git-daemon-run, git-gui, gitk, gitweb	git (<< 4.3.20-11), qgit (<< 1.5.5), git-completion
[...]

---

### Post by mister_pink on 2008-09-03
Thanks, I think I'll just go with using tr to swap them. Basically I'm trying to write a script that will import some legacy data that used to be stored in excel.

---

### Post by forger on 2008-09-04
In that case you could also use sqlite3 -csv (csv means comma separated values) which I think excel supports.
Anyhow, tr is the best suggestion I have

---

