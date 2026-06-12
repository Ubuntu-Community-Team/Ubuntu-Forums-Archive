---
title: "bluetooth causes boot problems"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by aestrivex on 2008-08-13
i tried booting this morning to find that the boot process was hung up on initializing bluetooth.  several repeated attempts yielded the same thing.

so, in my infinite lack of knowledge, i ran recovery mode and removed the bluetooth initialization script from /etc/init.d/, figuring that it didn't matter because i'd never use bluetooth devices.


and it worked; ubuntu loaded as normally.  except my USB optical mouse (not a bluetooth device) which had previously functioned perfectly no longer worked.  plugging in an inferior PS2 mouse and rebooting i realized that having removed the bluetooth init script was probably a bad idea.

so i tried to boot the install CD to a live session, which also hung up on trying to initialize bluetooth.



what's going on?  is this an issue with some piece of my hardware?  how do i fix my mouse?

---

### Post by aestrivex on 2008-08-13
additionally, there seems to be some problem with my sound that i'm guessing is related to this issue.

from the login screen, the ubuntu login sound keeps playing perpetually.  i didn't notice this at first as i had my sound turned off since i didn't need it.  however when i tried to play a music file in mplayer it didn't work, which is typical on my machine when some other process is monopolizing the sound.

i turned off the login sound so as to get rid of it; it was highly annoying.  however, even after that the sound still seems to be occupied and mplayer still cannot play its music file.

---

