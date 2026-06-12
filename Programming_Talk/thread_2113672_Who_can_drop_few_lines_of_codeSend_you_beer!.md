---
title: "Who can drop few lines of code?Send you beer!"
date: 2013-02-02
forum: Programming Talk
---

### Post by mcurran on 2013-02-02
Recently there have been issues with my xidle returning the idle time, along with a trailing space and the abbreviation of "ms" for milliseconds.  This would not allow the original idlerain.py script to function, because it was passing an invalid string to float.  I have corrected the python script and it is pasted below.  This works for me, max_idle set at 600000 (milliseconds) for 10 minutes.  Remember you need satisfy the xdotool dependency for this script to work also.  Not sure if I'm using the wrong xidle, but this is for anyone who is receiving the following error, or similar:

```
Traceback (most recent call last):
  File "./idlerain.py", line 16, in <module>
    idle=get_idle_time()
  File "./idlerain.py", line 8, in get_idle_time
    return float(proc.communicate()[0])
ValueError: invalid literal for float(): 578 ms



MODIFIED/FIXED idlerain.py

##########################################################################
##########################################################################

#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT,call
import os
import time

def get_idle_time():
    proc=Popen('xidle', shell=True, stdout=PIPE, )
    idlstr = proc.communicate()[0]
    return float(idlstr.split()[0])

is_raining=False
sleep_seconds=1
max_idle=600000
last_idle=0
rain_start_time=time.time()
while True:
    idle=get_idle_time()
    if is_raining:
        duration=time.time()-rain_start_time        
        if(is_raining and duration>1.5*sleep_seconds and
          idle<last_idle):
            is_raining=False
            os.system('xdotool key shift+F9')        
    else:
        if (last_idle<max_idle and max_idle<=idle):
            is_raining=True
            rain_start_time=time.time()
            os.system('xdotool key shift+F9')
    last_idle=idle
    time.sleep(sleep_seconds)  

##########################################################################
```

---

### Post by lisati on 2013-02-08
Moved from [http://ubuntuforums.org/showthread.php?t=1246897](http://ubuntuforums.org/showthread.php?t=1246897) to its own thread: a lot can change in the space of two years....

---

