---
title: "[Ubuntu 18.04.2 LTS] script for watching a certain process if running"
date: 2019-07-03
forum: Programming Talk
---

### Post by zhelev81 on 2019-07-03
Hello, 

anybody can help me to create a script for watching a certain process if  running, if not running to start it. My scrip for start looks like this  right now.

```
#!/bin/sh

st_user="MYUSER"

screen -A -m -d -S MYPROCESS \
su - $st_user /home/MYUSER/servers/scripts/MYSCRIPT.sh
```

```
#!/bin/sh

cd /home/MYUSER/servers/MYSCRIPT-folder/
/home/MYUSER/servers/MYSCRIPT-folder/MYSCRIPT.pl
```

i just want to track this process all the time if it is running , if it not then start the screen again automatically.

I hope someone can tell me how

---

### Post by dmnur on 2019-07-03
I guess that in your case the following construct will do:
```
while :; do screen -D -m MYCOMMAND; done
```

The **-D -m** options tell **screen** to not return until the session is terminated.
The session will be terminated when **MYCOMMAND** exits. **screen** will return then, but the infinite **while** loop will start it again.

[HR][/HR]

Let's take a look at this example:
```
while :; do screen -D -m top; echo "screen is gone! Restarting it..." >&2; done
```

We ran that command, now we open another terminal:
```

$ pgrep -xa top  # it's running
24135 top
$ kill 24135  # now let's terminate it

```

At the terminal where we ran the first command, the following is printed:
```
screen is gone! Restarting it...
```

And we see that **top** has been restarted:
```

$ pgrep -xa top  # now with a different PID
24183 top

```

---

### Post by zhelev81 on 2019-07-04
I am not very good at this things ,, and i did not understand i have to create another script with all this lines and run it with cron job or how ? also i did not understand how do you locate the PID because everytime i start my app it is with different PID

---

### Post by dmnur on 2019-07-04
Just edit your start script for it to become a watch script as well:
```

#!/bin/sh

st_user="MYUSER"

while :
do
  screen -A -m -D -S MYPROCESS \
  su - $st_user /home/MYUSER/servers/scripts/MYSCRIPT.sh
done

```

If you really need a separate script, the easiest way to watch if some process is running is to search it by its command line. For example:
```

#!/bin/sh

script_path=/home/MYUSER/servers/scripts/MYSCRIPT.sh

while :
do
  # Check if there is a process that contains the value
  # of the $script_path variable in its command line.
  if ! pgrep -c -f "$script_path" >/dev/null
  then
    # If not, start the script.
    /path/to/your/start/script
  fi
  # Sleep for 5 seconds before checking again.
  sleep 5
done

```

Another option is to edit your main script to write a PID file, and then from another script watch the PID from this file. But that's much more complicated.

---

### Post by zhelev81 on 2019-07-04
so if i understand well if i edit my script like this :

```
#!/bin/sh

st_user="MYUSER"

while :
do
  screen -A -m -D -S MYPROCESS \
  su - $st_user /home/MYUSER/servers/scripts/MYSCRIPT.sh
done
```

it will watch for  MYPROCESS  and once MYPROCESS crashes it will execute again :

```
#!/bin/sh

st_user="MYUSER"

while :
do
  screen -A -m -D -S MYPROCESS \
  su - $st_user /home/MYUSER/servers/scripts/MYSCRIPT.sh
done
```

is that correct ?

---

### Post by zhelev81 on 2019-07-04
it did not work, i tried....

---

