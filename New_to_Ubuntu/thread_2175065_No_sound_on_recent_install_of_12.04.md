---
title: "No sound on recent install of 12.04"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by drrwhistle32 on 2013-09-17
I recently installed 12.04 on 2 Gateway laptops, model M250E.  Neither have sound.  No sound on splash screen or anything else.  Went into system setting - sound and did a speaker test and nothing!  I am almost sure they are not muted, 99%.  Unless there is another way to mute tucked away somewhere.  Did lspci | grep audio and recieved back 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04).

What do I do next?

---

### Post by cariboo on 2013-09-18
Open a terminal, and type:

```
alsamixer
```

and make sure none of the outputs are muted, or turned down to low. Use the left and right arrow keys to navigate between the different controls, and the up and down arrow keys to alter the volume. Pressing the ***m*** key toggles mute on and off. To store the settings after you are happy with them press the ***esc*** key to exit alsamixer, then type:

```
sudo alsactl store
```

to save the settings.

---

