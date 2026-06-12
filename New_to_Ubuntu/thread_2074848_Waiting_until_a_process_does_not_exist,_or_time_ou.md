---
title: "Waiting until a process does not exist, or time out (I failed at it)"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by Dabo Ross on 2012-10-22
Hello, I have been doing some BASH scripting, or, well, failing at it.
I am trying to make a Shell Script that Tells this process to stop, then waits until either the process has stopped, or until 1 minute has passed. After that it restarts it.

I can tell the process to stop, and restart it fine. The only part I am having trouble with is when I am trying to wait until either the process has stopped or 1 minute has passed.

This is the only java process that runs. (it is running in a screen)

Before this code in the script, I am using a command in the script through screen that tells the java process to save everything, and shut down. That saving and shutting down usually takes 30 seconds, and I want to get the new process up as soon as I can. Why I also have the 1 minute time out is that if, for some reason, the process is frozen, It will kill the process as well, instead of continuing to wait forever.

Here is my code for doing it:
```

IS=0
TIMEOUTDATE=$(date +1%Y%j%H%M%S)
until [IS>1]; do
PIDS=`ps cax | grep java | grep -o '^[ ]*[0-9]*'`
if [ -z "$PIDS" ]; then
  if [ $(date +1%Y%j%H%M%S)>$(($TIMEOUTDATE+100)) ];
  then
    echo "Timeout, Killing"
    touch /home/newlanders/logs/$(date +%Y-%m-%d).log
    echo $(date +%Y/%m/%d) $(date +%H:%M) Timeout, killing >> /home/newlanders/logs/$(date +%Y-%m-%d).log
    killall -v screen >> /home/newlanders/logs/$(date +%Y-%m-%d).log
    killall -v java >> /home/newlanders/logs/$(date +%Y-%m-%d).log
    screen -wipe
    exit 1
  else
    echo "Still Running"
    touch /home/newlanders/logs/$(date +%Y-%m-%d).log
    echo $(date +%Y/%m/%d) $(date +%H:%M) Still running >> /home/newlanders/logs/$(date +%Y-%m-%d).log
  fi
  exit 1
else
  IS=2
  echo MCServer Has Stopped. From $TIMEOUTDATE to $(date +1%Y%j%H%M%S)
  touch /home/newlanders/logs/$(date +%Y-%m-%d).log
  echo $(date +%Y/%m/%d) $(date +%H:%M) MCServer has stopped. from $TIMEOUTDATE to $(date +1%Y%j%H%M%S) >> /home/newlanders/logs/$(date +%Y-%m-%d).log
fi
sleep 1
done
killall -v screen >> /home/newlanders/logs/$(date +%Y-%m-%d).log
killall -v java >> /home/newlanders/logs/$(date +%Y-%m-%d).log
screen -wipe

```

I use log the outputs, and also show them to the person running the program, to see if it has worked/is working.

I kill all of them afterwords just to be safe.

I am trying to make a loop until the IS variable is more than one, which it shouldn't be until the process has stopped. Then I use If checks to see if it is running, or if it is stopped, or if it has timed out.
I am not sure why this isn't working, though I don't really know bash, and I pretty much cobbled this script together out of many different things on the web.

If you can see any errors, or why It isn't working, Please Respond.

I know this isn't that basic, but I am relativity new to ubuntu, and where should things like this go?

---

### Post by spjackson on 2012-10-22
Some issues...

Add a line at the start your script:
```

#!/bin/bash

```
The "until" line should be
```

until [ $IS -gt 1 ]; do

```
Your test for processes is the wrong way round: if there are no processes then you issue a kill. You need the "not" operator which is "!".
```

if [ ! -z "$PIDS" ]; then

```
Finally, I'm not too sure about this one:
```

  if [ $(date +1%Y%j%H%M%S)>$(($TIMEOUTDATE+100)) ];

```
I think it should be ok if you just change ">" to " -gt ".

I haven't tested it in full with all these corrections. Please let us know if it works.

---

### Post by Dabo Ross on 2012-10-22
> **spjackson said:**
> Some issues...

Add a line at the start your script:
```

#!/bin/bash

```
The "until" line should be
```

until [ $IS -gt 1 ]; do

```
Your test for processes is the wrong way round: if there are no processes then you issue a kill. You need the "not" operator which is "!".
```

if [ ! -z "$PIDS" ]; then

```
Finally, I'm not too sure about this one:
```

  if [ $(date +1%Y%j%H%M%S)>$(($TIMEOUTDATE+100)) ];

```
I think it should be ok if you just change ">" to " -gt ".

I haven't tested it in full with all these corrections. Please let us know if it works.

Ok, I will try that, Thank you. The
```

  if [ $(date +1%Y%j%H%M%S) > $(($TIMEOUTDATE+100)) ];

```
Is to check if 1 minute has passed, I will change to -gt.
I have edited it And now it works, Thanks!

I now have the script completely functioning, Here it is for anyone to reference:
```

IS=0
TIMEOUTDATE=$(date +1%Y%j%H%M%S)
until [ $IS -gt 1 ];
do
PIDS=`ps cax | grep java | grep -o '^[ ]*[0-9]*'`
if [ ! -z "$PIDS" ];
then
    if [ $(date +1%Y%j%H%M%S) -gt $(($TIMEOUTDATE+100)) ];
    then
        killall java
        exit 1
    fi
    exit 1
else
    IS=2
fi
sleep 1s
done

```

---

### Post by drmrgd on 2012-10-22
You might have a look at this.  It outlines bash test operators, specifying whether it's used for string comparison or integer comparison.  That might clear up some confusion:

[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

---

