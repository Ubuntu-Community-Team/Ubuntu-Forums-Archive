---
title: "bash : $_ in cronjob is empty"
date: 2012-07-30
forum: Programming Talk
---

### Post by ashalaenko on 2012-07-30
cd some_dir && php some_crone.php || echo "$? $_" | xargs ./some_handler.php
So when I run this code from console I got a correct value for $? and for $_

$? - exit status $_ - Gives the last argument to the previous command. At the shell startup, it gives the absolute filename of the shell script being executed.

But when I put this code to cronjob :

crontab -e
*/1 * * * * cd some_dir && php some_crone.php || echo "$? $_" | xargs ./some_handler.php
I got an empty $_. Please help. I can not understand what a problem?

---

### Post by Lars Noodén on 2012-07-30
You might want to wrap [font=Courier New]cd some_dir && php some_crone.php || echo "$? $_" | xargs ./some_handler.php[/font] inside a script and then call the script from cron.  I sometimes find that is necessary with complex actions.

---

### Post by spjackson on 2012-07-30
> **ashalaenko said:**
> 
But when I put this code to cronjob :

crontab -e
*/1 * * * * cd some_dir && php some_crone.php || echo "$? $_" | xargs ./some_handler.php
I got an empty $_. Please help. I can not understand what a problem?
Change crontab's default shell from /bin/sh to /bin/bash by adding the following line to your crontab.
```

SHELL=/bin/bash

```

---

### Post by ashalaenko on 2012-07-30
Thanks. Created bash script script and it works well. So about
SHELL=/bin/bash - I could not change cron variables - had not permissions

---

