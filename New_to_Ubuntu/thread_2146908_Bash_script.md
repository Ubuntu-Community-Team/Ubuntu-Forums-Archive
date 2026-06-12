---
title: "Bash script"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-05-20
Hi, friends

#!/bin/bash
thetime=`date +%Y-%m-%d--%H:%M:%S`
mv bugs.sql bugs-$thetime.sql

i saved the above script in a file called test.sh, 
problem is; i cannot execute test.sh file in crobjob but i could execute by manually like this;
jug@fpmohan:~/Desktop/mysql$ ./test.sh

When i run manually as ./test.sh in terminal, file bugs.sql moved into bugs-2013-05-20--15:15:27.sql but in cronjob its not executing.

---

### Post by steeldriver on 2013-05-20
When you execute the script in the current directory it presumably finds bugs.sql also in the current directory - to execute from cron you will need to give the full path to the file you want to move and where you want to move it to. If the script is not in cron's PATH you will need to call that by its absolute name as well.

---

### Post by pmohankumar on 2013-05-20
Thanks,

Problem solved.

---

