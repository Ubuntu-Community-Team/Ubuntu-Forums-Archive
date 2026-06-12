---
title: "Cron Command Priorities"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by Shivraj_Jain on 2014-05-10
Hello Experts,

I am new to ubuntu. I am trying to run 2 commands rmdis testCron and mkdir testCron

commands are executing perfectly, but when i check log as grep CRON /var/log/syslog

it shows command execution log randomly sometimes mkdir first and sometimes rmdir..

how can I set priority /order of commands to be executed?

Thanks

---

### Post by coldcritter64 on 2014-05-10
> run 2 commands rmdis testCron and mkdir testCron I'm not familiar with the command "rmdis", but assuming it is right I'd stick the 2 commands into 1 simple script, setting the order of run and how they run in the one script. Then have cron run the 1 script.

Can be done a couple of ways; using the boolean operators && for "then execute" (and) or the || for "then execute" (or). 
Meaning both command 1 AND command 2 must succeed with &&, or command 1 OR command 2 must succeed for the script to succeed. Basically using the || will let the second command run even if the first fails. If both commands must succeed use the && operators.

If both command must complete;
```

#!/bin/sh

rmdis testCron && mkdir testCron;

exit 0
```Switch the order of commands in the script to have whichever you want to run 1st.

If the first command is likely or possible to fail and you want the script to complete use ||.
```

#!/bin/sh

rmdis testCron || mkdir testCron;

exit 0
```Save this script in a "bin" folder in your home directory to have it in your users path. _*Set it executable;*_ Right click the script > Properties > Permissions Tab > Tick the box down the bottom (ensure a full "tick" and not a dash or blank box is showing). 

Even if it is in your $PATH (system variable for your user path) use absolute addresses in your crontab (_*iirc*_, cron uses the "sh" interpreter).

eg use for the command in the cron entry '/home/<username>/bin/<scriptname>' _not_ ~/bin/<scriptname> or other system variables etc, sometimes cause cron errors. Replace <username> and <scriptname> as required by your set up.

Good luck.

---

