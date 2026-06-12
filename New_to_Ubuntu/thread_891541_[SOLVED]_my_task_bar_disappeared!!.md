---
title: "[SOLVED] my task bar disappeared!!"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-16
when i started kubuntu a dialog box came up and asked me some questions,then when kubuntu started my theme settings where changed and the kicker is gone.
how do i get it back?
Rick

---

### Post by jrothwell97 on 2008-08-16
Are you using KDE3 or KDE4?

If you're using KDE3, then try running

```
killall kicker
kicker &
```

Press Alt+F2 (I think) to get a 'run' dialog box.

If you're using KDE4, and all your desktop widgets *as well* as the Kicker have disappeared, then you need to restart Plasma. Restart X by pressing Control, Alt and Backspace. It may beep loudly, but don't worry, and you'll be returned to the login screen.

If it's *only* the Kicker that's gone in KDE4, then use the 'add widgets' function to add a new Kicker panel on the bottom of the screen and then reconstruct your old layout (with Kickoff menu, system tray, clock, etc). It doesn't sound like you have much configured, so if you want to reset to a vanilla KDE4 install, then here's what to do:

[list][*]Drop to a virtual terminal by pressing Control, Alt and F2. The screen will blank for a bit and then come up with a text login prompt: log in using that (the password characters won't appear, but don't worry.)
[*]Run ```
cd ~
``` to ensure you're in the right directory.
[*]Run ```
mv .kde4 .kde4.old
```. This moves the KDE4 configuration directory out of the way.
[*]Type ```
logout
``` to log out of the virtual terminal, and then press Control, Alt and Backspace to restart X. Try logging in again, and the Kicker should have reappeared.[/list]

I'm unsure about some of the steps I've gone through here, but they should work. Good luck.

---

