---
title: "firefox is preventing the screen from going off"
date: 2024-10-16
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2024-10-16
the only opened tabs are..
tuta mail, tuta calendar, and proton drive..
it started a month ago..

how can i fix it?

thanks

---

### Post by ronjjjg8885 on 2024-10-18
anyone?

ive asked it elsewhere

---

### Post by maglin2 on 2024-10-19
I'm not sure if would-be helpers will fully understand what the issue is from the description.

Are you saying that when Firefox is running the timed power settings  actions to turn off the screen or suspend the machine after defined periods of inactivity don't work?

Or are you saying that when Firefox is running GUI or command line inputs eg ```
systemctl suspend
```
 or ```
loginctl lock-session
``` to suspend machine/lock screen don't work?

---

### Post by maglin2 on 2024-10-19
If you go to 
Settings/Apps/Firefox/Permissions
you should see that it is allowed to 'Prevent screen sleep/lock' (4th item up from bottom)
Slide that toggle to the left and hopefully your issue will go away.
Having said that, I leave that permission enabled, and have never seen the issue you report.
Perhaps try looking at Firefox's Task Manager to see if anything unexpected is running, try disabling extensions, or create a new Firefox profile and see if the problem still applies?

---

