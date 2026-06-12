---
title: "MySQL -u root -p database &lt; dumpfile.sql"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by panerabread on 2011-10-19
I would really appreciate any form of help with a importing pickle that I can't seem to shake.  

I recently converted a Microsoft Access database into .sql format using the Bullzip program for Windows OS.  (After first trying to use 'mdb tools', and then a different conversion wizard which produced corrupted data).  Now I'm trying to import the dump.sql file into MySQL from Ubuntu.  Every time I try to use the code 

shell> MySQL -u root -p database < dumpfile.sql 

There shows an error 1064 (42000)in your SQL syntax blah blah blah near '-------------------------------------------------------
CREATE DATABASE "database"' at line 1

To fix this, I open up the dump.sql file and comment out the CREATE DATABASE " " command.  What happens then is same error 1064 (42000)in your SQL syntax blah blah blah near '-------------------------------------------------------
CREATE TABLE at line 1
appears!

So while the script all looks good in the .sql file, I just can't seem to get it into a MySQL database.  At this point I am considering hand-coding every table of the database into MYSQL (this would take days)!

-For a second I thought that the bullzip program was the problem, but the file seems to check out----

Thank you kindly in advance.

---

### Post by gmargo on 2011-10-19
Is the .sql file in DOS format (with CR/LF line endings)?  If so try converting to standard UNIX format (LF line endings).

---

### Post by panerabread on 2011-10-19
Hey, 
Thank you for the response. 
Not knowing what line endings are, I will now spend the next two hours reading the wikipedia entry on newline, trying to figure out which one comprises the data, and then converting the file if necessary.  Working from gedit.

---

### Post by rene8 on 2011-10-19
@panerabread:
If you created the .sql file originally in window, it likely has DOS line-ending format (CR = Carriage Return).

Try as suggested by gmargo; convert it to Unix format. You can try this in a terminal:
```
awk '{ sub("\r$", ""); print }' win_textfile > unix_textfile
```
Then try again to do what you were trying to do originally.

**EDIT:**
I found a mistake in your command syntax: if the first SQL command in your dumpfile is "CREATE DATABASE (...)", then you should not put the name of the database before the "< dumpfile " clause. It then should read:
```
sh> mysql -u root -p < dump.sql
```

Hope it works.

---

