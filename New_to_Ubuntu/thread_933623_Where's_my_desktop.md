---
title: "Where's my desktop?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by fallenstar on 2008-09-29
:KS
err, help! I'm using suse 11.0 with gnome, which i love, but want ubuntu studio for the music production. I just installed it (as dual boot with suse, my house is a windows-free-zone), but instead of a desktop, my whole monitor has turned into a console! I'm really not that hot at using console to achieve anything and want a desktop environment!

I assume that somehow I've only loaded the kernel and not the GUI, any ideas how I managed it and how I can fix it? I don't see the point in reinstalling only to make the same mistake again!

And yes, I feel a bit silly...

Thanks x:confused:

---

### Post by starcannon on 2008-09-29
did you share /home with both operating systems?
have you tried restarting gdm to get a look at the error messages?
be sure to look at /var/log/syslog might be a juicy hint in that log as to whats not working.
have a peak at dmesg as well. Thats where I'd start, post those outputs as well.

GL

---

### Post by LowSky on 2008-09-29
if you loading to a CLI try typing **startx** at the prompt

---

### Post by fallenstar on 2008-09-30
Hey, I couldn't give any outputs as it had taken over my whole computer, and thus not copy and paste-able, but I reinstalled and realised I hadn't selected to install ubuntu desktop environment, as i had pressed enter on it instead of space to select, and enter to accept. So i had managed to load only the kernel and nothing else!

All working spiffingly now, thanks for your time and sorry for being daft!

---

