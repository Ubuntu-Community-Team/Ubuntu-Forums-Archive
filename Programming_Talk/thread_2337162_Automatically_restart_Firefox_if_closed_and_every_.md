---
title: "Automatically restart Firefox if closed and every 10 minute"
date: 2016-09-15
forum: Programming Talk
---

### Post by mariobalotelli on 2016-09-15
Hi, I run this script to restart Firefox when it closed or every 10 minute
I want to run a loop that, if Firefox is closed or every 10 minute, it will automatically re-open.


```

#!/bin/bash

while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox
fi
sleep 5
done
```

This code work good if firefox is close, but every 10 minute firefox will restart i don't know how i ca edit the code for work perfect?

Help me.

---

### Post by howefield on 2016-09-15
Thread moved to the "*Programming Talk*" forum for a better fit.

---

### Post by mariobalotelli on 2016-09-15
thank you @howefield

---

### Post by Rocket2DMn on 2016-09-15
You need to fork the process to the background for the other lines in the script (like the sleep call) to run while firefox is still running.
```

/usr/bin/firefox

```
becomes
```

/usr/bin/firefox &

```

I'm not entirely clear on what exactly you want.  I see that you want to restart firefox if it's closed, which your script will do.  But did you want to kill and restart it every 10 minutes as well?  What if somebody is actively using it when the 10 minutes expires?

---

### Post by mariobalotelli on 2016-09-16
Thank you.
My script work well, but when server restart it not auto run, 
how i can auto run script [COLOR=#545454][FONT=arial]after startup[/FONT][/COLOR]?

Hi @Rocket2DMn

```

#!/bin/bash

while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox $ [COLOR=#ff0000]sleep 600
killall firefox[/COLOR]
fi
sleep 5
done
```

I try add other red line like above, and it work.

Now,
Because my server offen restart, so[COLOR=#ff0000] i want this script auto run when server startup.[/COLOR]

I try use crontab but it now work.
My file is run.sh (/root/run.sh)
And i use cron is :
```
@reboot /root/run.sh 
```
[COLOR=#DD4814]**Rocket2DMn**[/COLOR][COLOR=#DD4814]**Rocket2DMn**[/COLOR][COLOR=#DD4814]**Rocket2DMn**[/COLOR]

when killall firefox i have 2 value, 
1/ killall successful => script work ok
2/ no process found => no kill => script not work. how i can fix this?

Now my code is, i swap fi and sleep 5
```

#!/bin/bash

while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox $ [COLOR=#ff0000]sleep 600
killall firefox[/COLOR]
sleep 5
fi
done
```

---

### Post by Rocket2DMn on 2016-09-16
You don't want a $ symbol, you want a & symbol to fork firefox to the background.

As for starting your scipt when you boot the system, I think you probably need to create a systemd service for it, but I'm not sure how to do that.  This is a different problem that you should start a new thread for.  Then somebody with more expertise in that can help you.

---

### Post by mariobalotelli on 2016-09-16
> **mariobalotelli said:**
> Now my code is, i swap fi and sleep 5
```

#!/bin/bash

while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox $ [COLOR=#ff0000]sleep 600
killall firefox[/COLOR]
sleep 5
fi
done
```

This code not work if firefox close for firefox crash

> **Rocket2DMn said:**
> You don't want a $ symbol, you want a & symbol to fork firefox to the background.

As for starting your scipt when you boot the system, I think you probably need to create a systemd service for it, but I'm not sure how to do that.  This is a different problem that you should start a new thread for.  Then somebody with more expertise in that can help you.
  i used "&".

i am trying use this code

```

#!/bin/bash


while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox
else
sleep 600 & killall firefox
fi
done

```

---

### Post by mariobalotelli on 2016-09-16
I have script like that
run.sh
```

#!/bin/bash


while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox
else
sleep 600 & killall firefox
fi
done
```


it auto start firefox and run 10m, then close and loop.

now i want this script auto run when server startup. Because sometime my server reboot without any reason

I try use crontab but not work
chmod +x run.sh

```

@reboot /root/run.sh

```

Help me.

---

### Post by Rocket2DMn on 2016-09-16
You're changing your code on me.  What you just posted is not logically correct.  It says that firefox will run if it's NOT already running, but you don't fork it to the background and sleep.  It says if firefox IS running, sleep for 10 minutes then kill firefox.
What I think you want is more along the lines of:
```

#!/bin/bash

while true
do
        if [ ! `pgrep firefox` ] ; then
                firefox &
                sleep 600
                killall firefox
        fi
        sleep 5
done

```

This doesn't account for the condition in which firefox is closed manually (or crashes) after it is launched.  In such a case, the script still waits the full 10 minutes before trying to re-launch it.  To support this, you could add an inner loop that checks every few seconds if firefox is still running, for a total of 600 seconds.  If it's not, you could break out of the loop:
```

#!/bin/bash

while true; do
        if [ ! `pgrep firefox` ]; then
                firefox &
                for ((i=0; i<600; i+=5)); do
                        sleep 5
                        if [ ! `pgrep firefox` ]; then
                                break
                        fi
                done
                killall firefox > /dev/null 2>&1
        fi
        sleep 5
done

```

---

### Post by mariobalotelli on 2016-09-16
> **Rocket2DMn said:**
> You're changing your code on me.  What you just posted is not logically correct.  It says that firefox will run if it's NOT already running, but you don't fork it to the background and sleep.  It says if firefox IS running, sleep for 10 minutes then kill firefox.
What I think you want is more along the lines of:
```

#!/bin/bash

while true
do
        if [ ! `pgrep firefox` ] ; then
                firefox &
                sleep 600
                killall firefox
        fi
        sleep 5
done

```

This doesn't account for the condition in which firefox is closed manually (or crashes) after it is launched.  In such a case, the script still waits the full 10 minutes before trying to re-launch it.  To support this, you could add an inner loop that checks every few seconds if firefox is still running, for a total of 600 seconds.  If it's not, you could break out of the loop:
```

#!/bin/bash

while true; do
        if [ ! `pgrep firefox` ]; then
                firefox &
                for ((i=0; i<600; i+=5)); do
                        sleep 5
                        if [ ! `pgrep firefox` ]; then
                                break
                        fi
                done
                killall firefox > /dev/null 2>&1
        fi
        sleep 5
done

```

i need my code ( auto start firefox when it close (crashes or manually), , if running i want it still run for 10 minutes, and auto close.) and loop

it my case, i can use your above code? @Rocket2DMn

sorry my english is bad.

---

### Post by mariobalotelli on 2016-09-16
mean : firefox allways run, and run only 10min, then restart.

---

### Post by ian-weisser on 2016-09-16
You don't want the script to run at startup (poweron).
You want the script to run after a user logs in.

Firefox will promptly abort if a DISPLAY variable isn't assigned...which cannot happen until after the X server starts as part of the login. 
That's why @reboot doesn't work.

See your /home/$USER/.config/autostart directory for other events that occur after login.

---

### Post by mariobalotelli on 2016-09-16
```

#!/bin/bash

while true; do
        if [ ! `pgrep firefox` ]; then
                firefox &
                for ((i=0; i<600; i+=5)); do
                        sleep 5
                        if [ ! `pgrep firefox` ]; then
                                break
                        fi
                done
                killall firefox > /dev/null 2>&1
        fi
        sleep 5
done
```
i try but it not run. bad for loop variable

---

### Post by mariobalotelli on 2016-09-16
hi,
but i don't see /home/$USER/.config/autostart directory in my server

---

### Post by ajgreeny on 2016-09-16
I have merged the two threads about this subject that you have started in the last two days, both of which had replies.
Please do not create duplicate threads about the same problem; it is confusing for all and dilutes community effort.

To see hidden files and folders such as /home/$USER/.config/autostart. Note the folder .config name which starts with a . and is therefore normally hidden.  To list this with the **ls** command you need to use the **-a** option, **ls -a**

---

### Post by mariobalotelli on 2016-09-16
my /root/.config foders only have user-dirs.dirs and user-dirs.locale, i don't see autostart file.
used ls -a

---

### Post by ian-weisser on 2016-09-17
/root does not need an autostart directory. Root has systemd.
Root should NEVER be running a graphical desktop. That is what users do, not root.

Why do you want to run (and kill) Firefox every 10 minutes?
That seems like a tremendous waste of CPU and memory.
Is this some kind of school assignment?

---

### Post by mariobalotelli on 2016-09-17
i open some website in firefox, but sometime the firefox idle, and i want restart firefox auto.

i try cd .config
and ls -a
only see pulse foder.

---

### Post by mariobalotelli on 2016-09-17
Now i use this code again
```

#!/bin/bash

while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox
fi
sleep 5
done
```
and use crontab : */20 * * * * killall firefox.
looking for how to auto run this script when system startup.

---

### Post by ajgreeny on 2016-09-18
I'm confused!
You're not running firefox as root, I hope?

If you are, I very strongly suggest that you close it immediately and not open it as root again as it is incredibly foolish to do so, and your OS's security could be very severely compromised.

---

