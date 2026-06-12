---
title: "black screen only !"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by melrokz on 2008-10-17
Alas! My login screen does not appear, and if it does, after logging in only a black screen appears. What shall I do?

---

### Post by stephanvaningen on 2008-10-17
Maybe start with diagnosis:
[LIST]
[*]Press Ctrl-Alt-F1
[*]Login with the userid and password
[*]run command:  dmesg | tail
[*]see if any screen/X/monitor-related messages appear in the result of the command
[/LIST]
Is it after a clean-install of an Ubuntu machine, or did it now happen after using it a while? Or did it happen after an upgrade, or after playing around with configuration settings?
--
If after clean install, you can re-do the clean install of-course (unless it was automatically like this without changing anything).
--
You can try to re-install the desktop maybe (?) anyone else a better solution?
--

---

### Post by AndyCooll on 2008-10-17
By "black screen" do you mean you end up at a commandline, or that a gui login appears and it thens up going black in colour?

:cool:

---

### Post by Paul41 on 2008-10-17
It could be the video drivers. Along the lines of the other two posts it depends on when it started and if anything has changed to know where to start looking.

---

