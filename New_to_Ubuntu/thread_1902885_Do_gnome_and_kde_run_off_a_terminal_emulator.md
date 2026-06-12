---
title: "Do gnome and kde run off a terminal emulator?"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by venom104 on 2012-01-01
I've been curious about this for a while. When I installed arch-linux I had to screw around with the .xinitrc file and include a line with exec to get gnome to run automatically. Does ubuntu work the same way? I guess what I'm asking is behind the desktop manager is there some terminal session running everything? Can I kill that terminal session, if I kill that terminal session, will it kill all child processes?

---

### Post by ubudog on 2012-01-01
The system starts different things when it starts up, and no, these aren't running off a terminal emulator, rather the Linux system.  You can kill certain programs.  To see programs running, either open the System Monitor, or type: 

```
top
``` <enter>

Into a terminal.

In top, it will show you the PID.  To kill a certain PID, you would run:
kill PIDNUMBER

But be careful what you kill, as some things running are important to your system.  

:)

---

### Post by The Cog on 2012-01-01
Another interesting tool is pstree.

As ubdog says, the Linux system is all started by scripts, although they are not strictly terminal sessions as there is not a terminal attached to these scripts, they are just running in the background. The very first script to run is init (pid 1), and it is init's job to start everything else.

Killing any process will (in general) kill all their child processes, although it is possible for a process to disown its children so this doesn't happen. Killing init is not a good idea.

Edit:
Actually, I think that init is a compiled program and not a script.

---

### Post by mcduck on 2012-01-01
> **venom104 said:**
> I've been curious about this for a while. When I installed arch-linux I had to screw around with the .xinitrc file and include a line with exec to get gnome to run automatically. Does ubuntu work the same way? I guess what I'm asking is behind the desktop manager is there some terminal session running everything? Can I kill that terminal session, if I kill that terminal session, will it kill all child processes?

In a way, yes. X runs on a virtual console, and if you use the magic key to kill the current virtual console (SysRq + k) while in the desktop all the programs will be killed and X will restart, throwing you back to the login screen.

---

