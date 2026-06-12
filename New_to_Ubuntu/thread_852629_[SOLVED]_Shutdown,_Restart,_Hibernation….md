---
title: "[SOLVED] Shutdown, Restart, Hibernation…"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Gwasanaethau on 2008-07-07
Hi everyone! Quick question:

When you use the 'quit' button in the top-right hand corner, what commands/scripts are run when the shut down/restart/hibernate buttons are pressed?

Cheers!

---

### Post by phidia on 2008-07-07
GUI to terminal: shutdown=sudo halt or sudo shutdown -h now restart=sudo reboot hibernate=sudo /etc/acpi/hibernate.sh
To see what runs (scripts,ect) enter those commands in terminal and watch.

---

### Post by Gwasanaethau on 2008-07-07
That's brilliant, thanks a mill! ;)8)

---

