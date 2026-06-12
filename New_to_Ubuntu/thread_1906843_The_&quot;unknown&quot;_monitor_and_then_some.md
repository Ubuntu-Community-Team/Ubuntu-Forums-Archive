---
title: "The &quot;unknown&quot; monitor and then some"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by swhitey91 on 2012-01-10
I literally just found out about ubuntu today, installed, it a few hours ago, and have been doing nothing but trying set it up since. It's installed on an ASUS G60Vx notebook, with an NVIDIA GTX 260M graphics card. While i was fixing the audio problem, it popped up asking me to install the driver for the graphics card. i installed it without thinking anything of it and restarted my computer after the audio was fixed. After i restarted it, The Vizio tv i have hooked up as an external monitor was no longer recognized by the computer, and I've got the "unknown" monitor ordeal going on. I've been looking everywhere for a fix on here, and tried a few, but nothing has fixed it. If i could get any help, it'd be appreciated, but it may have to be dumbed down quite a bit. Haha. If I need to give more information, let me know

---

### Post by TeoBigusGeekus on 2012-01-10
After installing the restricted nvidia drivers, open a terminal and give
```
gksu nvidia-settings
```
Try to fix things from there - don't forget to save changes to X configuration file after you're done.

---

### Post by swhitey91 on 2012-01-10
Alright, well i reinstalled the driver and typed in what you said, but it gave me this:

(gksu:1935): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by swhitey91 on 2012-01-10
I looked around and saw a website say to put this in if that happened:

[FONT=Courier New]sudo apt-get install gtk2-engines-pixbuf

I did and now when i put in what you said, it pauses for a few seconds, and then gives me the input line again, but nothing else
[/FONT]

---

### Post by TeoBigusGeekus on 2012-01-10
Reboot and try again.

---

### Post by amitsarkar321 on 2012-01-10
new reply

---

### Post by swhitey91 on 2012-01-10
well, It just did the same thing. Pause for a few seconds, then input line again.

---

### Post by swhitey91 on 2012-01-10
I actually found the application in the Dash home, but even trying to open it that way doesn't work. It says it's loading, then nothing happens.

---

