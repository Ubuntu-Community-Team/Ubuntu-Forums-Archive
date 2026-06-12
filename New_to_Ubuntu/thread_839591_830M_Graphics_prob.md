---
title: "830M Graphics prob"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Pepperoni on 2008-06-24
I'm trying to get Ubuntu installed on an older Fujitsu C Series laptop, but the video gives me issues.  It's an Intel 830M chipset.  The install starts OK, but then the screen gets corrupted and goes 100% white.  I can hear the log on music, so it appears that it's not crashing--other than the video problem.  I tried safe graphics mode--same problem.  Any other ideas?

---

### Post by Biggy on 2008-06-24
maybe Xubuntu is best choise for your laptop...

---

### Post by Pepperoni on 2008-06-25
Xubuntu doesn't work, the alternate CD doesn't work.  I've even tried Fedora and that doesn't work.  Each time when the xserver tries to kick off, the screen slowly turns all white.  It's frustrating because this laptop is not that bad (P III, 512 RAM) and I'd like to get it working.  I suppose that this Fujitsu laptop isn't compatible.

---

### Post by immerohnegott on 2008-08-08
I haven't had THAT particular issue, but the machine should be compatible (I have a Dell C400 with similar hardware). Mine works, albeit with a different set of graphical glitches. Can you ctrl+alt+F2 into a tty?

---

### Post by Ptero-4 on 2008-08-08
Get into the text console (ctrl-alt-f1), install 915resolution (855resolution installs this package), run it and restart X.

---

