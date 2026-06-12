---
title: "I cannot cd into a dir as normal user ?"
date: 2019-11-17
forum: New to Ubuntu
---

### Post by automate-stuff on 2019-11-17
I used to be able to cd into ```
/etc/X11/xorg.conf.d
``` as a normal user.
But now I cannot, I get this error:

 **bash: cd: xorg.conf.d: Permission denied.**

 I have to switch to root in order to be able to cd into xorg.conf.d .. notice that I can cd into /etc/X11/ but not xorg.conf.d

any fixes ?

---

### Post by CatKiller on 2019-11-17
It's the execute permission that lets you enter a directory. By default you can. I suspect that you've been playing around with permissions.

---

### Post by TheFu on 2019-11-17
This will explain: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by automate-stuff on 2019-11-17
I ran **sudo geany** in the terminal and then entered the password and then I edited **/etc/X11/xorg.conf.d/20-intel.conf** ... does this cause problems ? how do I fix this ? 

[COLOR=#000000][FONT=&amp]I also opened **/etc/rc.local **and I get Permission denied errors about it at boot..
[/FONT][/COLOR]

---

### Post by TheFu on 2019-11-17
Using sudo with any GUI program can cause problems, especially when a solid understanding of permissions is lacking.  This is because almost all GUI programs want to create a config file which will be in the wrong HOME directory and owned by the wrong userid.  Any parent directories that have to be created will also be owned by the wrong userid, hence all sorts of pain.

To edit system files, please use **sudoedit**.  You can configure the EDITOR variable to use any editor you like.

Newer Ubuntu releases don't use rc.local.  

If you need specific help with permissions, please post the permissions using ls -al output.  We need to see the directory, parent directory and file permissions, including the owner, group, other, and any ACLs.  Without that data, we cannot possibly help with no risk of harm.

---

### Post by automate-stuff on 2019-11-17
I did:** chmod a+x xorg.conf.d** and **chmod a+r xorg.conf.d**

then I could cd into xorg.conf.d ... 

here is the output of ls -al /etc/X11/xorg.conf.d/ : 

[B]-rw-r--r-- 1 root root  140 Nov 17 22:08 10-intel.conf
-rw-r--r-- 1 root root  226 Nov 12 19:46 20-monitor.conf[/B]

I opened these two files with geany....Do I have to worry about /etc and /etc/X11 too ?

 here is the output of ls -l /etc/rc.local : 

**-rwxr-xr-x 1 root root 586 Nov 17 22:09 rc.local**

I edited rc.local and added the following lines to it (using geany): 

[I]echo enabled > /sys/bus/usb/devices/1-1.5/power/wakeup
echo enabled > /sys/bus/usb/devices/2-2/power/wakeup
echo enabled > /sys/bus/usb/devices/2-3/power/wakeup[/I]

At boot I get an error that wakeup cannot be created at /sys/bus/usb/devices/1-1.5/power/ ...

Also, I cannot create a file under /sys/bus/usb/devices/1-1.5/power/ not as a normal user and neither as root.

please help!!

---

### Post by uRock on 2019-11-17
That'd be a lot easier to read if you used code tags. [noparse]```
whatever code
```[/noparse]
Edit: you formatted while I was typing. Looks a lot better.

---

### Post by CatKiller on 2019-11-17
> **automate-stuff said:**
> Also, I cannot create a file under /sys/bus/usb/devices/1-1.5/power/ not as a normal user and neither as root.

No. Those [aren't really files.](https://en.wikipedia.org/wiki/Sysfs)

---

### Post by TheFu on 2019-11-17
And the permissions for the directory and parent directory?  That would be the first two items in an **ls -al** listing.

rc.local doesn't work on newer releases unless you specifically setup something to make it work.

Never assume that a directory exists.  If it doesn't, trying to create a file inside it won't work.  Different releases put power management stuff in different places.  Usually, there is a better way than to write to /sys/. Perhaps there isn't in this situation. I don't know.

+1 on the code tags. Much easier to enter too.

---

### Post by oldrocker99 on 2019-11-18
The recommended way to edit system text files (at least AFAIC) is nano.
```
sudo nano /etc/default/grub
```
For example. Nano does not use standard commands, but every command is on the margin of the window. To save, you use CTRL-w (for Write out), for example.

I've been editing system text files that way since 2008, about a month after I started using Linux.

It's already installed on virtually every distribution.

---

### Post by Holger_Gehrke on 2019-11-19
Actually the IMHO best way to edit system files is to use 'sudoedit'. This copies the file to a temporary file, runs the editor of choice (configurable through the environment variables - in order of precedence - SUDO_EDITOR, VISUAL and EDITOR or an entry in /etc/sudoers) **without elevated privileges** and copies the edited file back when you exit the editor. This has at least two advantages: you're not running the editor as root so you can use a GUI editor, and if you do a longer editing session you can save whenever you want without having to make sure the file is in a usable state.

And /etc/rc.local works just fine, but you have to enable it with 'systemctl enable rc-local' and /etc/rc.local has to be executable (didn't need that with the old init, it was sourced from another script) and it needs to have a '#!/bin/bash'-line at the start to identify the interpreter for it (obviously that wasn't necessary for the old init either and yes, that means you should be able to have a script written in another language than the shell as your rc.local).

Holger

---

