---
title: "creating a startup program"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by syam-nair on 2013-11-02
I need to create a startup program, so that it may load after bootup.  The application to boot was written in python and the same was given  executable permissions and works fine. From a little surf up in internet  I came up with this **short code for autobooting and placed in under /etc/init.d/** and updated rc.d using **update-rc.d <filename> defaults**. But I was not successful in this try out. Please help me out.

code in init.d/<filename>

 [B]#! /bin/sh

case "$1" in
  start)
    echo "Starting python gui test"
     /home/syam/Documents/gui1.py
    ;;
  stop)
    echo "Stopping python gui test"
    killall gui1.py
    ;;
  *)
    echo "Usage: /home/syam/Documents/gui1.py {start|stop}"
    exit 1
    ;;
esac

exit 0 
[/B]
The app runs when I run **/home/syam/Documents/gui1.py {start} **in terminal**, **but I require it to startup at boot; like in windows startup programs

---

### Post by rihikz on 2013-11-02
If you are using Ubuntu,
search for 'Startup Applications' in the dash. Open up the first result and add an application. The 'command' box is basically a terminal command.

---

### Post by ian-weisser on 2013-11-02
Your /etc/init.d script does indeed run at boot...as root, and not attached to a display.
That's probably not what you want.

There are ways to run jobs at boot. Those jobs are usually run as root or a system user.
There are ways to run jobs when anybody logs in. Those jobs may be run as root, a system user, or that user.
There are ways to run jobs when only a specific user logs in. Most of those jobs run as that user. rihikz is right about how to make that work for you.

---

### Post by syam-nair on 2013-11-03
Thanks rihikz and ian-weisser; adding to startup is working for me, tried that. :D

But I 'm trying to build a specific machine stripping down Ubuntu GUI and only run my program, as programming in raspi or beaglebone. So I need help with scripting for the same so that I may boot it without adding via "startup applications". All suggestions are welcome

@ian: is there any way I can change these to run at lower permission levels. I don't need to run them as root, may be sudo group or lower will do, assuming system has only one user other than su. Thanks in advance :)

---

### Post by ian-weisser on 2013-11-03
Well, a truly stripped-down system would use ncurses instead of an X server. How stripped-down do you want?
If you plan on keeping an X server, your current method (Startup Applications) is the right way to start user-level applications.

You can certainly run non-root startup jobs the same way the system does, by creating another user or system user, and changing ownership of the job so the new user owns it. However, it may be unwise to let non-user applications have control of the user's display...or to let users have control of non-userspace applications (through an inappropriate CTRL+C, for example).

Since you want to autostart a user-interactive window, let's assume that it's an application chooser in an X environment. I think that should run in userspace, not root or a system-user, and Startup Applications is the right way to go.

---

### Post by Tornikee on 2013-12-09
> **rihikz said:**
> If you are using Ubuntu,
search for 'Startup Applications' in the dash. Open up the first result and add an application. **The 'command' box is basically a terminal command**.
I was wondering how I could find that terminal command for a specific application. I would like to add Transmission torrent client to the startup, what will its command be?

---

### Post by ian-weisser on 2013-12-09
You should open a new thread for that. Transmission is more than one program, so the answer would depend on your intent.

---

