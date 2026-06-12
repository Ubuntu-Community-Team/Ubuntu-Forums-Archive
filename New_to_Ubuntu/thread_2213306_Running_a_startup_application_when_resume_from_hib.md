---
title: "Running a startup application when resume from hibernation."
date: 2014-03-25
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-03-25
Hi, Running Ubuntu 13.10 on a hp netbook. Hibernation works great (just had to enable it) but I have a small problem here. I have made a script to run at start up to enable edge scrolling on the touchpad, it works at startup but not on resume from hibernation. [http://ubuntuforums.org/showthread.php?t=2211813](http://ubuntuforums.org/showthread.php?t=2211813) 

I can manually run it by clicking the .run file but since I am setting this laptop up for someone not into tinkering I would like to find a way for it to start automatically after resume from hibernation/suspense. 

Any help would be greatly appreciated.

---

### Post by Toz on 2014-03-25
synclient requires that an active X session is available. Post hibernation scripts are best run from /etc/pm/sleep.d, but since they are run as root outside of the user X session, synclient commands can not be executed. However, you can export your DISPLAY and XAUTHORITY variables and it should find the X session and make the changes. 

To that end, with root privileges, create the file **/etc/pm/sleep.d/99_synclient** with the following content:
```

#!/bin/bash

USERID=<your_user_id>
SCRIPT="/full/path/to/run/file"

case "$1" in
  suspend|hibernate)
     ;;
  resume|thaw)
    export DISPLAY=":0"
    export XAUTHORITY="/home/$USERID/.Xauthority"
    su $USERID -c "$SCRIPT"
     ;;
  *) exit $NA
     ;;  
esac
```
...make sure you change values of USERID and SCRIPT to their proper values (USERID should be your login userid and SCRIPT should be the full path to the script file (make sure it accessible outside of your session - not encrypted).)

Make /etc/pm/sleep.d/99_synclient executable and see if that helps.

---

### Post by monkeybrain20122 on 2014-03-26
Hi, 

Thanks for the tip. Using your method the script does run after waking up from suspension, so there is progress. But the computer doesn't hibernate any more. Instead it goes to suspensopn. Removing 99_synclient and it hibernates again when lid is closed but my script doesn't run on resume. In 13.10 the hibernate option is missing in the power settings even when hibernation is enabled in the drop down menu (the gear menu with shut down, logout and suspend) . I followed this tutorial to initiate hibernation when closing the laptop lid. [URL="http://ubuntuhandbook.org/index.php/2013/12/change-behavior-when-lid-is-closed/"]http://ubuntuhandbook.org/index.php/2013/12/change-behavior-when-lid-is-closed/

[/URL]

---

### Post by Toz on 2014-03-26
Hmmm. Can you post back the contents of the script you created (to verify) and also the contents of /var/log/pm-suspend.log when the 99-synclient is being used after a hibernate attempt?

---

### Post by monkeybrain20122 on 2014-03-27
Hi,

It all works now! Thanks to the hint I checked pm-suspend.log for errors. It turned out I have put <user_id> with the <> instead of just user_id in the second line. 
Thanks a lot for the help! I am marking this thread as solved.

---

