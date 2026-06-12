---
title: "Automaticaly delete old files."
date: 2013-09-22
forum: New to Ubuntu
---

### Post by Vagelism_Meintasis on 2013-09-22
Hello to all. 
I would like to make a cron job on my ubuntu machine.
The machine has an account legitimate on WINDOWS 2003 server. I want to search the file server and if it finds a file 6 years old that has not be modified since then to delete it.
So the actual question is how to write the rm command to do this job?
Thank you in advance.

---

### Post by sanderj on 2013-09-22
It sounds like a dangerous thing to me. But if you're sure you want to proceed, use 'find'. See [http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/) for an instruction to delete files older than x days.

HTH

---

### Post by Vagelism_Meintasis on 2013-09-22
> **sanderj said:**
> It sounds like a dangerous thing to me. But if you're sure you want to proceed, use 'find'. See [http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/) for an instruction to delete files older than x days.

HTH

Thank you!

---

