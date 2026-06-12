---
title: "how to set command to work as ubuntu loads system"
date: 2019-01-12
forum: New to Ubuntu
---

### Post by darzad on 2019-01-12
I was having a problem getting sound from speakers using line in and eventually found a terminal command which solved the problem so my question is can I enter the command in such a way as it will load automatically after I log off or reboot?  -  [COLOR=#242729][FONT=Arial]pactl load-module module-loopback 


[/FONT][/COLOR]

---

### Post by TheFu on 2019-01-12
Normally, sound is tied to a userid session. That means you cannot run the command until after login.  For openbox, there is an autostart file in ~/.config/openbox/autostart.
Just put  **pactl load-module module-loopback**  into that file, assuming you run openbox.
Different DEs or WMs will use different methods, but it is basically the same.  There's a file and just add the commands to it.  Which DE are you running?

Also, with pulseaudio, I've found that creating an entry into this file fixes the crash problem:
~/.config/pulse/client.conf  - this single line:
```
enable-shm = no
```
Add that line, you might have to create the file first, logout and login.  See of sound isn't fine going forward.

---

### Post by &amp;KyT$0P# on 2019-01-12
> **darzad said:**
>  can I enter the command in such a way as it will load automatically after I log off or reboot?  -  [COLOR=#242729][FONT=Arial]pactl load-module module-loopback [/FONT][/COLOR]

Automatically running that command isn't the best way to do what you're trying to do.

Just edit [FONT=Courier New]/etc/pulse/default.pa[/FONT] , add this line on the end -
```
load-module module-loopback
```

On next reboot it should work.

---

