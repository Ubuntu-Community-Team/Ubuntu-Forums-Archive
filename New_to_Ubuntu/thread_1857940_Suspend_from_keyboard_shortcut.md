---
title: "Suspend from keyboard shortcut"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by thatoneguy99 on 2011-10-11
Good Morning Ubuntu Fam,
 
I did search the forum and found a few threads but none with a definitive answer!
 
I am on Natty just FYI. I am trying to figure out how to create a keyboard shortcut for suspend mode. I just want to push a couple of keys together and have the computer go to sleep. I tried making a bash script with ```
sudo pm-suspend
``` in it and it would pull up terminal asking for sudo password. I tried putting the user in SUDOERS but I figure that I did it wrong because it was still asking for a password. 
I just need a simple solution to put the computer in suspend mode from a keyboard shortcut. I dont care about security with the root password whatsoever...
Could somone please help me out with EXACTLY what I need to do so I dont have to put in a sudo password or anything of the sort. Thank you very much in advance.

---

### Post by Lisiano on 2011-10-11
Good evening.
Please take a look at this [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
I'm not an expert on the sudoers file so I can't help in how to set it up so you can use pm-suspend without a sudo password, but the page I linked above should help you.

---

### Post by thatoneguy99 on 2011-10-11
Forgive me if I sound like an ***. I have looked at the SUDOERS manual and information and wasn't able to figure it out. I am expecting someone to spoon feed me the answer.

---

### Post by Lisiano on 2011-10-11
My sudoers file looks like this```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
``` You need to make it like this (As far as I understand it)
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt, /usr/sbin/pm-suspend-hybrid, /usr/sbin/pm-suspend, /usr/sbin/pm-hibernate, /usr/sbin/pm-powersave

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%admin ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL
#includedir /etc/sudoers.d
```This will let anyone who is a member of the admin group to execute any of the commands in the SHUTDOWN_CMDS, that is shutdown, reboot, halt and any pm-* command without a password.

---

### Post by thatoneguy99 on 2011-10-11
Thank you very much! I am at work right now but I will try this when I get home and let you know what happens. What you have added in sudoers does not look like what I added so that could be my mistake.

---

### Post by Toz on 2011-10-11
You might also be able to suspend your computer using dbus. The benefit is, you won't need elevated privledges to do so (no need for sudo). Here is the command:

```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

---

### Post by thatoneguy99 on 2011-10-11
Toz it worked perfectly. I have that command binded to a keyboard shortcut and it just works. Thank you very much! Lisiano thank you as well but Toz's suggestion just seemed easier and more straight forward. Have a good day!

---

### Post by Toz on 2011-10-11
Glad to hear. Can you please make this thread "Solved" using the Thread Tools link above?

---

