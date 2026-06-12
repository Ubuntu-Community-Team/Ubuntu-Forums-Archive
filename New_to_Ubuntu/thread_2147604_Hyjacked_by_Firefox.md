---
title: "Hyjacked by Firefox"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by gabmuks on 2013-05-22
Hello and good day to all.

Three days ago I installed regular updates from update manager.
Since then, Firefox launches every time I boot up.
I can't close Firefox!
There is no "x" icon to close it with.
The File and Edit tabs do not function at all.
I am not allowed to open any other applications at all.
Can anyone tell me how to disable Firefox?
I can't even get into the Applications screen to launch a terminal.
Can someone tell me how to get to terminal and command to disable Firefox?
Thank you for your time.

---

### Post by SlugSlug on 2013-05-22
seems a bit odd.

you can use ctrl+alt + F1  to get to a terminal.

then once you have logged in use 

pkill firefox

the ctrl+alt + F7 (or F8) to get back to GUI

---

### Post by Frogs Hair on 2013-05-22
Ctrl + Alt + T to open the terminal and try the following to kill Firefox. I don't know the cause of the problem though.

```
killall firefox
```

---

### Post by gabmuks on 2013-05-22
> **SlugSlug said:**
> seems a bit odd.

you can use ctrl+alt + F1  to get to a terminal.

then once you have logged in use 

pkill firefox

the ctrl+alt + F7 (or F8) to get back to GUI

Thank you very much Sir!
So far that has worked.
Interesting that I tried the "Control+Alt+T" suggestion first.
But a terminal did not come up at all.

Should I submit this problem to someone?

Thanks again

---

### Post by gabmuks on 2013-05-22
Have a new symptom if still interested.
You have definitely solved the Firefox problem by disabling it.
So now I can bring up my Google browser.
But the browser screen is cut in half.
A vertical line right down the middle.
So am unable to view entire browser screen at the same time.
Only half of it is visible. Basically worthless.
must use screen positioning arrow at bottom of browser screen
 to move and view other half of screen.
The "x" icon is present now and is functional,
but the "minimize" and "maximize" icons do not function.
But everything else works fine now. All applications available and present.
Thanks for your time.

---

### Post by Bartender on 2013-05-22
Maybe completely uninstall Firefox, restart PC, and reinstall?

---

### Post by oldos2er on 2013-05-22
gabmuks, which version of Ubuntu are you running?

---

