---
title: "HowTo: Remove the locked screen login after resume from suspend or hibernate (8.04)"
date: 2008-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by AaronMT on 2008-06-01
Hi all,

This is a very short and simple tutorial on how to remove the locked screen login prompt after resume from suspend or hibernation in Ubuntu 8.04 (Hardy)

All you have to do is comment out a single line in a specific configuration file.

First, lets bring up a terminal window. **Applications -> Accessories -> Terminal**

Now that we have a terminal up, let's enter the **command** ```
gksudo gedit /etc/default/acpi-support
```

This will grant authoritative access to the configuration file which handles suspend and hibernation operations and utility.

Once the file is open in gedit text editor, let's scroll down to the line ```
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true
```

**LOCK_SCREEN** is a boolean variable that has a true and false value. Rather than change its value to false, let's simply comment it out by placing a **#** before **LOCK_SCREEN** so that the enter line becomes, ```
#LOCK_SCREEN=true
```

Let's now save and we're done. **Reboot or Ctrl-Alt-BackSpace (to restart Ubuntu)** for changes to take effect and you can now try to suspend or hibernate and your changes should be there.

To set LOCK_SCREEN again, repeat the process, but remove the # instead.

That's it, enjoy.

- AaronMT

---

### Post by AaronMT on 2008-06-08
Just wanted to update this thread with some findings. My tutorial above worked for a few reboots of my laptop and now the lock screen has returned regardless of the changes.

I'm bumping this thread for any possible findings or discussion if any of you find a reason for this behavior.

---

### Post by NTolerance on 2008-06-09
I have always used gconf-editor to do this.  No root access required.  

Run:
```
gconf-editor
```

Go to
apps -> gnome-power-manager -> lock

and uncheck hiberate and/or suspend as desired.

---

### Post by hihihi on 2008-07-10
yes, this will not work on mine, the change in acpi_support will not deactivate the prompt and unchecking the boxes in gconf-editor also do nothing.
anyone with same problem?
i guess this has to do with ubuntu hardy having pm-utils as default instead of acpi scripts.
unfortunately, pm-utils do not work at all on my maschine, acpi-scripts do.

edit:
i managed to get pm-sleep working by doing the following (tip from launchpad):
       $ sudo su
       $ echo "SUSPEND_MODULES=\"uvcvideo\"" >/etc/pm/config.d/unload_modules
       $ chmod +x /etc/pm/config.d/unload_modules

now, after suspend with pm-suspend, the changes suggested above took place.
login-prompt will not come up.
thanks

---

### Post by SkonesMickLoud on 2008-07-10
Also, CTRL+ALT+BACKSPACE doesn't restart Ubuntu.  It restarts X.

---

### Post by hihihi on 2008-07-10
yeah, you better reboot the whole thing :KS

---

### Post by Signal64 on 2008-10-12
Ack!  After fighting with this for awhile I found one way to get this to work.

You use gconf-editor, but don't run it from a terminal session.
I'm sure it has to do with the path to the config files, but to be on the safe side try this.

1. Add gconf to your menu.

Go to System Preferences -> Main Menu

Select System Tools on the left
Check Configuration Editor

Exit

2. Now open Applications -> System Tools -> Configuration Editor

Follow NTolerance's advice.
Within the configuration tool go to apps -> gnome-power-manager -> lock
and uncheck hiberate and/or suspend as desired.

---

