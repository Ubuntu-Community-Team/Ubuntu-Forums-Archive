---
title: "Oops... accidentally removed NVIDIA from startup applications"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by squiddy2 on 2013-08-09
I just installed Gnome 3 on Ubuntu 12.04. I was playing around with the startup applications preferences and accidentally removed the only one that was on the menu. I didn't get a good look at the name but it was called NVIDIA something. I'm assuming it's important since it was the only one that was built in!! Any ideas on how I can get it back?

---

### Post by deadflowr on 2013-08-09
If I'm not mistaken the nvidia program on start up is
NVIDIA X Server Settings

and the command is 
```
sh -c '/usr/bin/nvidia-settings --load-config-only'
```
and the comment is
Configure NVIDIA X Server Settings

Open the start-up applications program and add these to a new one.

---

### Post by squiddy2 on 2013-08-09
Excellent, thank you!

---

### Post by deadflowr on 2013-08-09
Looking over this again, I believe the file for it is a system file.
The start-up applications program makes start up programs run per user.
If you want, or need, to move the associated file from the users folder into the system folder.
first
```
ls ~/.config/autostart
```
and locate the name of the nvidia file.
(Should be something like "nvidia-autostart.desktop")
Then run
```
sudo mv /home/user/.config/autostart/the-nvidia-filename /etc/xdg/autostart
```

This should move the file for system-wide use.

---

