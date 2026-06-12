---
title: "Cannot right click (compiz)"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by bjunt4prez on 2008-11-11
I recently upgraded from Ubuntu 8.04 to 8.10. I was following this post: [http://ubuntuforums.org/showthread.php?t=939183](http://ubuntuforums.org/showthread.php?t=939183) to get virtualbox on startup in workspace 2, when i couldn't right click on anything (even in virtual box). I have undone everything from the post (that didn't help). I found this post: [http://ubuntuforums.org/showthread.php?t=964629](http://ubuntuforums.org/showthread.php?t=964629) which says "revert settings to default" in the compiz settings manager but I don't know where that is, and I don't want to do it because I like the customizations. Any one have any ideas?

---

### Post by bjunt4prez on 2008-11-11
bump

---

### Post by Crafty Kisses on 2008-11-11
Make sure none of your Compiz plugin bindings are using the right click.

---

### Post by bjunt4prez on 2008-11-11
i don't see any, if im looking in the right place.

---

### Post by bjunt4prez on 2008-11-11
of course it would probably help knowing which button means 'right click'

---

### Post by mr.v. on 2008-11-11
not to be negative or anything, but you're probably going to need to look through both gconf and compiz config settings manager at all the bindings to see what right click is bound or is not bound to (since it isn't working more likely right click got unbound to its functional settings). This will likely take *much* longer than resetting everything to defaults and monkeying with the graphics settings again.

To get compiz control settings manager type
```
 sudo apt-get install compizconfig-settings-manager 
```

---

### Post by bjunt4prez on 2008-11-12
i have looked in ccsm but can't find any

---

### Post by mr.v. on 2008-11-12
> **bjunt4prez said:**
> i have looked in ccsm but can't find any

Can't find any what?

If you're referring to the reset, open up CCSM then click on preferences button on the left then you should see a button on the right that says "Reset to Defaults" ... click that and see if it fixes the problem.

---

### Post by bjunt4prez on 2008-11-12
Still didn't fix the problem.  How about gconf?  I've never edited that file so I don't know where it is.

---

### Post by bjunt4prez on 2008-11-12
bump

---

### Post by bjunt4prez on 2008-11-12
bump

---

### Post by bjunt4prez on 2008-11-12
bump

---

### Post by bjunt4prez on 2008-11-13
bump

---

### Post by bjunt4prez on 2008-11-13
Completely removed compiz, same problem.

---

### Post by bjunt4prez on 2008-11-14
bump

---

### Post by bjunt4prez on 2008-11-15
is there a file somewhere that controls the mouse and keyboard? xorg.conf? please help

---

