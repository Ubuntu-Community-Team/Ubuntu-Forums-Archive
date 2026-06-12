---
title: "Updating wrecked resolution options"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by krappenfest on 2008-05-16
My system worked perfectly, then on May 12th I did an update and my resolution is stuck at 640x480.  When I go to change the resolution through system-->preferences the only option is 640x480.

I searched the forums and downloaded Envy. My drivers work fine because I can run Compiz Fusion effects, which by the way look awesome at 640x480 resolution. :)

Anybody have an idea how to fix this?  I am a n00b with ubuntu, so go easy on me.

---

### Post by shifty_powers on 2008-05-16
```
gksudo gedit /etc/X11/xorg.conf
```

and post the contents please ;)

---

### Post by skyjacker on 2008-05-16
> **krappenfest said:**
> My system worked perfectly, then on May 12th I did an update and my resolution is stuck at 640x480.  When I go to change the resolution through system-->preferences the only option is 640x480.

I searched the forums and downloaded Envy. My drivers work fine because I can run Compiz Fusion effects, which by the way look awesome at 640x480 resolution. :)

Anybody have an idea how to fix this?  I am a n00b with ubuntu, so go easy on me. Restart the computer and choose "Recovery Mode" in the Grub menu. Type the following:
1) ```
sudo dkg-reconfigure xserver-xorg
```
Select the "vesa driver, and press enter whenever you don't know the answer to a question.
At the end of the screens type "reboot, and press enter.

when Ubunte comes up, you should be able to choose the correct resolution from the preferences menu... Good luck, let us know if this helps.:)

---

### Post by dstew on 2008-05-16
For Hardy, to reconfigure the xserver, the command is now **xfix**. You can get it from the Recovery Mode boot option (grub menu).

---

