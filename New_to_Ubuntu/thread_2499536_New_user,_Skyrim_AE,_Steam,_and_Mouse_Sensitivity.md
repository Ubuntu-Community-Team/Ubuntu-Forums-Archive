---
title: "New user, Skyrim AE, Steam, and Mouse Sensitivity"
date: 2024-07-30
forum: New to Ubuntu
---

### Post by turtlegrunty on 2024-07-30
Recently switched from Windows to Ubuntu Pro.  Loaded up Skyrim on Steam and the mouse seems a little fast for me.  Adjusted the pointer speed Skyrim to the lowest point and it's still a little too fast for me.  Keeps running either just past the speech option or jumps over whatever it is I'm trying to focus on.  Turned off Mouse Acceleration and made Pointer Speed slower in the Mouse & Touchpad section of settings but that didn't seem to solve the issue.  Turning off Repeat Keys in Accessibility did solve the issue of moving for far longer than I wanted the character to.

Where can I find the preferences file in Skryim to adjust the mouse settings within the game itself?  I tried searching not only my home folder but the Ubuntu drive and no luck.  When right clicking on the Skyrim Icon it will only allow me to launch the game, not open the folder where it's housed.  Same with Steam.

Anything I should download to adjust this or find the files needed?

Thanks for any help.

---

### Post by currentshaft on 2024-07-30
Try this:

find ~ -iname "skyrim*ini"

---

### Post by turtlegrunty on 2024-07-30
Awesome!  Found them!

Now, any reason why I can't see the folder .steam in my Home folder?  I had to actually type in /.steam in the search bar to make it pop up.  I assume it's some kind of permission issue even though I'm the only user of this machine.

---

### Post by currentshaft on 2024-07-30
Files starting with a "." in Unix are considered "hidden" and it looks like Ubuntu doesn't show them by default. Control-H seems to change that setting.

---

### Post by turtlegrunty on 2024-07-30
Almost got the sensitivity to where I want it.  Thank you so much for all the help and information!

---

