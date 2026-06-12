---
title: "Launcher autohide at fullscreen"
date: 2017-10-03
forum: New to Ubuntu
---

### Post by dimitri123abcd on 2017-10-03
Hello I would like when I maximize any software the launcher to go to auto hide. I cannot see this option at Ubuntu 16.4
I installed a custom script and I sign it as a keyboard shortcut so whenever I want the launcher to go auto hide I just press a keyboard key (that I assigned) 
But I would like to do it automatically. Is any way? Thank you

---

### Post by mc4man on 2017-10-03
No, that option(s) have been gone for years & currently can't be hacked around. What you want was called 'dodge windows', it had 2 options - hide launcher if any window touched or was over or dodge windows active which only hid launcher if the active window touched or was over.

---

### Post by again? on 2017-10-03
Add this to your script (requires wmctrl to be installed)
```
wmctrl -r :ACTIVE: -b toggle,fullscreen
```
Toggles fullscreen of the focused window.

If you don't know how to implement in your script, post the script.
Then in keyboard shortcuts change the F11 key to run your script or assign an unused custom keyboard shortcut.

---

### Post by dimitri123abcd on 2017-10-03
I put your code in the script it looks like it is like before, it just it takes not the whole screen and it does not desplay the File,edit,view etc. Is any way it can
work automatically without pressing the shortcut key?

---

### Post by again? on 2017-10-03
My mistake.
Should be maximize not fullscreen.
```
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
```

Have a look at these python scripts.
[https://askubuntu.com/questions/553539/how-can-i-auto-hide-the-launcher-via-a-script-when-i-maximize-the-browser](https://askubuntu.com/questions/553539/how-can-i-auto-hide-the-launcher-via-a-script-when-i-maximize-the-browser)

---

### Post by again? on 2017-10-04
Hi, had to go out.
Just tested the first python script from my previous link. [https://askubuntu.com/a/553547](https://askubuntu.com/a/553547)
Works for me in Ubuntu 16.04.

---

