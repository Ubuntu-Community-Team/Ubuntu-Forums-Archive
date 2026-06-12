---
title: "Gnome trouble"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by telekarlsen on 2008-11-14
I restarted my 8.10 desktop after an update yesterday.

I then realised that I cannot "log into" Gnome, I only read these two messages:
[LIST]
[*]"Could not update ICEauthority file /.ICEauthority" and
[*]"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"
[/LIST]

There seemed to be nothing wrong with neither the file .ICEauthority nor my home folder; I own them both.

In an attempt to "reset" my Ubuntu I probably screwed up big time; I deleted the .xsession-errors and the .ICEauthority files. - Some said they would be re-generated at the next start-up. They didn't... :(
The same two error-messages keep popping up at reboot, though.

However, I am able to log into Ubuntu with a terminal. Obviously.

One more thing: this seems to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215")
- Did this just happen to many Ubuntu-users? Due to an update?
And does anyone know how to fix this problem?

Thank you.

---

### Post by MasterSander on 2008-11-14
Try typing startx when you're in the terminal, and do apt-get update

---

### Post by phidia on 2008-11-14
Enter > sudo chown -Rc your_user_name:your_user_name /home/your_user_name/

*put your actual user name where I've inserted "your_user_name"

---

### Post by telekarlsen on 2008-11-15
Thank you both for your replies.

Startx resulted in this: 

```
xxxxx@ubuntu:/$ startx
xauth:  timeout in locking authority file //.Xauthority
xauth:  timeout in locking authority file //.Xauthority
xauth:  timeout in locking authority file //.Xauthority
xauth:  timeout in locking authority file //.Xauthority

X: user not authorized to run the X server, aborting.
No protocol specified
giving up.
xinit: No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  timeout in locking authority file //.Xauthority
xxxxx@ubuntu:/$
```

Update/upgrade doesn't change my system now, I did that the other day, before I rebooted and faced this problem.

And I did the chown -Rc too yesterday.


Kind of lost a bit of confidence with Ubuntu with this error. WIll try to do a new installation soon if there will be no fix for this.

t

---

### Post by seantron on 2008-11-22
I just did my first Linux/Ubuntu installation and am stuck at this error now.  Has anyone made any headway on this?  I tried the chown thing...no love.

"There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited status 256"

Also how to I kill a gnome session and get back to the login screen(ie is there a ctrl-alt-del)?

---

