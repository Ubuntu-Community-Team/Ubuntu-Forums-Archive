---
title: "Trackpad problems"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by Sigma1 on 2013-02-28
Hello,
After a clean install on a Samsung NP370R5E-A03FR (this is commercialised in France), the trackpad is no longer operative. It worked during installation. I've been through a number of the simpler fixes with no success (system settings, function keys etc.). It seems to me that, while the installation uses a generic driver, which works fine, once installed there must be a samsung module which, for whatever reason, does not work. Now, I'd like to go back to the module which was working during installation. In short, I'd appreciate it if someone could help me:
1. find out which module is responsible for the trackpad problems;
2. blacklist it;
3. provide a fallback option (perhaps this is automatic)
Thanks in advance!

---

### Post by cortman on 2013-02-28
Have you tried

```
synclient TouchPadOff=0
```

May as well cover the basics first.

---

### Post by Sigma1 on 2013-02-28
Thanks, I'll give this a go... I'm not in front of the computer, which is my daughter's, but will report back soon!
Thanks again

---

### Post by Sigma1 on 2013-03-01
No luck there, apparently: the touchpad remains entirely unresponsive...

---

### Post by cortman on 2013-03-01
But synclient IS installed, it seems?

Please post the output of

```
xinput list
```

Thanks.

---

### Post by Sigma1 on 2013-03-02
My daughter informs me that, after she plugged in a Wacom graphic tablet, the trackpad began working and has, touch wood, been functioning correctly since. Looks as if some switch was "off" that should have been "on". I'm sorry I can't be more precise, but don't have direct access to the machine.
Thanks again for your help, cortman... I've learnt a bit about trackpad support on the way!

---

### Post by cortman on 2013-03-02
> **Sigma1 said:**
> My daughter informs me that, after she plugged in a Wacom graphic tablet, the trackpad began working and has, touch wood, been functioning correctly since. Looks as if some switch was "off" that should have been "on". I'm sorry I can't be more precise, but don't have direct access to the machine.
Thanks again for your help, cortman... I've learnt a bit about trackpad support on the way!

Good to hear it's working, that's the main goal! Glad I could be of help. 
Good luck!

---

