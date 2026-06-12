---
title: "shell script won't run in cron.hourly"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by jrs2 on 2014-02-06
OK, my script runs fine when I do it from terminal, however, a program/executable located in /usr/src/ that is named 'tc' does NOT run when the script is run via cron.hourly. I have a feeling that this has to do with the PATH at the top of my shell script. Can anyone tell me what that path should include to get this executable to run via cron.hourly?

---

### Post by papibe on 2014-02-06
Hi jrs2.

It could be a problem with paths, permissions, environment, etc. I believe we can offer more ideas if we have more details.

Could you post the actual script and the file you modified so it could run hourly?

Regards.

---

### Post by jrs2 on 2014-02-06
```
#!/usr/bin/env bash


SHELL=/bin/sh 
PATH=/usr/src:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


log=/home/rice/Utilities/eth1_monitor.log


check_eth1=$(ifconfig eth1 | grep 'inet addr:')


if [[ -n $check_eth1  ]]
then
    echo "eth1 is up on $(date)" >>"$log"
    exit
else
    echo "eth1 is down, restarting on $(date)" >>"$log" 
   	sudo ifdown eth1 
	echo "eth1 down"
	sleep 2 
	sudo killall tc
	echo "tc stopped" >>"$log"
	sleep 2 
	sudo ifup eth1 
	echo "eth1 up" >>"$log"
	sleep 5 
	echo "waiting" >>"$log"
	sudo /usr/src/tc
	echo "started app on $(date)" >>"$log"
fi
```

---

### Post by jrs2 on 2014-02-06
It's basically an eth1 watchdog script that I want to run every hour, and if eth1 is up, do nothing....if eth1 is down, I want it to make sure eth1 is in fact down, stop my tc app, bring eth1 back up, and then restart the tc app. All works great from terminal. But when I put the script in the cron.hourly folder, it runs, but the tc app never reopens.

---

### Post by papibe on 2014-02-07
Thanks.

**sudo** is an interactive command. It does not work well on a unattended scripts.

I would remove the sudo, and I'd make sure the script is run as root. I'm not sure how are you calling this script from crontab, but an easy way to create a crontab for root is like this:
```
sudo crontab -e
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by jrs2 on 2014-02-07
Remove the sudo from the '[COLOR=#000000][FONT=Ubuntu Mono]sudo /usr/src/tc' line?

I have just placed the script that I made in the cron.hourly folder. It should run as root, correct?[/FONT][/COLOR]

---

### Post by jrs2 on 2014-02-07
Anybody else have any ideas? I know the script is getting to the line that should restart the tc app....because the log file shows '[COLOR=#000000][FONT=Ubuntu Mono]started app on $(date)"[/FONT][/COLOR]' in it everytime it runs. But the app never starts. This is incredibly frustrating. The script runs fine manually....but I need to automate it.

---

### Post by papibe on 2014-02-07
> **jrs2 said:**
> Remove the sudo from the sudo /usr/src/tc' line?
Remove all sudo preceding your commands (you have 4 of them).

Make sure your script is executable:
```
sudo chmod a+x /etc/cron.hourly/yourscript
```
Since you want to run bash, I would also remove this line
```
SHELL=/bin/sh 
```
If 'tc' does not to the background as a service, you may need a '&' at the end:
```
/usr/src/tc &
```
I would also make sure that 'cron' running. You can check by running:
```
sudo service cron status
```
Finally check if your script is being recognize as valid by run-parts (which adds restrictions even how the script is named):
```
run-parts --test /etc/cron.hourly
```
Let us know how it goes.
Regards.

---

### Post by jrs2 on 2014-02-07
Removed all 4 sudo from script.

Removed SHELL=/bin/sh

Added '&' to end of /usr/src/tc line in script.

When I run sudo service cron status: I see : cron start/running, process 1007.

When I do run-parts --test /etc/cron.hourly: I see: /etc/cron.hour/eth1monitor.

Setup another test by taking eth1 down, allowing the script to run at it's specified minute via the cron.hourly settings, same result. It takes the app down, restarts eth1, but does not bring the app back up. Prints in the log: [COLOR=#000000][FONT=Ubuntu Mono]started app on (date, time)[/FONT][/COLOR]

---

### Post by papibe on 2014-02-07
So the script is running, and it just failing on bring back tc.

what kind of service is tc?

Regards.

---

### Post by jrs2 on 2014-02-07
When I go to properties, it says it's type is: executable (application/x-executable)

---

### Post by papibe on 2014-02-08
Thanks, but what it does? Does it need to be run as root?

Try running it like this so you can check if it gives any error message:
```
/usr/src/tc &> /path/to/tc.log &
```
where '/path/to/tc.log' is a absolute path of a log file you can later check.

Let us know if that helps.
Regards.

---

### Post by jrs2 on 2014-02-08
tc app runs fine using above code, with no errors in the log file

---

### Post by papibe on 2014-02-08
Just to be sure, I meant to run it like that on the script.

Does it give any error?

Regards.

---

### Post by jrs2 on 2014-02-08
Sorry, just ran that from terminal. When I run it in the script using cron, this is the text in the log file:

(tc:6852): Gtk-WARNING **: cannot open display:

---

### Post by papibe on 2014-02-08
I imagine tc is a graphic application?

The cron environment is very limited and it does not define the DISPLAY variable, which it is needed to launch GUI apps.

Try this replacing the line that launch tc which this one:
```
env DISPLAY=:0  /usr/src/tc  &>  /path/to/tc.log  &
```
Let us know how it goes.
Regards.

---

### Post by jrs2 on 2014-02-08
now tc.log says this:

env: DISPLAY: No such file or directory

---

### Post by papibe on 2014-02-08
Then try:
```
DISPLAY=:0  /usr/src/tc  &>  /path/to/tc.log  &
```

---

### Post by jrs2 on 2014-02-08
No protocol specified


(tc:7843): Gtk-WARNING **: cannot open display: :0

---

### Post by papibe on 2014-02-08
Do you have multiple displays? If so, you may need to define DISPLAY=:0.0 for the first monitor, or DISPLAY=:0.1 for the second one.

Also, since the desktop is running as "you" (regular user), you need to authorize other users to use it. Run this on the terminal, and try again:
```
xhosts +
``` 
Regards.

---

### Post by jrs2 on 2014-02-08
No command found when I run xhosts + from terminal.

There are no displays connected to this box. It's running headless. I'm connected to the box using Bomgar.

---

### Post by jrs2 on 2014-02-08
xhost + worked though. The script is working with cron! Thanks so much for your help.

---

