---
title: "How to intercept global keystrokes?"
date: 2011-02-20
forum: Programming Talk
---

### Post by foxmuldr on 2011-02-20
I have an ISO for a stand-alone kiosk. It uses Iceweasel (instead of Firefox), and I've gotten it down to where it boots up, displays my background image, runs a script which goes only to my homepage, only that app in a loop, etc.  But I cannot figure out how to bypass certain control keys:

CTRL+L, CTRL+J, CTRL+T, CTRL+K, ALT+D and F1

I want a way to trap those keystrokes globally so they never reach Iceweasel.  I have been looking at XGrabKey(), but cannot get it to work properly.

Any help would be appreciated.  Thanks.


PS - I'm to the point where I'm ready to build a modified kernel from source, or build a modified X from source, or anything. Please help.

---

### Post by foxmuldr on 2011-02-22
> **foxmuldr said:**
> I have been looking at XGrabKey(), but cannot get it to work properly.

I downloaded the Linux kernel source code and was able to get it compiled. I can make changes to keyboard.c to address this issue, but does anybody have a site that can show me how to install the kernel? I get a message "bad magic number" and it won't boot.

Thanks! :-)

---

