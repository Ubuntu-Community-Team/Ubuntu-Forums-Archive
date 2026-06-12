---
title: "Cant run virtual box--the error displayed is The VirtualBox kernel driver is not acce"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by rraj.be on 2008-05-21
i started virtual box for the first tiem and i got the following error in a dialog box.

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```


what shoud i do now

---

### Post by Maestro23 on 2008-05-21
Following thread will tell you the steps needed to be done.

[http://ubuntuforums.org/showthread.php?t=797298&highlight=write+permissions+%2Fdev%2Fvboxdrv](http://ubuntuforums.org/showthread.php?t=797298&highlight=write+permissions+%2Fdev%2Fvboxdrv)

---

### Post by HotShotDJ on 2008-05-21
> **rraj.be said:**
> what shoud i do nowMy bet is on "Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect"

You can add users to the vboxusers group through System --> Administration --> Users and Groups

Make sure to unlock it first (see unlock button).  Now, "Manage Groups" and highlight vboxusers and click on the Properties button.  Check off the user(s) you wish to allow access to VirtualBox.  Log out and back in (no need to reboot)

All should work now.

---

