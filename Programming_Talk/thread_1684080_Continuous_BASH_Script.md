---
title: "Continuous BASH Script"
date: 2011-02-08
forum: Programming Talk
---

### Post by zkriesse on 2011-02-08
Hello, was wondering if this is possible. I have a BASH Script 
```

#!/bin/bash
cd /var/www/JoeTest || { echo "dir doesn't exist" >&2; exit 1; }
while sleep 5; do if ! cmp filea fileb; then cat filea > fileb; done
php gogo.php
done

```
Which runs a php script. This php script checks to see if a certain file (File B) does or does not exist. If it does it will update it from the info in File A, and then re-check. If it doesn't exist it will first create File B and then update it from File A's info. Ok, so I have it (The BASH script) starting up at system bootup and then it runs every five seconds checking to see if File B is current with File A. My question is this. Is there a way that I could at any time I chose to stop the BASH Script so I could say, update the code in it? And then start it again? I ask as I don't know how to kill the script and even if that does happen, to start the script I have to use terminal but if you close terminal the script stops as well...so, what do I need to do? Any help is appreciated. BTW, I'm still like, completely new to BASH so please don't overwhelm me with super coder talk just yet. :)

---

### Post by MadCow108 on 2011-02-08
see the man page of all italic words for more details:

you can kill the script with the *kill* pid command
the pid (process id) is a number that can be obtained e.g. with *pgrep* process-name
the process name is the name of the script.

to start it again persistently there are a couple of options:
add a launcher to the desktop, then it will run as long as you are logged

start it in a terminal with *nohup* ./script
*nohup* blocks the hangup signal which gets sent to the process and kills it when the terminal closes.

start *screen* in the terminal and execute it your script there.
you can then detach the *screen* with ctrl+d and close the terminal
later you can reattach the screen with *screen* -r

another approach would be to use a cronjob (*crontab*) which runs the script every 5 seconds and the script itself does not contain a the infinite loop.
then you can update the code and just wait, the next iteration will use the new code.
When using this method you have to take care that multiple script processes can run at the same time when they execute longer than 5 seconds.

instead of killing the process you could also add signal handlers to your script (*trap*) and send signals to it to restart. the system daemons usually use this approach and have extra scripts for restarting (/etc/init.d or with upstart, service)
but this is probably overkill for simple tasks

---

### Post by zkriesse on 2011-02-10
Many thanks MadCow, helped alot...do have one more question though...if I stop/kill the BASH script will the PHP script finish it's process(es) before it dies? Or will it die as soon as the BASH script is killed...

---

### Post by MadCow108 on 2011-02-10
it will be killed too.
you can avoid this by trapping the signal and stopping when its finished:
```

trap "stop=1" SIGINT SIGTERM
stop=0
while [ $stop -eq 0 ];
do
        sleep 5
        echo $stop
done

```

---

### Post by zkriesse on 2011-02-10
And would I put that in the php script? OR the bash?

---

