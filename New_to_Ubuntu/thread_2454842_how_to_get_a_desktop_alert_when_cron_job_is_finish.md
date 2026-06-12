---
title: "how to get a desktop alert when cron job is finished"
date: 2020-12-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-07
running ubuntu 20.04
what to add to the below cron job

#!/bin/bash
clamscan -r  --stdout  --exclude=/timeshift / > /home/ray/clamscan.log



tks

---

### Post by rburkartjo on 2020-12-07
00 08 07 * * /home/ray/clamscan

---

### Post by ActionParsnip on 2020-12-07
You could use
```

#!/bin/bash
export DISPLAY=:0
clamscan -r --stdout --exclude=/timeshift / > /home/ray/clamscan.log
export notify-send -i /usr/share/doc/clamav-docs/html/UserManual/images/demon.png 'Virus scan complete'

```

---

### Post by ActionParsnip on 2020-12-07
Obviously feel free to use a different image

---

### Post by rburkartjo on 2020-12-08
tks act but doesnt work

---

### Post by ActionParsnip on 2020-12-08
Can you run the command to make the notification show and does it show OK? What desktop session are you using?

---

### Post by Holger_Gehrke on 2020-12-08
In [this thread]("https://ubuntuforums.org/showthread.php?t=2453917") from two weeks ago the same problem was discussed. notify-send does not display anything by itself (and therefore doesn't need the DISPLAY) but uses the session dbus to communicate the notification to a notification daemon. Because of this it actually needs the address of the session bus in the variable DBUS_SESSION_BUS_ADDRESS.

```

#!/bin/bash
export DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
clamscan -r --stdout --exclude=/timeshift / > /home/ray/clamscan.log
notify-send -i /usr/share/doc/clamav-docs/html/UserManual/images/demon.png 'Virus scan complete'

```

Replace the '1000' in the value for DBUS_SESSION_BUS_ADDRESS with your numerical UID as given by the command 'id'.

Holger

---

### Post by rburkartjo on 2020-12-12
this worked for me .
#!/bin/bash
clamscan -r /usr/bin


/usr/bin/env DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus /usr/bin/notify-send 'virus scanning done'

ran as cron job

---

