---
title: "Startup problem"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by mikkenzi on 2008-07-13
Hi all,
I've never had serious issues with Ubuntu up to now but there is something weird happening since I got Ubuntu 8. 
When I start the machine, grub loads and all goes smoothly but afterwards, instead of the login screen I see a black screen and the PC just hangs. The second time I boot the PC, all goes ok again and I reach the login screen without problems. I log in and all seems ok. Now, I have noticed that it always goes OK the second time but it is never OK the first time. Imagine I go to bed and switch off PC for, say, 6 hours. When I come back - I boot - problem. I boot second time - no problem... 
I have no idea where it comes from. I read somewhere that I should hit Ctrl+Alt+F4 to see what happens behind the logo and the first time nothing happens when I hit the keys. The second time - I get to see the details and all is on [OK] and boot is rapid.
Does someone have the same problem? Might it be a virus??? I am pretty cautious when surfing but one never knows... Or is it simply the Ubuntu 8 update?
Thanks a lot!

---

### Post by hyper_ch on 2008-07-13
what makes you think it's a virus?

if you see grub, press "e" to edit the entries, then edit also the actual line with vmlinux on it and remove after the ro parameter everything and add "nosplash" and then press "b" to boot.

it should tell you then why x isn't started

---

### Post by mikkenzi on 2008-07-13
I don't know why... It was just a wild guess. I haven't installed anything on it except Open Office. But since I have had all sorts of trouble on Windows, I am pretty scared of everything now:)
When I reboot - it all loads correctly. I think it gets stuck after the PC is off for some time...

---

