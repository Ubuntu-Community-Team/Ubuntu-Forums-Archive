---
title: "notify-send"
date: 2021-12-31
forum: New to Ubuntu
---

### Post by rburkartjo on 2021-12-31
running 20.04
trying to get notify send not to time out
the below times out after a few seconds
no matter where i put the -t and input time doesnt help

#!/bin/bash
notify-send  "remember system suspend 23:00" -t -5
tks

---

### Post by deadflowr on 2021-12-31
Looking at the man page for it in Ubuntu it says this
>  (Ubuntu's Notify OSD and GNOME Shell both ignore this parameter.)

Not sure what to do about that.
There is a rather long bug report discussion about it here: [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508")

---

### Post by Holger_Gehrke on 2021-12-31
Here a not all that helpful quote from the manual:
> 
-t, --expire-time=TIME
              The duration, in milliseconds, for the notification to appear on screen.  **(Ubuntu's Notify OSD and GNOME Shell both ignore this parameter.)**

You could try setting the urgency of the message to critical ('-u critical'), the spec for desktop notifications says those should **not** time out.

Holger

---

### Post by rburkartjo on 2021-12-31
tks guys
hol here is how i got it to work

#!/bin/bash
notify-send -u critical "remember system shutdown 23:00" && pkill xfce4-terminal

note i had to use the pkill option because if not the terminal also stays open

---

