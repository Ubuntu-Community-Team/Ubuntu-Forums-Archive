---
title: "Crontab fails to start autostart.cron script"
date: 2020-12-04
forum: New to Ubuntu
---

### Post by shadowsaunter on 2020-12-04
I can't get a bash script to start my python program from crontab, not sure what is going wrong:

My crontab setting is:

```

# Crontab file
SHELL=/bin/bash


# start eAndon program at startup
@reboot /home/sammy/projects/project_folder/autostart.cron &

```

and my bash script is:

```

#!/bin/bash
#
# boot delay
#if ! [ "$1" == "now" ]; then
#  sleep 20
#fi


# The current working directory is necessary to find config.json
cd /home/sammy/projects/project_folder


# The next command is sent to background, allowing this bash script to exit
/usr/bin/python3.8 /home/sammy/projects/project_folder/main.py start schedule &> /dev/null &

```

When I manually run the autostart file, with './autostart.cron', it starts without issue, but crontab never starts it on reboot.  What can I do to make this work?

---

### Post by TheFu on 2020-12-04
Are there any environment variables that the scripts need which aren't set in a cron environment?

Which crontab file?  There are at least 4 places for those, with different formats.

---

### Post by shadowsaunter on 2020-12-04
Yes, omg is that it?  I&#8217;m using a database, and I&#8217;m setting the db credentials in .bashrc.  Does .bashrc not get looked at during cron boot?

Thank you for putting me on the right track!

---

### Post by shadowsaunter on 2020-12-06
In response to your 2nd question, what are the 4 locations?  I set crontab for this user with crontab -e, which is visible at /var/spool/cron/crontabs/sammy

---

### Post by shadowsaunter on 2020-12-06
I altered the autostart.cron above so that I am trying to set the environment variable, and I also added a test script to write a log file to see if this file runs:
```

#!/bin/bash
export AUTOSTARTVAR="ZZZZZZZZZZ"

# The current working directory is necessary to find config.json
cd /home/sammy/dev/project_folder

# The next command is sent to background, allowing this bash script to exit
# /usr/bin/python3.8 /home/sammy/dev/project_folder/main.py start schedule &> /dev/null &
/usr/bin/python3.8 /home/sammy/dev/project_folder/test.py

```


test.py only contains the python.org example script for logging:
```

import logging

logging.basicConfig(filename='example.log',level=logging.DEBUG)
logging.debug('This message should go to the log file')



```


1. test.py runs, because I see the example.log appear. So I was wondering if my path to python wasn't right or folder permissions weren't. This tells me that path and permissions for main.py from the previous iteration were set correctly,
2. when I check env, I do NOT see the variable AUTOSTARTVAR="ZZZZZZZZZZ", so something is wrong with how I'm trying to set this in the bash script.


Of course, running 'export AUTOSTARTVAR="ZZZZZZZZZZ"' in the cli works as written. 


Is it even possible to set my env variable in that same script?

---

### Post by Holger_Gehrke on 2020-12-07
Each and every program running has it's own environment. The shell which runs the script autostart.cron has AUTOSTARTVAR and since you exported it any child process of that shell like your python interpreter has it too. Anything not started from that shell won't have the variable.
Try adding
```

import os

logging.debug(os.environ['AUTOSTARTVAR'])

```
to your test.py script to see that the variable got exported as expected. 

And it's not only bash started from crontab that won't read ~/.bashrc; a non-interactive bash (like one executing a script) will not read ~/.bashrc. It might get exported variables set in ~/.bashrc when called from an interactive shell but it will not read ~/.bashrc itself.

Holger

---

