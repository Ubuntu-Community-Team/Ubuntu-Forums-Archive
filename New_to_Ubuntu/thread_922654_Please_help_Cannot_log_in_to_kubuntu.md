---
title: "Please help: Cannot log in to kubuntu"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by buntu_hugenewbie11 on 2008-09-17
Please help me. :-(
I recently used synaptic package manager to remove older images of ubuntu to free up some hard drive space.
I was instructed to choose "complete removal".
It cleaned up my grub screen nicely but now I have a problem:
when the log in screen appears for kubuntu
I log in like I always do.
The screen goes blank and returns me back to the log in screen like nothing happened. (If I enter in the wrong password it gives me a different error so I think it validates the password correctly.)
When I hit Ctrl-Alt-F1 and log into command line I log in correctly.
But when I try to startkde I get the following errors:

xsetroot: unable to open display
ksplash: cannot connect to X server
xpropo: unable to open display.
kdeinit: Aborting $Display is not set.
Warning: connect() failed: No such file or directory
ksmserver: cannot connect to X server
Error: Couldn't attach to DCOP server!
startkde: Shutting down...
Warning: connect() failed: No such file or directory
Error Can't contact kdeinit!
startkde: Running Shutdown scripts
xprop: unable to open display
startkde: Done

---

### Post by buntu_hugenewbie11 on 2008-09-17
As an update, when I create a new user I am able to login to gnome and kde using that user.
But when I use the other user to login I just get booted back to the login screen.
How can I fix this behavior for that user? Ideas?
I am using gutsy amd64.

---

### Post by Crafty Kisses on 2008-09-17
Try this command:
```
startx
```
Post back please.

---

### Post by buntu_hugenewbie11 on 2008-09-17
I cannot see all the output but when I am the problematic user in command line and I run startx I get the following output when it crashes:

Using config file: "/etc/x11/xorg.conf"
(II) Module already bult in
(II) Module already bult in
(EE) Failed to load module "type1" (module does not exist, 0)
(II) Module already bult in
Atom 4 CARD32, unsigned long 8
The XKEYBOARD keymap compiler (xkbcomp) reports: 
Warning: Type "ONE_LEVEL" has 1 levels but <RALT> has 2
Ignoring extra symbols
Errors from xkb are not fatal to the X server
Synaptics DeviceInit called
SynapticsCtrl called
Could not init font path element ?usr/share/fonts/X11/cyrillic, removing from list!
chmod: changing permissions of `/home/dave/.xsession-errors' Operation not permitted.
Synaptics DeviceOff called
waiting for X server to shutdown FreeFontPath: FPE "/usr/share/fonts/X11/misc"
refcount is 2, should be 1: fixing.

---

### Post by unutbu on 2008-09-17
Please post the output of 
```

cd
find . -maxdepth 1 -not -user $USER  -print | xargs ls -l
```

This will list all files in the top level of your home account which you do not own.

This error
> 
chmod: changing permissions of `/home/dave/.xsession-errors' Operation not permitted.
suggests you are not the owner of certain files that you should be the owner of.

Hm. Perhaps just try
```

sudo chown -R $USER:$USER ~
```

This will make you the owner of everything in your home account.

---

### Post by buntu_hugenewbie11 on 2008-09-17
I was able to login to kde finally from command line by doing the following:
1. In home directory create a file called ".xinitrc"
2. In ".xinitrc" place the following line:

exec startkde

3. Save and close the file and then go to the command line and 
   type "startx"

Now I will try your commands.

---

### Post by buntu_hugenewbie11 on 2008-09-17
As for files that I do not own.
The list includes just standard content folders.
There are many but nothing system based pops up.

Everything seems to work after that command I entered about xinitrc.

So my question is:
What does that command do and what do you think happened?
Thanks for the help though.

---

