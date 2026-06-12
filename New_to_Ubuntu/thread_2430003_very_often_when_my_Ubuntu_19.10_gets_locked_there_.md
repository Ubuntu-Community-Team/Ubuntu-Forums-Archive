---
title: "very often when my Ubuntu 19.10 gets locked there are problems with a freezing screen"
date: 2019-10-26
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2019-10-26
so when i go away the screen gets locked after a bit.
then it is often freezes and often won't return to work back until after a reboot.

do you know this problem?

Thanks!!!

---

### Post by dino99 on 2019-10-26
gnome/kde//else ?  which video driver ? X/wayland ?

---

### Post by ronjjjg8885 on 2019-10-26
ill check later

---

### Post by Impavidus on 2019-10-26
There are quite a few things to try between getting a black screen and hitting the power button. What have you tried? What did work?

---

### Post by ronjjjg8885 on 2019-10-27
how to check? - i've the default environment and don't know how to determine the video driver.

---

### Post by ronjjjg8885 on 2019-10-27
both shutting down with the power botton if rebooting with the reboot button

---

### Post by Impavidus on 2019-10-28
Some workarounds that may help:
- Try switching to a different console, then swithing back to the GUI. Use ctrl+alt+F1 ... ctrl+alt+F7. Sometimes this fixes a black sceen issue.
- Try logging in on one of the consoles. You may be able to restore the GUI from there, but I don't know the commands to try. Or use it to reboot.
- Reboot using SysRq+REISUB.

Rebooting using the power button will cause file system damage.

---

### Post by ronjjjg8885 on 2019-10-31
hi
what is "consoles"?
how does pressing ctrl+alt+f1/f7 helps?

sorry but ireally not sure what do you mean...

by the way i'm using the power button on the pc only when it is already stuck.

sometimes it freezes when i can see the desktop and hear music with the system...

i will glad if you clarify the things that you said......
is there anything else that may help?

the laptop is doing fine. it is only the desktop computer...

---

### Post by Impavidus on 2019-10-31
You typically have about 7 user interfaces on a Linux system, which we casually call consoles. I'm not sure of any official name. You can switch between them with ctrl+alt+F1-F7. One of them (here number 7, but this might have changed) runs the graphical interface, but you can use a command line interface on the others. Switching from the graphical interface to the command line interface and back sometimes helps to refresh the graphics. If you can login on the command line interface, you can run commands, like a clean reboot. As a last resort, try SysRq. Slowly hit```
alt+SysRq+r (set keyboard to raw mode)
alt+SysRq+e (kindly ask all applications to terminate, allowing them to make emergency backups)
alt+SysRq+i (kill remaining applications)
alt+SysRq+s (sync, write all changes to the hard drive)
alt+SysRq+u (unmount, remounts the file systems read-only)
alt+SysRq+b (reboot)
```Actually, not all of these functions are enabled on Ubuntu as they can be a security risk, but the important ones are.

When the computer appears to be stuck, it may be that only the graphics are stuck, but everything else is still running fine.

You could also dig into the log files. They are in /var/log/. Maybe you can find a clue at the time when the problem occured. Maybe not.

---

### Post by ronjjjg8885 on 2019-11-02
hi thanks, i didn't understood that much

ok,
but when i press the alt+sysrq commands nothing happens

when you talk about consoles you do mean the other 'desktops' that i can switch to?

edit: i've found out that you mean something else and you don't talk about workspaces

---

