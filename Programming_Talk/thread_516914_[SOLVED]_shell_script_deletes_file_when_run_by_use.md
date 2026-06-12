---
title: "[SOLVED] shell script deletes file when run by user, won't when run by cron"
date: 2007-08-03
forum: Programming Talk
---

### Post by punky on 2007-08-03
Basically I have written a shell script, which generates a file. At the beginning of the script I want to remove the last file created by the script, so I use the rm command.

now, when I run the script like ./script.sh the file is deleted. When the script is run by cron, the file isn't. The script still works though.

Anyone know what's going on? I can't see the difference between me running it and cron. I have tried running it via my user and root in cron, but it made no difference.

The only thing it could be, is that when i try and delete the files manually, it comes up with "rm: remove write-protected regular empty file <filename>", which I override with the -f switch in the script, which works (well, when I run it myself)

Many thanx in advance. :)

---

### Post by HermanAB on 2007-08-03
This common confusion is caused by the fact that cron runs with a very limited environment (for security reasons).  So, if you wish to call a program from a cron script, be sure to specify the full search path to the program.

'Hope that helps!

Herman

---

### Post by kpatz on 2007-08-03
In addition to specifying the path to the rm utility, make sure to specify the full path to the file you're trying to delete.  A script running from cron isn't going to have a $HOME, for example.

So, instead of:
```
rm -f myfile
```use```
/bin/rm -f /path/to/myfile
```

Also, if you're using /tmp, or another directory with the sticky bit set, only the user that created the file can delete it, though running as root would get around that.

---

### Post by punky on 2007-08-03
Cheers for that mate. Specifying the absolute path to the files to be deleted sorted it :)

Seems easy now its mentioned. Thankfully as you said its a common confusion makes me seem less thick :)

---

