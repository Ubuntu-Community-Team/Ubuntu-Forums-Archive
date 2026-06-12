---
title: "[SOLVED] default keyring to unlock.......wont unlock"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by jpease on 2008-11-04
I am total newbie.  I installed the latest ubuntu released on thursday.  Everything was well until yesterday morning.

I boot up.
It asked for default keyring
I enter it and hit ok
The default key ring comes back over and over.


I know my password by heart.  I know what I put in.  In fact this screen came up when I was at my weekend home.I put in my password and it worked no problems.  I came back from my weekend home on sunday it worked all afternoon no problems.

Now it acts like the password has been changed.

What can I do to fix it?  Can I reset the password?

Don't forget I am a total newbie

---

### Post by jpease on 2008-11-04
please help?

---

### Post by LowSky on 2008-11-04
LOL i just posted somewhere else the fix
anyway...

go to /home folder, show hidden folders (CTRL+h) delete the keyring folder
named .keyring or .gnome-keyring, whatever it is i cant remember just do it, it wont effect anything, dont worry

when keyring prompt now comes up dont enter anything instead just hit enter.

---

### Post by aysiu on 2008-11-04
Also don't forget to double-check Caps Lock possibly being on.

---

### Post by jpease on 2008-11-06
found the gnome-keyring.  I deleted it and now I am rebooting.

Lets see what happens.

---

### Post by jpease on 2008-11-06
fantastic!   It WORKED!

---

