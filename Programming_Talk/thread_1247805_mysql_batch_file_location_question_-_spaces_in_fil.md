---
title: "mysql batch file location question - spaces in filenames"
date: 2009-08-23
forum: Programming Talk
---

### Post by japhyr on 2009-08-23
Hello,

I am trying to run a mysql batch file.  If the file is in a path with no spaces, such as
```
/home/me/mysql_work/batch_file.sql
```
I can run the file fine.  If the file is in a path with spaces, such as
```
/home/me/mysql work/batch_file.sql
```
I can not get the file to run.  I keep getting errors:
```
Failed to open file '/home/me/mysql work/batch_file.sql', error: 2
```
I am using mysql from the terminal.  I know in the terminal I can use forward slashes to escape spaces in path names, but this does not seem to work in mysql.

Is there a solution to this other than making sure there are no spaces in any of my folder names for mysql development work?  Is it a good practice, generally, in programming work to not use spaces in file names?

---

### Post by unutbu on 2009-08-23
Hi japhyr, does putting quotes around the name work for you?
This works for me:
```

mysql -u USER -p DATABASE < ~/"test/mysql work/a file with spaces.sql"
```

If not, please post the command you are using.

---

### Post by japhyr on 2009-08-23
That's interesting.  In playing around with your suggestion, I found that
```
mysql> source ~/mysql work/batch_file.sql
```
works.  Also, after that, running
```
mysql> source /home/me/mysql work/batch_file.sql
```
works as well.  I'm not sure what happened earlier.  I don't think it was just a typo, because I tried it a bunch of times over several sessions.  Anyway, thank you for the help.

---

