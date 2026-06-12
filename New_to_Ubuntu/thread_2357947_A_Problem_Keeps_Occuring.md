---
title: "A Problem Keeps Occuring"
date: 2017-04-07
forum: New to Ubuntu
---

### Post by mobileberna on 2017-04-07
When Xubuntu loads, I get MULTIPLE pop-ups informing me that an internal issue has occurred. I'm not familiar with Xubuntu enough to troubleshoot the problem. I also have a message that wont leave my panel bar telling me a problem occurred when checking for the updates. I'm going to need step by step guidance here! I promise to spend this weekend really getting to know Xubuntu and Ubuntu (Ubuntu will be installed on my desktop).

---

### Post by TheFu on 2017-04-07
Check the log files.  google "ubuntu logs" if you need more.

Then google the exact error message without any system-specific parts or things that look like timestamps. Think error unique in your google-fu.

Linux is like Unix and takes years to learn. You will learn a bunch, but if your background is from non-Unix OSes, it is a steep, rewarding, learning curve.  Just know that the GUI is just another program and that almost all troubleshooting across all Linux systems, regardless of GUI, will follow the same basic steps. Just trying to set expectations.  If you skip the GUI programs and learn everything under it, that knowledge will last a lifetime. I'm still using techniques learned in the early 1990s because the underlying system hasn't changed all that much.  

If I had learned only the GUIs over the years, about every three years, I'd have to start all over. Not very efficient.

---

### Post by Bucky Ball on 2017-04-07
My guess is that this is the apport error check bug, known to happen in fresh installs of Xubuntu on occasion, and perhaps other flavours too.

Apport is used by devs and for some reason is not switched off again by default. You don't say which release you are using, but I'm guessing 12.04 or 14.04? Anyway, switch it off by following the instructions under ['Disable Apport at Boot' here]("http://howtoubuntu.org/how-to-disable-stop-uninstall-apport-error-reporting-in-ubuntu").

Basically, this:

```
sudo nano /etc/default/apport
```

and change 'enabled=1' to 'enabled=0'. When you open that file, is enabled set to one? That is a sign. Disable and reboot.

In other words, the error messages apport is throwing are probably not errors for you to be bothered about.

PS: You may find a better explanation of the apport error messages and why they can be ignored if you have [trawl through here]("https://duckduckgo.com/?q=switch+off+apport+xubuntu&t=hb&ia=web") if you can be bothered. :)

If you are still having issues with updates after that, might be best for you to post a new thread about it, preferably with a descriptive title rather than 'A problem ...'. Also, for best results, one support request a thread. Less confusing that way and the way the forum likes it. Good luck. ;)

---

### Post by wildmanne39 on 2017-04-07
*Thread moved to **New to Ubuntu**.*

---

### Post by mobileberna on 2017-04-08
Thank you for the advice! I do apologize for my ignorance and not properly posting...hahaha from now on I'll just post everything under "im an idiot" or "new to ubuntu"! I'm spending quality time this weekend really learning the system.

---

### Post by oldrocker99 on 2017-04-08
> **mobileberna said:**
> Thank you for the advice! I do apologize for my ignorance and not properly posting...hahaha from now on I'll just post everything under "im an idiot" or "new to ubuntu"! I'm spending quality time this weekend really learning the system.

**Everybody** was a newbie at some point, and we moderators sometimes post questions, too. This forum is designed to help all users. The time may come when **you** help another user!

---

