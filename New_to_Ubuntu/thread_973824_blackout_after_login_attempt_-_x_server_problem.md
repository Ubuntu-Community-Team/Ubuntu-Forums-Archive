---
title: "blackout after login attempt - x server problem"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by emmvie on 2008-11-07
after updating my hardy heron with kde 3, i have a massive problem of some kind with the x server and am completely clueless what to do.

i can log in on the bash, but on the bash apt get doesn't work so i can't reinstall, i don't think. when i try to run a program - for example kmail - i get the message "cannot connect to x server".

when i enter my password normally in the kubuntu login dialog, the screen goes black briefly, then the login dialog returns. and i KNOW the password is right because it works in the bash. i have this problem trying to get into kde OR into gnome, both of which i have installed and use alternately. now it doesn't even take my password anymore, probably because it spit me back out so many times???

i THINK i must reinstall the x server. anyone have any ideas or suggestions for me? my fear is, of course, data loss...

thanks.
emmvie

---

### Post by saru411 on 2008-11-07
After the POST you should see grub counting down in the upper left side of the screen from 3. while it is counting down hit ESC. Now boot in recovery mode. From there you can fix xserver and reboot normally.

---

### Post by Peter09 on 2008-11-07
It may be your video driver

Configuring your Video Driver:

1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers (ubuntu menu)
2. Boot into recovery mode and select xfix from the menu, this may resolve it. (Check 1. after doing this as well)

also post the output of the code below so that we can see which driver is active.
```
lshw -C display
```

---

