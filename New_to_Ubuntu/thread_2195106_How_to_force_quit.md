---
title: "How to force quit?"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by michael-piziak on 2013-12-22
I tried to open a jpg and the system locked up.  How do you force quit when this happens?  control-alt-delete didn't work

---

### Post by philinux on 2013-12-22
I use this if completely frozen.
[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

However if just an app I use ctrl alt t to get a terminal and use xkill

---

### Post by ajgreeny on 2013-12-22
> **philinux said:**
> I use this if completely frozen.
[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

However if just an app I use ctrl alt t to get a terminal and use xkill
+1

I have set a keyboard shortcut for xkill (Winkey+Del) which occasionally is very useful on the when ristretto locks up opening images in my Xubuntu 12.04.

You don't say which application or which OS version you have, but I am generally using another image viewer as default as ristretto locks more than any other.  If this is your problem try mirage or gpicview, or just delete the config file at ~/.config/ristretto/ristretto.xml and let the application make it again.

---

### Post by whitesmith on 2013-12-22
> **michael-piziak said:**
> I tried to open a jpg and the system locked up.  How do you force quit when this happens?  control-alt-delete didn't workIf by "the system" you mean Ubuntu or such, that can be corrected by resetting just that layer which sets atop Linux. Do an Alt+SysReq+RSKIUB. (*Raising skinny elephants is utterly boring,* if you hearken to mnemonics.) Many users refer to Linux itself as "the system." Its kernel is so robust that it rarely, if ever, fails, so that's one less thing to worry about after leaving products  made in Redmond. Best of luck to you and may you find peace with a real OS proudly made by geeks for geeks!

---

### Post by Vormeph on 2013-12-22
If a program freezes, open up the terminal or tty1 (CTRL+ALT+F1) and:

```
pkill -SIGKILL ##PROGRAM YOU WANT TO KILL##
```

e.g....

```
pkill -SIGKILL firefox
```

Good luck!

---

