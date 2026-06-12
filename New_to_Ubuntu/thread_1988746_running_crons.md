---
title: "running crons"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by marjenni on 2012-05-28
Hi,
   I have a cron setup to run a script at 9:30 every morning that scp's files from another server onto its machine and processes them.

The SCP happens successfully but the following commands in the script do not seem to execute.

If I run the script manually however, the whole script executes correctly.

What could this be?

many thanks

Mark

---

### Post by codemaniac on 2012-05-28
> # minute (0-59),
# |      hour (0-23),
# |      |       day of the month (1-31),
# |      |       |       month of the year (1-12),
# |      |       |       |       day of the week (0-6 with 0=Sunday).
# |      |       |       |       |       commands 

Above is a cron entry syntax that you may use at the begining of your ctontab . 

Please procide more information about your cron scp entry .

---

### Post by Cheesemill on 2012-05-28
Can you post your script please.

It's usually a path issue. As cron runs with little or no environmental variables set up you usually have to use the full path to all commands and files in the script.

---

### Post by marjenni on 2012-06-07
Yes that fixed it, just had to make sure that I had full paths to everything.
 
Many thanks
 
Mark

---

