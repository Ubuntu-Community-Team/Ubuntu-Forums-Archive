---
title: "How to write to the notification applet?"
date: 2010-02-11
forum: Programming Talk
---

### Post by AlexZaim on 2010-02-11
Hello, i want to write text to the notification applet. I want it to show me the text.

I made a small script for loading some driver modules and i want to have some feedback of the results after the execution. I'm using shortcut keys to run them. So, any advices?

---

### Post by tgalati4 on 2010-02-11
#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Booting"  "You'll be up in 3 minutes."
sleep 200
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Alive" "You can login now."
exit 0

---

### Post by AlexZaim on 2010-02-12
That did it. I had to install libnotify-bin . Thanks

---

