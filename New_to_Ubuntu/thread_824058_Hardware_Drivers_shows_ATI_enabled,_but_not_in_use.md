---
title: "Hardware Drivers shows ATI enabled, but not in use?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-09
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73501&stc=1&d=1213053647[/IMG]

The first thing I tried was sudo dpkg-reconfigure xserver-xorg.  That unchecked the enable box in the above window, but clicking enable, and restarting, just brought me right back to square one.

What should I do?

---

### Post by Mjölner on 2008-06-09
I too have an ATI card, and had a similar issue.

What I did was goto; Applications -> add/remove and then installed the "ATI binary X.Org driver" and then went back to; system -> hardware drivers and then disabled and enabled again. or something like that.

good luck :)

---

### Post by diablo75 on 2008-06-09
> **Mjölner said:**
> I too have an ATI card, and had a similar issue.

What I did was goto; Applications -> add/remove and then installed the "ATI binary X.Org driver" and then went back to; system -> hardware drivers and then disabled and enabled again. or something like that.

good luck :)

It appears the driver is already there.  In fact, I used Envy to install it a long time ago.  It use to work, compiz was running, but I don't know why it suddenly stopped working.  This is on my dads computer, and it's been a while since the problem first started and now....

---

### Post by Mjölner on 2008-06-09
I'm sorry, but I don't think I can help much more.
There is a google group [here]("http://groups.google.com/group/x1250?hl=en") dealing with my card. perhaps it'll get you what you want.

---

