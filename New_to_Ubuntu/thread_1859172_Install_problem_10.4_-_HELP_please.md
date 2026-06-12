---
title: "Install problem 10.4 - HELP please"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by bk60544 on 2011-10-13
>>Installed 10.4 yesterday as dual boot with Win7, and all was fine.  Today I get an error message: Installation Problem. The configuration defaults for GNOME Power Management have not been installed correctly.  Contact your system administrator."  
>>Newbie to Ubuntu, so no clue how to proceed / REPAIR.

---

### Post by ezramorris on 2011-10-13
> **bk60544 said:**
> >>Installed 10.4 yesterday as dual boot with Win7, and all was fine.  Today I get an error message: Installation Problem. The configuration defaults for GNOME Power Management have not been installed correctly.  Contact your system administrator."  
>>Newbie to Ubuntu, so no clue how to proceed / REPAIR.

Try this:

Once booted up, drop to a console by pressing Ctrl-Alt-F2, and log in using your usual username and password.

Then try reconfiguring unconfigured packages:
```
sudo dpkg --configure -a
```
(enter your password if asked)
When it's done:
```
sudo service gdm restart
```

The login screen should then reappear. Try logging in to see if you still get the error message.

If you still have the problem, press Ctrl-Alt-F2 to get back to the console, then check for and install any updates:
```
sudo apt-get update && sudo apt-get dist-upgrade
sudo service gdm restart
```

Hope this helps,
Ezra.

---

