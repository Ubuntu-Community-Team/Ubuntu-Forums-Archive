---
title: "Mouse not working after minutes"
date: 2021-08-11
forum: New to Ubuntu
---

### Post by dimaspaf14 on 2021-08-11
Soo I've succesfully install, run, & update xubuntu 20.04, this error came when i leave my laptop in a minutes, when i came back to learn xubuntu, my keyboard doesnt recognize anything i type, the mouse can move but same as my keyboard, what happen?, any help?

---

### Post by Impavidus on 2021-08-12
In the past there have been some bugs on Xubuntu with similar effect, but as you installed all updates, that shouldn't be your problem. Any chance this happens after the timer for screensaver/blank screen/lock session expires? Changing that timer may be a workaround.

A few things you could try:
Can you switch to the TTY with ctrl+alt+F1 through ctrl+alt+F7? One of those is the GUI session, the others have a command line login. Maybe switching from one to the other and back works.
If you can login on a TTY, maybe you can fix the problem there. But I wouldn't know how. Maybe somebody has an idea. In any case, you can reboot from the TTY by running the reboot command.
If you even can't get to the TTY, try rebooting with REISUB. alt+SysRq+r, alt+SysRq+e, alt+SysRq+i, etc., pressed in sequence with a few seconds interval. If you don't use a qwerty keyboard, use the keys where those letters would have been if it were a qwerty keyboard. If the SysRq key isn't marked on your keyboard, it's probably the same as PrintScreen.
In any case, avoid hitting the power button. That tends to cause filesystem corruption.

---

