---
title: "Cron Deletes my file"
date: 2010-06-08
forum: Programming Talk
---

### Post by Bryce3435 on 2010-06-08
I use the following script to grab performance data and email it to myself. I called this script email.sh . By Itself it runs fine and I get the information. When I run the script through cron it deletes the information in Performtop.txt file and reduces the file size to 0. The result is a email with no content. The script was working previous and I am not sure why it does not work now. Any help would be great.

Email.sh
#!/bin/bash

top -b -n 1 > /sm/tmp/Performtop.txt
cat /sm/tmp/Performtop.txt | uuencode /sm/tmp/Performtop.txt | /usr/sbin/sendmail -f [email]demo@securitymetrics.com[/email] [email]brycem@securitymetrics.com[/email]

Task1.cron

* * * * * /bin/bash -c /sm/tmp/email.sh

---

### Post by Bachstelze on 2010-06-08
First, it is not really recommended to call sendmail directly. COnsider using mail or mutt instead. Second, wy do you use uuencode at all? If it's a text file, you shouldn't need it, just do something like

```
cat /sm/tmp/Performtop.txt | mail brycem@securitymetrics.com
```

Third, you can just mark your script as executable and put this in your crontab:

```
* * * * * /sm/tmp/email.sh
```

---

### Post by gmargo on 2010-06-08
I don't see anything wrong with that code.  The "top -b -n 1" worked for me out of cron.  The uuencode/sendmail stuff is irrelevant and you should comment it out for testing purposes. 

The shell clears the output file and then invokes top - so either top is giving no output or the top command is not found.  Could it be a permission problem?  Are you running under cron as yourself or another user?  Could it be a PATH problem and top is not found?

At the very least, change your crontab line to capture stdout/stderr to try to get a better idea.  You could also try a "set -x".  You don't have 'noclobber' set do you?
```

* * * * * /sm/tmp/email.sh >/tmp/email.stdout 2>/tmp/email.stderr

```

---

