---
title: "bash script - launch process, forget it and keep going?"
date: 2008-11-27
forum: Programming Talk
---

### Post by AussieGuy69 on 2008-11-27
Hi

Im writing a script to launch 65 instances of a program using a loop. 

At each iteration I need bash to launch the process as a new process, not wait for the process to finish and keep going.

Ive tried
echo & sudo -u server1 startserver

and it interrupts my script so I cant get more than 1 process launched....

Is there anything that can cause bash to fork off a new process then forget it and keep going? I want to launch 100 processes that will stay running even after the script has finished.

If bash cant do it I might be forced to use C/PHP or some funny combination of C and bash so that it can sudo to all 65 server users and start their servers.

-Aussieguy

---

### Post by geirha on 2008-11-27
```

# Script will execute startserver and wait for it to finish
sudo -u server1 startserver

# The added & will make bash execute startserver, send it to the background, then 
# continue to the next line without waiting for it to finish
sudo -u server1 startserver &

```

---

