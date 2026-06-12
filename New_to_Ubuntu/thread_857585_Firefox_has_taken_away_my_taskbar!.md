---
title: "Firefox has taken away my taskbar!"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by jonofan on 2008-07-12
Without knowingly changing anything, firefox has taken over the screen so that I can't see the task bar. Have to alt+tab to get out. Is not in full screen. When I go View>Toolbars>Customize the taskbar shows up, but goes away soon as I close it...

---

### Post by RomeReactor on 2008-07-12
Hi. Try this: Press and hold ALT, then hold the left mouse button over Firefox and use the mouse to drag the window until you can see a corner, then resize it. Before you close Firefox, right-click on its entry in the window list (bottom panel) and make sure 'Always On Top' is unchecked.

---

### Post by jonofan on 2008-07-12
Hmmm, it does not allow me to resize the window. Holding ALT and left clicking does nothing. Always ontop is not checked.

---

### Post by RomeReactor on 2008-07-12
If you're certain it's not running in full screen, press ALT+F9 to minimize the window. You can then right-click on its window list entry to make sure 'Always On Top' is unchecked.

---

### Post by jonofan on 2008-07-12
Nope definitely not full screen nor always ontop. I just F11'd to fullscreen and back again and it seemed to resize the window back to normal.. hopefully that will have fixed it permanently.

Thanks for your help!

---

### Post by jimmysheldon on 2008-11-02
Hey. Just opened a firefox and had the same problem. F11 twice seemed to sort it out, hope it doesn't stay like this permanently.

---

### Post by Crafty Kisses on 2008-11-02
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox
```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any
```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```
Hope this helps.

---

