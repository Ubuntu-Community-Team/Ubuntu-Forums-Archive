---
title: "Boot problem"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-09-13
I have a dual-boot machine with Hardy and XP. Everything is working swimmingly, except for one annoying detail...

If XP is the last OS I've used and I go to try to boot into Hardy (doesn't matter if I'm rebooting or coming back after awhile), it fails to boot. I get the startup splash screen, the bar moves about halfway across, then the screen goes black. If I force kill the machine and boot back into Hardy, it does what it's supposed to do. I don't think this is a serious problem, but if someone could help me fix it, I'd be very grateful.

Thank you!

---

### Post by ptn107 on 2008-09-13
Paste the output of 'dmesg' into pastebin [because it's gonna be huge] ([http://paste.ubuntu.com/](http://paste.ubuntu.com/)).  Then post that url.

---

### Post by doctorbighands on 2008-09-13
[http://paste.ubuntu.com/46720/](http://paste.ubuntu.com/46720/)

I'm not sure I was able to capture everything...it seemed as if the terminal wouldn't scroll all the way to the top.

---

### Post by ptn107 on 2008-09-13
Hmm.  Unfortunately your log does not show any signs of error, which will make it hard to diagnose.

---

### Post by doctorbighands on 2008-09-13
Well, I suspected that it might just be a "quirk." Bummer.

If anyone else has any ideas, though, I'm open to them!

---

### Post by jemate18 on 2008-09-13
> **doctorbighands said:**
> Well, I suspected that it might just be a "quirk." Bummer.

If anyone else has any ideas, though, I'm open to them!


what did you use to have dmesg?
```
user@host# dmesg
```?

You might want to have the output saved into a file so that you will be able to view all of its contents...
type```
dmesg > nameoffile.txt
``` 
the .txt is optional though.....

---

