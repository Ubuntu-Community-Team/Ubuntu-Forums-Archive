---
title: "Desktop computer icon won't work."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by powerpleb on 2008-05-28
When I click on the computer icon on my desktop it doesn't work and gives me this error:
> Couldn't display "computer:///"
There is no application installed for this file type
Any ideas?

I'm running Gnome on Hardy.

---

### Post by sayakb on 2008-05-28
Did you recently disable any startup service from the Sessions/Services?

---

### Post by RSingh on 2008-05-28
i just would like to ask, did you create this Icon manually or enable it from Gconf.

I myself enabled these icons on the desktop from gconf and had no problems:

Open Terminal and type:

gconf-editor

Open Apps>>Nautilus>>Deskstop

Tick the respective icons you want to display on the desktop.

---

### Post by powerpleb on 2008-05-28
> **LinuxIsInnovation said:**
> Did you recently disable any startup service from the Sessions/Services?

No I didn't. The most recent thing I did was attempt to move my /home dir to a new partition. So I renamed /home to /home.bk, when it didn't work I changed it back to /home and everything else is hunky dory.

---

### Post by powerpleb on 2008-05-28
> **RSingh said:**
> i just would like to ask, did you create this Icon manually or enable it from Gconf.

I myself enabled these icons on the desktop from gconf and had no problems:

Open Terminal and type:

gconf-editor

Open Apps>>Nautilus>>Deskstop

Tick the respective icons you want to display on the desktop.

I think it was there when I installed Hardy. I definitely didn't put it there.
I've just had a look at gconf. Disabled and re-enabled, no change.

---

### Post by sayakb on 2008-05-28
Well, this shouldn't cause this kind of problem. Do you get the same error when you press the "Computer" from the Nautilus toolbar?

---

### Post by powerpleb on 2008-05-28
> **LinuxIsInnovation said:**
> Well, this shouldn't cause this kind of problem. Do you get the same error when you press the "Computer" from the Nautilus toolbar?

Yes, but I get more info: 
> Couldn't display "computer:///".
Error: DBus error org.freedesktop.DBus.Error.ServiceUnknown: The name :1.38 was not provided by any .service files
Please select another viewer and try again.

---

### Post by sayakb on 2008-05-28
Open terminal and type:
```
dbus-daemon &
```
And try again..

---

### Post by powerpleb on 2008-05-28
Didn't work. This is the output in the terminal...
> andrew@andrew-desktop:~$ dbus-daemon &
[1] 7199
No configuration file specified.
dbus-daemon [--version] [--session] [--system] [--config-file=FILE] [--print-address[=DESCRIPTOR]] [--print-pid[=DESCRIPTOR]] [--fork] [--nofork] [--introspect]
andrew@andrew-desktop:~$ 

Do I need to sudo this?

---

### Post by powerpleb on 2008-05-28
I tried it with sudo:
> :~$ sudo dbus-daemon &
[2] 7203
[1]   Exit 1                  dbus-daemon

But still the same error when I try to open 'Computer'

---

### Post by sayakb on 2008-05-28
OK, goto System->Administration->Services and press Unlock. Now scroll down and check "System Communication Bus (dbus)"

---

### Post by powerpleb on 2008-05-28
> **LinuxIsInnovation said:**
> OK, goto System->Administration->Services and press Unlock. Now scroll down and check "System Communication Bus (dbus)"

I did that but it was already checked.

---

### Post by sayakb on 2008-05-28
Sorry but I couldn't think of anything else. This problem generally arises when you use different Window managers (like openbox) with Nautilus, and naturally, you don't have dbus loaded. Maybe somebody else would find a solution. Though I shall try to find a way out. :)

EDIT: [https://bugs.launchpad.net/ubuntu/+source/enlightenment/+bug/235348](https://bugs.launchpad.net/ubuntu/+source/enlightenment/+bug/235348)
Here is the link to a bug to a similar problem you mentioned. But you say that you're using Gnome. So such problem is very unlikely unless you play around with the system files.

---

### Post by powerpleb on 2008-05-28
> **LinuxIsInnovation said:**
> Sorry but I couldn't think of anything else. This problem generally arises when you use different Window managers (like openbox) with Nautilus, and naturally, you don't have dbus loaded.

Aahh, I have been using openbox and gone back into gnome.

---

### Post by sayakb on 2008-05-28
With openbox, you might try [ROX-Filer]("http://ubuntuforums.org/rox.sourceforge.net/") for desktop icons and Nautilus for navigation :)

---

### Post by powerpleb on 2008-05-28
OK, I rebooted and problem went away. I guess I'll steer clear of Openbox on this machine in the future. I prefer fluxbox or IceWM anyway.

---

### Post by sayakb on 2008-05-28
Do take a look at [Enlightment]("http://timony.com/mickzblog/2008/04/15/e17-on-ubuntu-revisited/").

---

