---
title: "Lock screen and sleep display using key command"
date: 2010-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Dugger5688 on 2010-12-03
For some reason or the other, my screen was failing to lock after gnome-screensaver came on. To be honest, I'd much rather just have it lock and have the display turned off instantly. This is my first tutorial, so let me know if anything is wrong with it!

First, create a scripts directory in your home folder:
```
mkdir ~/scripts
```

Then, create and edit a new script called display.off:
```
gedit ~/scripts/display.off
```

Once gedit is open type the following into your script:

```

#!/bin/bash
#locks and puts display to sleep
gnome-screensaver-command --lock
xset dpms force off

```

Save your script and close gedit, then navigate to your scripts directory and change the permissions of your script. I set mine to 750, or read/write/execute for yourself, read/execute for your group, and nothing for others (to prevent any other user from invoking the script).
```

cd ~/scripts
chmod 750 display.off

```

Now to set the key combination, go to System->Preferences->Keyboard Shortcuts. First find your shortcut to lock the screen (should be 'Ctrl+Alt+L'), select the shortcut command and hit 'backspace' to clear it. Then click the Add button. Enter the following, replacing $USER with your username:

```

Name: Lock and Sleep Screen
Command: /home/$USER/scripts/display.off

```

Finally, press the shortcut to change the key combination and hit the control, shift and L keys.

---

### Post by Auxao on 2011-08-13
Great tutorial!

I was wondering if there is also a command to change the timer for which the display sleeps on its own.  That way, in case the it wakes unexpectedly, the display will sleep again much sooner than I would normally have it set to.

Thank you!

---

