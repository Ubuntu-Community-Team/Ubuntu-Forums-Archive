---
title: "Oneic doen1t start after update"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by daleybortolon on 2011-10-21
After last night's updates (198 updates I think) were installed and the computer rebooted, my oneiric started without any nvidia drivers. I've installed the first one on the list (it wouldn't install the updates or de more recent ones) and now my computer won't start. I shows the grub but goes to dos and just won't start!
Can anybody help me please?

---

### Post by computerandu on 2011-10-21
I am not sure but this might help you:

[http://www.computerandyou.net/2011/10/18/how-to-solve-unable-to-login-into-ubuntu-11-10/](http://www.computerandyou.net/2011/10/18/how-to-solve-unable-to-login-into-ubuntu-11-10/)

---

### Post by kaldor on 2011-10-21
Try selecting an older kernel (if available) in GRUB. 

If that doesn't boot either, then maybe removing the NVIDIA drivers and reverting to the default Nouveau driver would be a good idea. That way you can start from scratch.

---

### Post by drs305 on 2011-10-21
Try starting with the 'nomodeset' option and if it boots install a different video driver.
[LIST]
[*]At the Grub menu, press 'e' to edit the highlighted menuentry.
[*]Cursor to the end of the 'linux' line.
[*]Delete the 'quiet splash' options and add 'nomodeset'
[*]Press CTRL-x to boot.
[/LIST]

If it gets to the Desktop, add a different video driver and see if the issue is solved.

---

