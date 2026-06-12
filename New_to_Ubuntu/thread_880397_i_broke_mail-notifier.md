---
title: "i broke mail-notifier"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by phirebug on 2008-08-04
i'm not sure what i did here.  i was trying to get it to open thunderbird instead of evolution and it just disappeared.  when i go to the menu and click on it, it does nothing.  i tried uninstalling it and reinstalling it but nothing changes.  what did i do?

---

### Post by bpowell2005 on 2008-08-05
Did it not shut down properly? Perhaps it's still running, but unresponsive; I hate to suggest a reboot, but that could help. Or, if you know the name of the process (or a part of it) you could go to the terminal and try: ps aux | grep <whatever> (less the brackets)...maybe try "mail" and see if there are any processes running...if so, you can make note of the PID number and kill it.

---

### Post by phirebug on 2008-08-05
well...i feel pretty stupid now.  it runs invisibly in the background.  you can open it through system>preferences.

thanks for the help, guys.  i did learn how to find out which processes are running and to kill them, though.  i'll get the hang of this thing yet.

---

