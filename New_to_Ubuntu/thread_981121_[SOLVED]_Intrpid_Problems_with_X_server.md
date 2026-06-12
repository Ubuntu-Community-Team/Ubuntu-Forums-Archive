---
title: "[SOLVED] Intrpid Problems with X server?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Sidney232 on 2008-11-13
My first post!
I recently upgraded from Hardy to Intrepid and everything appears to work just fine…all except the user switcher. It sometimes fails to work altogether. It sometimes throws up error messages along the lines of ‘X server failed to finish starting – 3X failed’. Yesterday I tried (after following another thread) and ran ‘sudo dpkg-reconfigure xserver-xorg’ and answered the questions to the best of my knowledge. Now the system starts up in low resolution mode (but looks as normal anyway). So questions:

1) What’s going on?

2) Can I and how do I revert back to my back-up xorg file?

3) How can I sort the original user switcher problem?

I’m running a Dell Dimension 4400 pentium 4 1.7GHz with 756MB Ram. Graphics card is Rage 128 Pro. There’s nothing else on the PC – no dual boot etc. I installed originally last year from 7.10 and upgraded to 8.04 with no problems. I have two HDD; a 13GB one on which the OS is installed and a 40GB one set up just for data. Both work just fine. Not sure I can tell you much else.

---

### Post by MuH4hA on 2008-11-13
I can't help you with your original problem, but there should be a backup of your xorg.conf in your /etc/X11 named something like "xorg.conf.20081113193900"....

You have to replace xorg.conf with this backup to set the system to the old configuration...

---

### Post by Sidney232 on 2008-11-13
OK thanks, that worked. :)
Still have my original problem though.:(

---

### Post by Sidney232 on 2008-12-11
Marking this thread as solved because discussing elsewhere. (See my thread under General Help.)

---

