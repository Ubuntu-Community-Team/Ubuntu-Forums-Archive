---
title: "A bash daemon script problem"
date: 2007-05-24
forum: Programming Talk
---

### Post by stee on 2007-05-24
I have a usb headset and an internal soundcard. I want to have a daemon-like program that monitors whether or not the headset is plugged in. I tried to do it in bash, and kinda got it to work. This is the simple code:

```

#! /bin/bash

defcard=0

while [ "true" ]
do
        if [ "$defcard" -eq 0 ]
        then
                if [ `aplay -l | grep USB | wc -l` -gt 0 ]
                then
                        echo "USB soundcard was found"
                        echo "Setting default soundcard to USB"
                        asoundconf set-default-card 1
                        defcard=1
                fi
        elif [ "$defcard" -eq 1 ]
        then
                if [ `aplay -l | grep USB | wc -l` -eq 0 ]
                then
                        echo "USB soundcard was not found"
                        echo "Setting default soundcard to internal"
                        asoundconf set-default-card 0
                        defcard=0
                fi
        fi
        sleep 1
done

```

This works, but if I put it in my /etc/init.d/ and a symbolic link in /etc/rc.2/, the booting process stops and waits for the while to finish. Obviously, I guess. 

I can start it with **start-stop-daemon --start --exec myscript -b ** in a terminal and it works just the way I want it... but how do I get it to start at boot like this? 

So what can I do? Is this code way too naive?

---

### Post by cwaldbieser on 2007-05-24
Put an entry in your /etc/inittab:
```

xy:12345:respawn:/path/to/your/script

```
The "xy" code is arbitrary.  Just pick some 2 leeter code that doesn't exist already.
The 12345 are runlevels.  The respawn tells init to rerun the script if it dies for some reason.
To tell init to re-read the config file:
```

$ sudo kill -HUP 1

```
See "man inittab" for more details.

---

### Post by stee on 2007-05-24
Thanks. It didn't work, however. My inittab was empty.

---

### Post by ruy_lopez on 2007-05-24
You probably should use absolute pathnames, or export the pathnames for the commands you use into the PATH variable at the top of the script. And why is it sleeping? It might have a better chance of working if you execute the script with rc.local.

---

### Post by stee on 2007-05-24
> **ruy_lopez said:**
> You probably should use absolute pathnames, or export the pathnames for the commands you use into the PATH variable at the top of the script. And why is it sleeping? It might have a better chance of working if you execute the script with rc.local.

rc.local did the trick! thanks!
i put "start-stop-daemon --start --exec myscript -b" in there and now everything is super.

---

### Post by kobewan on 2007-05-24
This "inittab" thing intrigues me. There is a program I use, xbindkeys, which already has a daemon mode. However, every so often it segfaults and I have to restart it manually. Will I be able to set it in inittab so that it will restart if it quits by itself?

---

### Post by cwaldbieser on 2007-05-26
> **kobewan said:**
> This "inittab" thing intrigues me. There is a program I use, xbindkeys, which already has a daemon mode. However, every so often it segfaults and I have to restart it manually. Will I be able to set it in inittab so that it will restart if it quits by itself?
Yes.  I actually got the idea from Tip #4 of OReilly's "Linux Server Hacks".  The init process can monitor any process and restart it with the respawn option if it detects it failed.

---

### Post by kobewan on 2007-05-27
I don't have an /etc/inittab file, and "man inittab" returns "No manual entry for inittab". I'm going to try it anyways and hope it works, but why would I be missing the man page?

---

### Post by cwaldbieser on 2007-05-29
> **kobewan said:**
> I don't have an /etc/inittab file, and "man inittab" returns "No manual entry for inittab". I'm going to try it anyways and hope it works, but why would I be missing the man page?

I'm not sure why.  I run Dapper, so I am not sure if something was changed in Edgy or Fiesty.  Try:

```

$ ps aux | awk '$2 == "1" {print $0;}'

```
That should show you the process with ID 1.  If it isn't "init", maybe it is something like "initng" or something similar.  In that case, there may be something similar that the "init" replacement can do.

---

### Post by blazoner on 2007-06-10
Actually, in 6.10 and up, the inittab stuff has been replaced by upstart.
[From the upstart overview page:]("http://upstart.ubuntu.com/")
> Feature Highlights

    * Tasks and Services are started and stopped by events
    * Events are generated as tasks and services are started and stopped
    * Events may be received from any other process on the system
    * Services may be respawned if they die unexpectedly
    * Bi-directional communication with init daemon to discover which jobs are running, why jobs failed, etc.

Planned Features

    * Events generated at timed intervals or scheduled times
    * Events generated as files or directories are changed
    * Supervision and respawning of daemons which separate from their parent process
    * User services, which users can start and stop themselves
    * Communication with the init daemon over DBUS

Looks like about the best time to learn the new process.  Hope this helps!

---

