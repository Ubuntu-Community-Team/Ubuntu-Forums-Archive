---
title: "[SOLVED] Network manager &amp;lt;debug&amp;gt; msgs at startup"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-22
I get more than a screen of messages prefixed with: Network manager <debug> that scroll off the screen before I can read them.
Can I turn them off? I'm not connected to any network. 
Do I need a Network manager if I have no network?

Thanks,
Norm

---

### Post by kilroy423 on 2008-05-23
You can check your logs, see if you can find those messages by:

```
cat /var/log/messages
cat /var/log/dmesg

```

just post those back here and we can help you figure out the problem


Kilroy

---

### Post by mapes12 on 2008-05-23
If you do not need network services the the Network Manager pacakage can be safely removed via Synaptic Package Manager.

If you need network services in the future you may want to try this alternative to Network Manager:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

