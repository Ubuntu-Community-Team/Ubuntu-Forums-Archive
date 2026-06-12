---
title: "Locked terminal"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by tooloose on 2012-09-30
I have locked a terminal in the upper left hand corner of my screen.  I can still see the log on page, cannot control the
terminal.  Terminal only returns error messages.  Any help will
be greatly appreciated.

TIA

tooloose

---

### Post by daslinkard on 2012-09-30
> **tooloose said:**
> I have locked a terminal in the upper left hand corner of my screen.  I can still see the log on page, cannot control the
terminal.  Terminal only returns error messages.  Any help will
be greatly appreciated.

TIA

tooloosePress "Ctrl-D" or type "exit" to exit the shell. This will also close the terminal window.  Let me know if that fixes it for you.

---

### Post by tooloose on 2012-09-30
Crtl-D brought me back to the logon page, but when I login...
same problem.  I cannot move the terminal, and it renders my
login useless.

Apparently I have lost internet connection, because using terminal
to add packages gives me this error.."E: Unable to locate package upgrade", or whatever else I try to install.

I appreciate your time, and helping me with this problem.

TIA

tooloose

---

### Post by Pletched on 2012-09-30
I think it would help if you reply with the error messages.

---

### Post by houseworkshy on 2012-09-30
I don't know what you did but it sounds like the problem is due to permissions.  So try the exit command with a sudo in front of it; "sudo exit".  You'll be asked for your password, because the sudo will give you root powers for 15 minets and is therefore an admin action,  and it should close.  If that doesn't work then posting the errors would be useful.

---

### Post by tooloose on 2012-10-01
Thank you all for your help.  Believe it or not I had the login

box checked in the wrong mode.

Thanks again.

tooloose

---

### Post by daslinkard on 2012-10-01
Sweet!  Let's mark this as solved!

---

