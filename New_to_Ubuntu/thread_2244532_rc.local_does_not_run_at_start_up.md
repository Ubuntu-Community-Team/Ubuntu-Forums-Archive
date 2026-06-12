---
title: "rc.local does not run at start up"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by son4 on 2014-09-17
Hi all, 
I want to start my Java application at start up, so I put my command in rc.local file.
Here is rc.local file: 
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

bash /home/tc/deploy/tc-client-ui/start.sh

exit 0

```

And my start.sh is run as normal, of course, that means no problem with start.sh file.

I've already checked the rc.local by command: 
```

sudo /etc/init.d/rc.local start

```
And my program run normally. But when my computer restarts it doesn't run automatically. I think that because rc.local isn't run at start up.
Anybody can help me? 
I used : Ubuntu 14.04 32 bits

---

### Post by steeldriver on 2014-09-17
Hello and welcome to the forums

I think it's more likely that tc-client-ui relies on some environment or service that's not available at the point that re.local is run (such as the X server - is it a GUI application by any chance?)

If you are trying to autorun a GUI/desktop application then the proper place for it is your session's 'Startup Applications' I think

---

### Post by rolkin on 2014-09-17
Does this actually need to run at startup? I'd venture to say that this can be set to automatically run when logging into your desktop environment.

---

### Post by son4 on 2014-09-24
Yes! Exactly as you think. My application is GUI Application. 
What do you mean by "t[COLOR=#000000]he proper place for it is your session's 'Startup Applications' " ?I
[/COLOR]I tried this by "Startup Application" app provided in Ubuntu, but it doesn't work as well. My application display for a few seconds, then auto closed. 
I don't know why. I run program by execute sh file via terminal with no problem. 
Any idea?

---

### Post by son4 on 2014-09-24
> **steeldriver said:**
> Hello and welcome to the forums

I think it's more likely that tc-client-ui relies on some environment or service that's not available at the point that re.local is run (such as the X server - is it a GUI application by any chance?)

If you are trying to autorun a GUI/desktop application then the proper place for it is your session's 'Startup Applications' I think

[COLOR=#000000]Yes! Exactly as you think. My application is GUI Application. [/COLOR]
[COLOR=#000000]What do you mean by "t[/COLOR][COLOR=#000000][COLOR=#000000]he proper place for it is your session's 'Startup Applications' " ?I
[/COLOR][/COLOR][COLOR=#000000]I tried this by "Startup Application" app provided in Ubuntu, but it doesn't work as well. My application display for a few seconds, then auto closed. [/COLOR]
[COLOR=#000000]I don't know why. I run program by execute sh file via terminal with no problem. [/COLOR]
[COLOR=#000000]Any idea?[/COLOR]

---

### Post by son4 on 2014-09-24
> **rolkin said:**
> Does this actually need to run at startup? I'd venture to say that this can be set to automatically run when logging into your desktop environment.

This requirement is from customer. They want my application auto start when they startup ubuntu. 

And more, when I set the sh file as executeable, then double click this file, my program display for a few second, then auto closed. 
Do you have any idea? This sh file is run as normal if I run via terminal!

---

### Post by son4 on 2014-09-25
anybody here please help me.
I stuck for that problem for a week :(

---

### Post by ian-weisser on 2014-09-25
You CAN'T run a process that requires a display before login. It will fail; the displays are not assigned until after login.


The difference between rc.local (pre-login) and Startup Applications (post-login) is *huge*.

1) The startup environment is intended for headless, displayless, processes. Think cron or mountall or dbus or the network-manager-daemon.
2) lightdm runs in this environment, finds a display (low-level, not an X display; X isn't running yet), and creates the GUI login window.
3) Then the user logs in graphically.
4) After login, lightdm starts the X server, X creates and assigns the displays, then the GUI environment starts.
5) Finally, GUI Startup Applications run. 

If you boot the system, but then run off to the bathroom before logging in, your system is running. Cron is running, the network is running, services are running. But no GUI applications can run until after you return and login - X isn't running yet.

So, if Network Manager is a headless process, why do I have an icon for it on my GUI desktop?
The user-interface is a different process. NM-daemon and the user-interface communicate using dbus.
NM-daemon starts during 1). NM-icon starts during 5).

I think you have a couple options:

a) You can get the customer to change the 'startup' requirement to 'login.' Perhaps they don't understand the difference. Or simply used the wrong term. Do they really want the application to run unattended as a system user (instead of a logged-in user)? 

b) You can separate your core and interface processes the same way NM (and others) do. It's not too hard. They can communicate using sockets or dbus (which also uses sockets). One advantage is you can then use the same core API for multiple interfaces: web, command line, dbus, etc...if that's useful. The core can be a daemon...or not; both Upstart and systemd have robust ways to spawn child processes (services) that terminate when the connection ends.

---

