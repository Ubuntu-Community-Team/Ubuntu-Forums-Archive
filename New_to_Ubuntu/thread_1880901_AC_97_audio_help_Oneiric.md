---
title: "AC 97 audio help Oneiric"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by teacherjeff on 2011-11-14
I have an ancient Emachines laptop.  I was dual-booting Windows XP and Ubuntu Natty and everything was good.  Then I decided to install Oneiric. Clean install, not an upgrade.  Now I have no audio through the built in speakers.  I do have audio through headphone jack.  And speakers work in Windows, so I assume it's not a hardware problem.  

I've been through what I think must be every combination of Hardware and Output options in the Sound Settings menu, and no luck.  

Any advice?  I really hate to give up on this poor old computer.  It is still useful to me.

BTW, I'm not a complete Ubuntu novice, and I realize I probably need to post more information.  But after reading about Alsa, Pulse, and who-knows-what else, I'm a bit bewildered.  I'm not even sure what information to post.

Help, please..... :)

---

### Post by ajgreeny on 2011-11-14
If you haven't already tried this, run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low or muted.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by teacherjeff on 2011-11-14
Thanks, aj.  But I should have mentioned that I spent a good part of yesterday with alsamixer.  Unmuting, muting, sliding, and everything else I could think of.  

Still no luck.

---

