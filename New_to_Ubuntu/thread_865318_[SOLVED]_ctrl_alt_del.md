---
title: "[SOLVED] ctrl alt del"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by SOME1ELSE1999 on 2008-07-20
does ubuntu have a equivalent to ctrl alt del

---

### Post by ConMan318 on 2008-07-20
If you want a list of running processes, you could go to System > Administration > System Monitor > Processes tab.  I'm sure you could set a keyboard shortcut for that; if you add the system monitor applet to a panel you could just click on that to open it up.

---

### Post by lukjad on 2008-07-20
Yes. Ctrl+Alt+Backspace to restart GNOME.

---

### Post by SOME1ELSE1999 on 2008-07-20
thank you for that, thats helpfull. i guess i should have been a little more specific i have managed to lock up ubuntu 3 times now is there a way to restart the comp / pull up the power down menu?    or is there already a shortcut for this?

---

### Post by lukjad on 2008-07-20
The Ctrl+Alt+Backspace will put you back at the login screen. From there you can login again or shutdown, reboot, etc.

---

### Post by SOME1ELSE1999 on 2008-07-20
thank you works great

---

### Post by lukjad on 2008-07-20
Great!
Glad it helped.
PS Please thread mark solved.

---

### Post by YaroMan86 on 2008-07-20
> **SOME1ELSE1999 said:**
> thank you for that, thats helpfull. i guess i should have been a little more specific i have managed to lock up ubuntu 3 times now is there a way to restart the comp / pull up the power down menu?    or is there already a shortcut for this?

Well, it's usually good to do a rising system of how to deal with it.

1. Try to force quit the misbehaving application. There's a GNOME panel applet that allows you to do this. If GNOME isn't responding....

2. Press CTRL + ALT + F1. If it goes to the text-only TTY1, log in and use ps -e to find the offending process, then use the kill command with the PID of the offending process. If that fails or you don't switch to TTY1.

3. CTRL + ALT + BACKSPACE when back on GNOME. This will restart X, hopefully. If that doesn't work.

4. You'll need to raise elephants. ALT + PRT SCR + R, E, I, S, U, B. This is the emergency reboot procedure. It is a way to allow behaving apps to shut down gracefully, then terminate the frozen apps, emergency sync the file systems, then remount them read only, then restart the computer.

One thing I like to do is run problematic apps from the terminal. That way, two things can happen when the application goes loco: I can often get a printout of what the application was doing, and I can CTRL + C to break the application and get things going again.

---

### Post by tjwoosta on 2008-07-20
regular old ctrl-alt-delete  will work also   (it brings up the shutdown menu)


also when my computer freezes i can just push ctrl-alt-delete and it will just reboot the computer rather then bringing up the menu (i dont know why but im not complaining cuz it works)

---

