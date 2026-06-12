---
title: "setting variables in crontab based on command output"
date: 2007-02-03
forum: Programming Talk
---

### Post by thoughts on 2007-02-03
I can't figure out how to set a simple date variable in crontab.  Setting static variables works fine, for example:

```
FOO="bar bim baz"
```

But all of the following (some of which work fine in BASH) don't work in crontab:

```

MYDATE=date
MYDATE=`date`
MYDATE=$(date)

```

They cause MYDATE to contain the literal text that appears on the RHS, including backticks, dollar-sign and parentheses, etc.

So it appears to be a problem with command execution or redirection, but I haven't been able to figure it out.  It's not a PATH issue though; using "/bin/date" in place of just "date" makes no difference.

Any ideas?

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by WW on 2007-02-03
Could you give the complete crontab line that you are trying to use?

---

### Post by thoughts on 2007-02-03
Well, that *is* the entire line that's not working.  Here it is with another line that attempts to use the variable:

```

MYDATE=`date`
* * * * * /usr/bin/touch /tmp/testfile-$MYDATE

```

The second line works properly; it creates the file as it should.  But the MYDATE variable doesn't contain what you'd expect, so the file created is called /tmp/testfile-`date`.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by WW on 2007-02-03
OK, I see.  As you have found, the definition of variables in the crontab file is not as flexible as it is in, say, bash.  Check out this man page: [http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5](http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5). In particular, when talking about assignments such as "name=value", that man page says "The value string is not parsed for environmental substitutions, thus lines like ```
PATH = $HOME/bin:$PATH
```will not work as you might expect."

You could make a bash script that does what you want, and give the name of the script to crontab.

---

### Post by thoughts on 2007-02-03
Yeah, I've discovered that, but since the manual doesn't mention anything about capturing command output into variables, I've been holding out hope that there may be a chance.  It's looking pretty grim though, and using a separate BASH script to actually do the work (as you mentioned) is the method I'm using as a workaround.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by kitsi80 on 2008-02-14
I have found a solution to this after struggling with the problem this morning to name a mysql backup file each day. I ran this at 12:20 today and my file was named db_backup_2008-02-14-12-20.sql

The cron line is:/usr/bin/mysqldump -uUSERNAME -pPASSWORD DATABASE > FILEPATH/db_backup_$(date +\%Y-\%m-\%d-\%H-\%M).sql

You can view more date options by using man date

---

### Post by njparton on 2008-02-14
Why not put it in a bash scipt, make it executable and then call that from crontab?

I do this to automate daily backups etc using rsync.

Added advantage is that when you do a reinstall or upgrade, you can leave the script in your home directory and just point crontab to it again. No need to reconstruct the commands etc.

---

### Post by Zwack on 2008-02-14
Strictly speaking the crontab file is not a shell, it allows you to define some variables, but if you want the power of a shell then it's not in cron. Your second attempt works because it does actually pass the whole command part to the shell.  You might be able to set "MYDATE in the shell line, but not dynamically on a different line.

Z.

---

