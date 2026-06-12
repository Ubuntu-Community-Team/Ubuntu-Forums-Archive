---
title: "Cannot Display This Video Mode"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by DeZal on 2008-07-20
I have just installed ubuntu (partitioned with XP Home), it installed ok and when I loaded for the 1st time a message appeared saying there was 39 updates to install, after installing these I rebooted and now when trying to boot ubuntu I get the message "Cannot Display This Video Mode" and the boot up stops.

I have an Dell Dimension with ATI x300 video card.

Do I need to re-install or is there an easier way to solve this problem.

---

### Post by phidia on 2008-07-20
When you say boot stops-does the system ask you if you want to look at the xorg log or detailed error messages?
You should be able to open a commadline interface by pressing the Alt+Ctrl+F1 (or F2-F7) keys.
Try typing "startx" and note what error messages you get.
If you're not comfortable in commandline you can boot from a livecd and look at the partiton your install is on + copy and paste the etc/X11/xorg.conf file here.

---

### Post by DeZal on 2008-07-20
Thanks for your response phidia.

When the "Cannot Display This Video Mode" appears it doesn't give me any options, the only thing I could do is switch the PC off.

I have gone into the commandline and typed startx and this is what showed:
> 
Server is already active for display 0 if this is no longer running remove /tmp/.X0-lock and start again

invalid MIT-MAGIC-COOKIE-1 keygivingup
Xinit: interrupted system call (errno 4) unable to connect to X server
Xinit: no such process (errno 3) Server error


I typed remove /tmp/X0-lock but it said invalid command.

---

### Post by markbuntu on 2008-07-20
Try this command:

sudo dpkg-reconfigure -phigh xserver-xorg

It will reconfigure the X server.

---

### Post by DeZal on 2008-07-20
Thanks markbuntu, now works perfectly.


Solved

---

