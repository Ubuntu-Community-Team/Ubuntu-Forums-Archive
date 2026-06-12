---
title: "Ctrl+Alt+Del ain't what it used to be."
date: 2012-01-28
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-28
For as long as I can remember, Ctrl+Alt+Del has been the first-line method of escape from sticky PC situations - before REISUO/REISUB - before Switching off - before Pulling the plug.

I just found out by accident, that in 11.10, Ctrl+Alt+Del only brings up a Logout Dialog with no Shutdown option.

I don't think I like that (maybe it is OK?) so looked for alternatives.

I found this & have applied it OK.
[http://askubuntu.com/questions/75343/how-can-i-assign-ctrlaltdelete-to-shutdown-dialog](http://askubuntu.com/questions/75343/how-can-i-assign-ctrlaltdelete-to-shutdown-dialog)
Mapping the command ```
/usr/lib/indicator-session/gtk-logout-helper --shutdown
```  to Ctrl+Alt+Del now brings up the Shutdown Dialog box & I can escape by "Enter" or, I suppose, by waiting 60 sec.

Is there any way I can map the final Shutdown command directly to this key combination, to have 1-step shutdown?
What extra am I risking by going that way instead of the 2-step way?
Can I find a list of alternative commands for this sort of action?

Thanks!

---

### Post by SteveDee on 2012-01-28
> **2CV67 said:**
> ...Can I find a list of alternative commands for this sort of action?...

I think there are a couple of "immediate" options discussed here: [http://www.stackprinter.com/export?service=askubuntu&question=53263&printer=false&linktohome=true](http://www.stackprinter.com/export?service=askubuntu&question=53263&printer=false&linktohome=true)

---

### Post by ajgreeny on 2012-01-28
If your machine really has frozen, there is often nothing that can be done, even REISUB will do nothing if the keyboard will not respond or take any key-presses.  However if you want an instant shutdown you can make a new launcher with the command ```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
``` which will work without any intervening query about what you want to do.

---

