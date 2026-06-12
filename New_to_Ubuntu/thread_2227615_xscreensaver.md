---
title: "xscreensaver"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-06-03
Ubuntu 14.04

I have upgraded from 13.10 to 14.04. Now my xscreensaver don't seem to start at boot-up any more. I have removed and re-installed xscreensaver also. That (or something else???) have created a startup program called "Indicator Application" running "/usr/lib/i386-linux-gnu/indicator-application/indicator-application-service". I don't know what that is. I have also created another startup program running "xscreensaver -nosplash". That have worked perfectly well in 13.10. If I start the screensaver setup application and exit it again, then the screensaver works correctly, but not without me doing that first. Please help.

---

### Post by AskTell on 2014-06-03
Found this fix on [http://askubuntu.com/questions/128481/how-do-i-set-xscreensaver-to-autostart](http://askubuntu.com/questions/128481/how-do-i-set-xscreensaver-to-autostart)

"I had it working then I updated to 14.04 and it stopped working.

  The solution is to go into Synaptic and **completely remove** the Gnome screen saver. Ubuntu sneakily reinstalls it on "upgrade".

  When you reboot it should work now with the original xscreensaver -nosplash startup."

Good luck :)

---

