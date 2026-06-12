---
title: "[SOLVED] Having trouble setting resolution"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by jasontu on 2008-08-25
Having trouble setting resolution

I was recently given a very nice 32" LCDTV with a native resolution of 1366x768.  Linux doesn't seem to recognize the brand, Winbook, but it is recognizing it as a Tutung which I believe is probably the same thing.  

It displays fine in both 1280x768 and 1366x768 resolutions, but it will not keep the settings after a reboot when I set it to 1366x768.  Furthermore, I can only get to 1366x768 through sudo nvidia-settings.  After a reboot though it is back to 1280x768.

The gksu displayconfig-gtk utility does not give me an option of 1366x768.

Any suggestions?

---

### Post by bawilson2 on 2008-08-25
Sorry if this is too simple of a suggestion but after you set the resolution to 1366x768 do you tell the nvidia-settings to "Save to X Configuration File"?  If you don't do that it shouldn't remain after rebooting.

---

### Post by wolfen69 on 2008-08-25
try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then do ctrl-alt-bksp to restart x.

---

### Post by jasontu on 2008-08-25
I did save the nvidia-settings, but there have been times when I had similar problems because I didn't.  It was definitely a worthwhile suggestion in my case.

---

### Post by bawilson2 on 2008-08-25
Why don't you try posting your /etc/X11/xorg.conf file.  I'm not an expert at this by any means but I've had to fight through a few problems hooking up different displays.

---

### Post by jasontu on 2008-08-26
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This worked.  After I ran this I just reinstalled the nVidia driver via EnvyNG.

Thanks

---

