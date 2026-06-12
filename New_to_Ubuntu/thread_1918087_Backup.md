---
title: "Backup"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by reactedsean on 2012-01-31
Hello,

Is there a way i can backup both MYSQL databases and a website into one compressed folder. I don't want it to do anything else no FTP as i will copy it off once a week.

I know i can have a script and a cron job that runs but not sure what the script should be for this?

---

### Post by aeiah on 2012-01-31
what you require is a 2 stage process:

use mysqldump to dump the database to a file
add this dump and the contents of /var/www/ to an archive

so you need to find out what the syntax of the mysqldump will be and the syntax of a .tar.gz archiving operating will be.

---

