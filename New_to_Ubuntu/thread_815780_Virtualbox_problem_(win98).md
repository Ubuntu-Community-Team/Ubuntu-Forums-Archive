---
title: "Virtualbox problem (win98)"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by penguinbreath on 2008-06-02
[[IMG]http://img105.imageshack.us/img105/2063/screenshotwin98runningvyh9.th.png[/IMG]](http://img105.imageshack.us/my.php?image=screenshotwin98runningvyh9.png)

I got stuck here during the installation of Windows 98 inside Virtualbox. It seems it is looking for some .dll from the Win98 CD. It says it cannot find it.
I tried unmounting/mounting the cdrom drive, however it still does not work.

Any ideas?

---

### Post by bumanie on 2008-06-02
Have a look at the virtualbox documentation re windows 98 problems.
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

### Post by penguinbreath on 2008-06-02
>  Have a look at the virtualbox documentation re windows 98 problems.
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)


I could not find anything in the link relating to my problem, however the wiki may prove useful to me in the future. Thanks.



I got through the installation of win98, however win98 was never able to get the drivers/.dll's it needed to run properly (since it could not pull it off the disk?), and I am getting a lot of errors saying a driver/.dll is missing when I run win98.


Another problem I am having:
I get this error message when I start virtualbox:

```
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
```

I set the permissions of /dev/vboxdrv, logout and login, and virtualbox works. 
However when I reboot, the permissions seem to get set back to where they were before, and I get the above error message. I go back again and set /dev/vboxdrv permissions, and everything works until I start my computer back up again. 

  Is there a way I can permanently set the permissions of /dev/vboxdrv so I don't have to set them every time I start my computer and use virtualbox?

Edit: 
Here is a screenshot
[[IMG]http://img75.imageshack.us/img75/4628/screenshotvboxdrvproperrg6.th.png[/IMG]](http://img75.imageshack.us/my.php?image=screenshotvboxdrvproperrg6.png)
As soon as I reboot, the permissions need to be tampered with again.

---

### Post by Nchalada on 2008-06-12
the easiest way to do this is goto system, administration, users and groups

click manage groups, press "v", then edit vboxusers, place a tick on your name, click "close", till you're back at the desktop, then reboot

should work fine then :D

Tony

---

