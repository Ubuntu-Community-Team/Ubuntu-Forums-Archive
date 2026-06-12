---
title: "Similar Option"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by rmarti on 2012-01-20
I would like to know if ubuntu has similar option like Windows where you can check the event viewer for application errors...

---

### Post by sanderd17 on 2012-01-20
Linux stores everything to files. The logs are in /var/log

---

### Post by rmarti on 2012-01-20
can I read the log files from the command line?

---

### Post by ajgreeny on 2012-01-20
Yes, easily.

```
less /path/to/filename
``` will show you the content and then allow to to scroll through it as you want either with the scroll mouse or cursor keys, as will the **less **and **cat** commands.

See "**man cat**", "**man less**" or "**man more**" for details.

---

### Post by sanderd17 on 2012-01-20
as you seem not to be afraid of the cli, this might be a good introduction for you: [http://linuxcommand.org](http://linuxcommand.org)

---

### Post by rmarti on 2012-01-21
Thanks a lot for the link!

---

