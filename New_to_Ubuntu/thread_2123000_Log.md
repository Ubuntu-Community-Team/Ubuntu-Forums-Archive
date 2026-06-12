---
title: "Log"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by BobJam on 2013-03-06
When you restart, the black screen immediately appearing after the restart flashes some information.  It appears too quick on the screen and then goes away too quickly for me to see what it all is (and then it goes to the grub menu, which is fine).

I assume this info is somewhere in a log.  Just curious to read it . . . does not break my machine at all.

So what log is it in and where is the log?  (Most are in the var directory, but I can't seem to find it there.)

---

### Post by Frogs Hair on 2013-03-06
I have seen this on 12.10 due to a Nvidia proprietary driver.  It was resolved after installing one of the other available Nividia drivers. I don't think there is anything to worry about if all is working well. Sometimes proprietary drivers will cause problems when the splash screen loads. If you have not installed any drivers it may be a similar problem, but with the default driver.

---

### Post by siddharth007 on 2013-03-07
You could try the kern.log, boot.log and bootstrap.log in /var/log. Catting would do.Alternatively,you can access those files using some basic editor.

---

