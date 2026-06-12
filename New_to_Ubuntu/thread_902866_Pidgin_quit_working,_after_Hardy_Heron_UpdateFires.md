---
title: "Pidgin quit working, after Hardy Heron Update/Firestarter Install"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by juicethief on 2008-08-27
Pidgin quit working after I updated to 8.04 and installed firestarter. It will say it is starting and then just disappear without any warnings or anything. Need help don't know much about Ubuntu; Windows developed a nasty virus and I had to put it down for good. Not upset one bit.

---

### Post by tdrusk on 2008-08-27
> **juicethief said:**
> Pidgin quit working after I updated to 8.04 and installed firestarter. It will say it is starting and then just disappear without any warnings or anything. Need help don't know much about Ubuntu; Windows developed a nasty virus and I had to put it down for good. Not upset one bit.
Try going into Synaptic Package Manager and completely removing Pidgin. Then install it again. If that does not work restart. If that does not work I will get back to you.

---

### Post by zamadatix on 2008-08-27
well you could always try reinstalling pidgin, i wasnt aware that pidgin actually gave startup messages to tell the truth.

---

### Post by jerome1232 on 2008-08-27
Try starting it from a terminal and post the output of the error it generates.

Also you might want to try it with fresh configs just to test
```
mv .purple .purple-backup
pidgin
```

Try disabling all of pidgins plugins too.

I've had a similar issue, it was msn account that was making pidgin segfault. I will post a link to the thread I ended up reinstall I get fed up with it, there is a purposed solution if this is the case for you.
Here is the link
[http://ubuntuforums.org/showthread.php?t=880449](http://ubuntuforums.org/showthread.php?t=880449)

---

