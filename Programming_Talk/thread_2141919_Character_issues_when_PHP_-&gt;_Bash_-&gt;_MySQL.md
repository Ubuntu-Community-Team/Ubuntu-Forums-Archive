---
title: "Character issues when PHP -&gt; Bash -&gt; MySQL"
date: 2013-05-04
forum: Programming Talk
---

### Post by Valpskott on 2013-05-04
My website has a php form, which passes info into a bash script via arguments, the bash script then feeds this into a MySQL table.

If I write "å ä ö Å Ä Ö" (it's a Swedish site) into the form, the value in the MySQL table looks all weird. How ever, If I pass it into a log file, the text in the log file looks fine. Further more, if I hard code a variable in bash with "å ä ö Å Ä Ö" and then feed it into MySQL table, all looks fine.

I found that I can convert charset with iconv:
```

result="$(iconv -f ISO-8859 -t UTF-8 $1)"

```

But, can I check/test a variable in bash for what charset it uses?
Or can I force PHP to send/use UTF-8 to begin with?

---

### Post by SeijiSensei on 2013-05-04
My bet is that MySQL is using a Latin character set rather than UTF-8.  Take a look at [this posting](http://stackoverflow.com/questions/3513773/change-mysql-default-character-set-to-utf8-in-my-cnf) on how to change the character set in MySQL.

I'm curious why you pass the input to bash first rather than simply writing the data directly into the database with PHP's native MySQL functions.  Almost any manipulation of the input I can think of is much easier in PHP with its rich array of functions than in bash where you have to use clunkier alternatives like sed and awk.  I occasionally pass commands to Linux with functions like shell_exec(), but they are usually something I can only do at the OS level.  For string manipulation and the like, I find using PHP itself a whole lot easier.  In fact I have written system administration scripts in PHP that run from the command prompt for precisely this reason.

---

### Post by Valpskott on 2013-05-07
Thanks for you suggestion SeijiSensei.

All charvar tables in the database where set to the Swedish UTF-8. And well, after more research I found that the problem only arose when www-data executed the bash-script. If I did it myself from the terminal, everything was just fine.

How ever, the problem is now solved.

Added these lines to the php
```

$locale='sv_SE.UTF-8';
setlocale(LC_ALL,$locale);
putenv('LC_ALL='.$locale);

```

Now, how do I mark this thread as solved?

---

### Post by iweballey on 2013-05-08
Thank you 
Good Information for me

---

