---
title: "[SOLVED] Boot to Command Interface, not GDM."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by ant2ne on 2008-10-25
Is there a conf file or something that I can modify to prevent the system from booting into GDM by default, and instead boot to CLI by default?  I would actually prefer it to NOT load Gnome or GDM at all, until I tell it to.

---

### Post by sdennie on 2008-10-25
Go to System->Administration->Services and disable Graphical Login Manager (gdm).  Note: This will immediately terminate your X session.  To then start gdm from the command line:

```

sudo /etc/init.d/gdm start

```

---

### Post by bhadotia on 2008-10-25
You can also choose to start the recovery mode at start up if you want the CLI only, but that has limited resources.

---

### Post by McAngus on 2008-10-25
i believe the file you're looking for is here


/etc/X11/default-display-manager

just change the path from /usr/sbin/gdm to wherever the path of cli is located

---

### Post by ant2ne on 2008-10-25
Lets assume that the system in question crashes when GDM starts, which it currently does by default.  So I need to boot either directly to CLI or modify something when booting from CD so that it stops crashing. Then I can examine xorg.conf and troubleshoot further.

---

### Post by ant2ne on 2008-10-25
> **McAngus said:**
> i believe the file you're looking for is here
/etc/X11/default-display-manager
just change the path from /usr/sbin/gdm to wherever the path of cli is locatedAny idea where that path might be?

---

### Post by dracayr on 2008-10-25
wait a minute. If you just want to boot directly to CLI temporarily to repair your system, use the recovery mode. If you don't have a dual boot, press esc on startup. Then, in the grub menu (If you have a dual boot, you should be presented the menu without pressing esc), choose the option with (recovery mode) behind it. After booting, you should be presented with 3 options. First try the repair X... option. Then, try the resume normal boot, and if that doesn't work, use the root prompt option to troubleshoot. from the root prompt, startx /usr/bin/gnome-session should start x without starting gdm (I haven't tried this, but I think it should work).

dracayr

---

### Post by ant2ne on 2008-10-25
suppose I'm not using grub.

---

### Post by lswb on 2008-10-25
> **ant2ne said:**
> suppose I'm not using grub.

Then for whatever bootloader you are using, do whatever is required to edit the kernel options line to have the word "single" at the end without quotes.

Ubuntu uses the upstart system for starting services, instead of the older init system still used by many other distros. Ubuntu's implementation of upstart somewhat complicates changing services that run at startup.

If you want to boot ubuntu to a text mode, multiuser login, as opposed to the single user recovery mode, there are different ways to do it.

Here are a few:

1) Modify your default runlevel so that it does not start gdm or other gui. A hardy default install always boots to runlevel 2 so you would modify the links in /etc/rc2.d. To stop gdm from running you can just 
sudo mv /etc/rc2.d/S30gdm s30gdm. I rename the link rather than just remove it so it will be easy to find and change back if desired. There are a few other services that can also be skipped. Check the man page for update-rc.d for another, perhaps better way of manipulating these links, or install sysv-rc-conf or a similar program from the repositories.

2) Modify a different runlevel, say runlevel 3, as above (links in the /etc/rc3.d directory instead of /etc/rc2.d) and use an /etc/inittab file to cause the system to boot into runlevel 3. This will preserve the default as-installed runlevel 2 settings, and you can switch to runlevel 2, thus starting gdm, with the command "sudo telinit 2" The /etc/inittab file should have this line to designate runlevel 3:
```

id:3:initdefault:

```

3) If you are only occasionally going to use the text mode login and don't mind an extra step, change the rc3.d links as above. Boot to recovery mode, drop to root shell, and use the command "telinit 3". Or, for a recovery menu item in hardy, create a file named named "textmode" (Name not important) in /usr/share/recovery-mode/options with the contents:
```

#!/bin/sh

if [ "$1" = "test" ]; then
  echo "Runlevel 3: Text mode"
  exit 0
fi

/sbin/telinit 3

```

4) The most flexible way is to modify the the file /etc/event.d/rc-default so that different runlevels can be specified on the kernel option line at boot. Then you can put menu items for the different levels in your grub menu ( or other configurable boot loader ) See this thread, post # 8 for more details:

[http://ubuntuforums.org/showthread.php?t=863539](http://ubuntuforums.org/showthread.php?t=863539)

---

### Post by ant2ne on 2008-11-02
> **McAngus said:**
> i believe the file you're looking for is here


/etc/X11/default-display-manager

just change the path from /usr/sbin/gdm to wherever the path of cli is located

Changed to

```
/bin/bash
```

booted right into a CLI. Thanks

Now to repair xorg.conf

---

