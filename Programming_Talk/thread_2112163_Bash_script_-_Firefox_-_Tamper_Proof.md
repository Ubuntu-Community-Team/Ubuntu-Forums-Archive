---
title: "Bash script - Firefox - Tamper Proof"
date: 2013-02-04
forum: Programming Talk
---

### Post by rodmiles on 2013-02-04
Hi All,

New to the Ubuntu OS (12 months in) and trying to setup a machine with a script to take care of some functions we need to make it useable as a bit of a kiosk machine.

Basically the machine is logged in as a restricted user, firefox automatically starts up (startup application with website as homepage) in fullscreen and is directed to the website.

The bash file I am running on start up is as follows:

#!/bin/sh

# Checks if Firefox is running and starts it if it has been closed

CHECKPOINT=2 # seconds

while [ true ]
do
echo -n "`date +%r` Firefox is "
if [ -z "`pidof firefox`" ]
then
echo "not running! Starting Firefox now."
firefox &
else
echo "running. Checking in $CHECKPOINT seconds."
fi
sleep $CHECKPOINT
done

I am hoping that someone could tell me how I can incorporate the following operations into this code to get the desired result?


[LIST]
[*]Startup Firefox in fullscreen showing only the Back, Forward, Reload and Home buttons.
[*]Do not allow Firefox to be closed or minimised.
[*]Hide the Minimise, Restore and Close buttons if possible.
[*]Restart Firefox if it is closed (already the basis of the code above)
[/LIST]
I know there are add-ons for kiosk style machines but they are somewhat  lacking in functionality and I would like to make it pretty robust and  configure the code so every eventuality will be covered.

Thank you in advance to anyone who might have the time and the inclination to help out with some code.

---

### Post by codemaniac on 2013-02-04
Please do not start multiple threads for the same issue, it only dilutes the community efforts. You can carry the discussion on the mentioned issue in your original thread.

[http://ubuntuforums.org/showthread.php?t=2109591](http://ubuntuforums.org/showthread.php?t=2109591)

Thanks!

---

