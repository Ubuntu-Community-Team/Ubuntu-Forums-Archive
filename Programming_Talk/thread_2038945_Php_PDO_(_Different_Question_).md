---
title: "Php PDO ( Different Question )"
date: 2012-08-07
forum: Programming Talk
---

### Post by ubunwhat on 2012-08-07
Apologies for the earlier thread.  I was making the problem bigger than it needed to be so I just marked it as solved and decided to try again.  The issue, as I now understand it, is a bit different.  I'm hoping someone can help me.

I have current Php installed.  I have several sites running MySql via mysqli without problem.  However, I need PDO for a current project.  When I open a terminal and run php -i|grep PDO it comes up as enabled.  Great.  However, when I run phpinfo it doesn't show up.  Fine, no worries.  The CLI and the Apache server have different php.ini files.  I just have to make the Apache one reflect what is in the CLI one and I'm good to go.  

Except..... they are identical.  I did a line by line search for "pdo" ( all cases ) and every line with "pdo" is absolutely, character for character, identical between the two .ini files.  Now, I am somewhat confused as to how these can be identical, yet PDO is enabled in CLI but not in Apache.  I'd love to understand that but right now my biggest concern is just getting the bloody thing to work in Apache.  To that end, can someone, anyone, please tell me what to put into the php.ini file that Apache uses to enable PDO?  I've searched for hours and have come up with nothing more than advice to download Php from here or there, etc.  My Php is current and clean.  I just need that one line.  Php.net offers a line, but doesn't tell you when or where to apply it.  Anyone?  Please??

---

### Post by spjackson on 2012-08-07
I don't know if this will help you but I have php PDO working in apache with MySQL on Ubuntu 10.04. I didn't have to do anything special to get it working - just installed the right packages.

Is /etc/php5/apache2/conf.d the same as /etc/php5/cli/conf.d ? Do both contain pdo.ini and pdo_mysql.ini?

phpinfo() through apache shows:
```

Additional .ini files parsed:

  /etc/php5/apache2/conf.d/gd.ini, 
  /etc/php5/apache2/conf.d/mcrypt.ini, 
  /etc/php5/apache2/conf.d/mysql.ini, 
  /etc/php5/apache2/conf.d/mysqli.ini, 
  /etc/php5/apache2/conf.d/pdo.ini, 
  /etc/php5/apache2/conf.d/pdo_mysql.ini

Under the PDO heading:
  PDO drivers: mysql

```

---

### Post by ubunwhat on 2012-08-07
This is insane!  Out of pure frustration I removed and reinstalled Php from Synaptec.  The result?  Exactly the same.  PDO shows enabled in CLI but not in phpinfo.  I have checked and rechecked the .ini files and conf.d directories.  Identical. WTF???

---

### Post by ubunwhat on 2012-08-07
I guess I will mark this as solved although I'm still not sure how.  I eventually gave up trying to figure it out and just copied the cli version of php.ini over to apache2 and it works.  I still have absolutely no idea how this could be as those two files are character for character and line for line identical.  But hey, whatever.

---

