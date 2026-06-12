---
title: "substract days with date in bash"
date: 2010-04-03
forum: Programming Talk
---

### Post by davidtuti on 2010-04-03
Hi,

I would like in a shell-script to substract some days with bash, but doesnt works. For do this I do:

david@maquinon:~/tele$ echo $n
3
david@maquinon:~/tele$ diaBusqueda=`date --date='-$n day'`
date: fecha `«-$n day»' inválida

Althought if I do:
david@maquinon:~/tele$ diaBusqueda=`date --date='-3 day'`
It works.

could you help me please?
Many thanks and sorry for my english!

---

### Post by falconindy on 2010-04-03
Use double quotes rather than single quotes to allow the variable to be substituted.

```
$ n=3
$ date --date "-$n day"
Wed Mar 31 10:14:11 EDT 2010
```

---

### Post by JCM_Pico on 2011-01-12
Hi, is there any way to make this with a different date format like 
$ *date +%d*

---

### Post by sisco311 on 2011-01-12
Yes:
```

n=3
date --date="-$n days" +'%d'

```

---

### Post by fubofo on 2012-05-06
Sorry for opening an old post but I would like an answer to similar question.

I have a script that creates daily backups and names them as DAYNAME.tgz

How can I script it so that it keeps only the last 3 days? I have tried below but cannot work it out..

```
#!/bin/bash

#DELETE ANY OLD BACKUPS IF THEY EXIST
rm -rf /backups/server/full_site/daily/backup_`date -date="-3 day" +'%a'.tgz

tar cvzf /backups/server/full_site/daily/backup_`date +%a`.tgz /home/sites/public_html
```

Also have a similar setup for months - how can I get it to keep only the last, say 3 months?

```
#!/bin/bash
tar cvzf /backups/server/full_site/monthly/backup_`date +%d_%m_%y`.tgz /home/sites/public_html
```

---

### Post by ofnuts on 2012-05-06
> **fubofo said:**
> Sorry for opening an old post but I would like an answer to similar question.

I have a script that creates daily backups and names them as DAYNAME.tgz

How can I script it so that it keeps only the last 3 days? I have tried below but cannot work it out..

```
#!/bin/bash

#DELETE ANY OLD BACKUPS IF THEY EXIST
rm -rf /backups/server/full_site/daily/backup_`date -date="-3 day" +'%a'.tgz

tar cvzf /backups/server/full_site/daily/backup_`date +%a`.tgz /home/sites/public_html
```Also have a similar setup for months - how can I get it to keep only the last, say 3 months?

```
#!/bin/bash
tar cvzf /backups/server/full_site/monthly/backup_`date +%d_%m_%y`.tgz /home/sites/public_html
```
If you consider that the last change date of the backup files will normally be the day they have been created, you can use the ***find*** command with the appropriate parm (-mtime or -ctime) to list files older than N days.

---

### Post by apmcd47 on 2012-05-06
```
find /backups/server/full_site/monthly -name 'backup_*.tgz' -mtime +90 -print0 | xargs -0 rm -f 
```

should delete files that are 90 days old. If you want something more precise you could look at %j format of date:
```
$ echo $(( $(date +%j) - $(date --date=-3months +%j) ))
96

```

Andrew

---

### Post by fubofo on 2012-05-06
Sorry but both of those have me stumped. I'm really noob at shell scripting...and it's late lol

---

