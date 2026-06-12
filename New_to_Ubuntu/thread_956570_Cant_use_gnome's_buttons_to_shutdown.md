---
title: "Cant use gnome's buttons to shutdown"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by SoftTaco on 2008-10-23
I cant use gnome's buttons to shutdown. The little red button in the top left hand corner (by default) brings up the six options  and all but the restart and shut-down work fine (even hibernate). I can shut down using terminal commands (ie sudo reboot). But if i click the shutdown or restart all programs are shutdown and the gnome panels go away but then it just sits there. I can still ssh in or switch to the console using ctrl-alt-F*.

Any ideas?

---

### Post by alphaniner on 2008-10-23
Is this something that has happened since the system was first installed, or something new that just popped up?  If the latter, have you tried reseting with terminal commands, such as 'shutdown -r now' or 'init 6'?

---

### Post by azebuski on 2008-10-23
I have sort of the same problem.  I can shutdown or reboot fine from a terminal window, but if I click on the shutdown button in the panel or choose QUIT from the System Menu it takes from 2 to 4 minutes for the shutdown window to appear (I've timed it with my watch.)
Sometimes the shutdown window appears right away and I have all the options of shutdown, suspend, hibernate, logoff, etc.  Most of the time it takes several minutes for the shutdown window to appear and it only has 2 buttons, shutdown and logoff.
I'm running Hardy on an old PIII 450mhz and I have to use acpi=force as a kernel switch for power management.  Screensavers work fine and the monitor powers off after 30 mins of inactivity just like I set it for.

---

### Post by Tux.Ice on 2008-10-23
Would you be using a laptop? I believe this would be a bug..... Has happened on my laptop for a while.

---

### Post by SoftTaco on 2008-10-23
Its not a laptop

I have no real delay between clicking the button and having the options appear.

And, Yes if I use the terminal I can shutdown useing halt, reboot, shutdown or whatever other command.

Not sure what you mean by 'init6'

---

### Post by SoftTaco on 2008-10-25
Can any one lead me to a log file or something that would give me a clue as to what is happening here?

---

