---
title: "Ubuntu - Script help"
date: 2009-05-14
forum: Programming Talk
---

### Post by PureLoneWolf on 2009-05-14
Hi all

I wonder if anyone can help me.  I am running XBMC on a dual-monitor setup.  I like to have it maximised to full screen on my main monitor and still be able to work in monitor 2.

I found a script for boxee that uses wmctrl to do this and the wmctrl command line works perfectly, but I would like the script to launch xbmc, wait a couple of seconds and then execute the wmctrl command.

This script worked perfectly when I was using boxee, but I got rid of boxee due to performance issues.

Here is the original boxee launch script:
```

#! /bin/bash

STATUS=0
WINCLASS=Boxee.Boxee
DISPLAY=:0.0
SLEEPDELAY=5


/opt/boxee/run-boxee-desktop "$@" & 

while [ $STATUS -eq 0 ]
do
  sleep $SLEEPDELAY
  STATUS=`wmctrl -x -l | grep $WINCLASS | wc -l | awk '{print $1}'`
done

wmctrl -x -r $WINCLASS -b toggle,fullscreen

```

If I run the following command XBMC maximises on the correct screen as I would like:
```

wmctrl -x -r XBMC Media Center.XBMC Media Center -b toggle,fullscreen

```

I tried to modify the boxee script to this
```

#! /bin/bash

STATUS=0
WINCLASS=XBMC Media Center.XBMC Media Center
DISPLAY=:0.0
SLEEPDELAY=5


/usr/bin/xbmc "$@" & 

while [ $STATUS -eq 0 ]
do
  sleep $SLEEPDELAY
  STATUS=`wmctrl -x -l | grep $WINCLASS | wc -l | awk '{print $1}'`
done

wmctrl -x -r $WINCLASS -b toggle,fullscreen

```

When I run this, XBMC loads windowed as expected, but then the wmctrl line seems to be ignored.  I tried increasing the delay to 10 seconds just in case, but as XBMC launches considerably quicker than boxee, I wouldn't think this is the issues.

If anyone could assist it would be great..apologies if this is in the wrong forum, I was recommended to post this here.

Thanks

---

### Post by odyniec on 2009-05-14
> ```
WINCLASS=XBMC Media Center.XBMC Media Center
```

I think you should add quotes in the above assignment, i.e.:
```
WINCLASS="XBMC Media Center.XBMC Media Center"
```

---

### Post by PureLoneWolf on 2009-05-14
Thanks for the tip, I just tried what you said, but it didn't work unfortunately.

---

### Post by odyniec on 2009-05-14
Are you sure the wmctrl command is actually executed? Could it happen that $STATUS is always non-zero and the while loop goes on forever?

---

### Post by PureLoneWolf on 2009-05-15
Actually, I am pretty certain that it isn't being executed.  If I launch XBMC and then run the wmctrl commmand in a terminal, it works as expected.

Would you know of another way to achieve this in a script?  I know the wmctrl command that works, I just want it to execute a couple of seconds after the xbmc app launches.

Many thanks

---

### Post by odyniec on 2009-05-15
Try some debugging then -- if the command is not executed, then apparently the while loop does not end, and $STATUS is non-zero. You could verify this by echoing $STATUS in the loop:

```
while [ $STATUS -eq 0 ]
do
  sleep $SLEEPDELAY
  STATUS=`wmctrl -x -l | grep $WINCLASS | wc -l | awk '{print $1}'`
  echo $STATUS
done
```

---

