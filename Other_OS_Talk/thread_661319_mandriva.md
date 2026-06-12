---
title: "mandriva"
date: 2008-01-07
forum: Other OS Talk
---

### Post by themuddaload on 2008-01-07
well, i installed mandriva on my computer, and wanted me to make my username and password. 

i did the wrong thing for my username, and wanted to go back to change it, so i pressed cancel. instead of going back, it takes me to a log in screen, and now i cant log in, and the window wont pop up any more, so i cant just redo. 

help please, 
thanks.

---

### Post by SunnyRabbiera on 2008-01-07
err, you might be sol.
normally you can try to log in as root if you set up a password for it, just type in root as the user name and then the root password but root logins are disabled...
you may need to re install

---

### Post by MissionImpossible on 2008-01-07
> **themuddaload said:**
> well, i installed mandriva on my computer, and wanted me to make my username and password. 

i did the wrong thing for my username, and wanted to go back to change it, so i pressed cancel. instead of going back, it takes me to a log in screen, and now i cant log in, and the window wont pop up any more, so i cant just redo. 

help please, 
thanks.
If you can get to Console mode (Ctrl+Alt+F1 or however you can get there) and login as root, the following should be your fix:

adduser user_name
Create a new account (you must be root). E.g.,  adduser barbara  Don't forget to set up the password for the new user in the next step. The user home directory is /home/user_name.

useradd user_name
The same as the command " adduser user_name ".


userdel user_name
Remove an account (you must be a root). The user's home directory and the undelivered mail must be dealt with separately (manually because you have to decide what to do with the files).

Linux Newbie Administrator Guide 
Linux Shortcuts and Commands: [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

