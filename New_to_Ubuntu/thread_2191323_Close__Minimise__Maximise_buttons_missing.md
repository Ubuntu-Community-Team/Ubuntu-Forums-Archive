---
title: "Close / Minimise / Maximise buttons missing"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by raghavender-reddy2410 on 2013-12-02
Hello,

I'm new to this forums. This is my first post.
I'm using Ubuntu 13.10. I know that the close / minimize and maximize buttons are hidden until we move our cursor to top left corner.
from few days when I move my cursor to top it shows close/minimize/maximize buttons. But when I move cursor on to the buttons they hide again.
[ATTACH=CONFIG]248260[/ATTACH] This SS shows that the buttons are visible when the cursor is in the rectangle region.

[ATTACH=CONFIG]248262[/ATTACH] This SS shows that the buttons are hidden when the cursor is at top left corner ( Rectangular region )

It happens in all windows i.e. chromium, Mozilla, file browser, etc.
How to solve this problem?

---

### Post by thatredbird on 2013-12-02
You might try changing the theme in system>appearance>themes. Toggle to one and then back. Supposedly its a redraw problem.

---

### Post by daslinkard on 2013-12-02
Have you tried resetting your unity?
```

unity --reset
```

After this is completed restart your computer and see if this fixes your issue.

---

### Post by deadflowr on 2013-12-03
Grab the top bar of the window and drag it down so it becomes a non max window, then drag it back to the top to remaximize it.
Do you have buttons again, or no?

---

### Post by raghavender-reddy2410 on 2013-12-03
> **thatredbird said:**
> You might try changing the theme in system>appearance>themes. Toggle to one and then back. Supposedly its a redraw problem.
 I tried but no use.

---

### Post by raghavender-reddy2410 on 2013-12-03
> **daslinkard said:**
> Have you tried resetting your unity?
```

unity --reset
```

After this is completed restart your computer and see if this fixes your issue.

It happens every time. I mean after 30-40 minutes of using PC.
I cant restart for every 30-40 minutes.

---

### Post by raghavender-reddy2410 on 2013-12-03
> **deadflowr said:**
> Grab the top bar of the window and drag it down so it becomes a non max window, then drag it back to the top to remaximize it.
Do you have buttons again, or no?
No. :(

---

### Post by deadflowr on 2013-12-03
> **raghavender-reddy2410 said:**
> No. :(

When you dragged the window down, did the buttons show up in the window title bar, as they should?

---

### Post by raghavender-reddy2410 on 2013-12-11
> **deadflowr said:**
> When you dragged the window down, did the buttons show up in the window title bar, as they should?
ya

---

### Post by fenario on 2013-12-11
get rid of unity and install gnome-session-fallback. personally I don't like unity at all; I think it was meant to be for touch screens.

---

