---
title: "Run script on hibernate"
date: 2014-10-13
forum: Programming Talk
---

### Post by chris137 on 2014-10-13
Hey,
I'm using ubuntu and am trying to run a script on hibernate.
Right now I run a script on startup with @reboot in crontab and a script on shutdown by adding it to /etc/rc0.d/
That shutdown script shall be ran also on hibernate.
How do I do that?
AFAIK there is no runlevel for hibernation.

---

### Post by Toz on 2014-10-13
You can use pm-utils for this. Create a script in /etc/pm/sleep.d using the following template:
```
#!/bin/bash
case $1 in
    hibernate)
        # Pre-hibernate script here
    ;;
    suspend)
        # Pre-suspend script here
    ;;
    thaw)
        # Post-hibernate script here
    ;;
    resume)
        # Post-suspend script here
    ;;
    *) 
        # Catch-all for others (there shouldn't be any)
    ;;
esac

```
...and make the file executable.

---

### Post by chris137 on 2014-10-14
Alright so this theoretically works but the script does not run what this is all about.
I'm calling an URL via curl which works perfectly fine when typing the command inside the shell.
But when I click suspend nothing happens.
I added a 'mkdir works' at the end of the script and this folder is there after that.
Problem could be again that the network is already down when the script is ran.
On startup I just used a loop until the network was available. But how does this work the other way around?
I need to run my script before the network is shut down.

---

### Post by Toz on 2014-10-14
> **chris137 said:**
> I need to run my script before the network is shut down.
The files in that directory and the parent /usr/lib/pm-utils/sleep.d are run in alphabetical order. During the sleep/hibernate phase, they are run in ascending order (000xxx to 99xxx) and in the resume/thaw phase in descending order (99xxx to 000xxx). To see this in action, have a look at your /var/log/pm-suspend.log file.

55NetworkManager seems to be the script that disables/enables to the network, so rename the file to be preceeded with a number lower than 55. If you want it to run first before anything else (which might be a good idea), try renaming it to start with 0000 (four zeros).

---

### Post by chris137 on 2014-10-14
Thanks!
Renaming the file to 000... worked!
I did name it so it would be the first in that particular folder but did not know there was another one.

---

