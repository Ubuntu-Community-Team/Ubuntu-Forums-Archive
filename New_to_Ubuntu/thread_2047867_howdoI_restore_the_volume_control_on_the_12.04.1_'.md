---
title: "howdoI restore the volume control on the 12.04.1 'panel'"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-08-25
Hi Community:

In some of the work I did to "fix" my sound, I inadvertently removed the volume control icon on the upper horizontal "panel" of Unity.

:-?

How do I restore that icon?

Thanks!
Oldest of Old Jimma

---

### Post by nyamina on 2012-08-25
> **Old Jimma said:**
> Hi Community
Hi...I didn't even know you could do that! Did you uninstall the gnome power manager by mistake? That's what I would be checking.

---

### Post by cryptotheslow on 2012-08-25
Without knowing what you have done to "fix" your sound it's hard to say.

The volume indicator in the top panel is a package called indicator-sound. Open a Terminal and use this command:

```
sudo apt-get install indicator-sound
```

If you haven't removed it, it will just say that it is already installed - if it is already installed then please be more specific about what you have done to try to "fix" your sound and what the problems were that caused you to try to "fix" it.

HTH

---

### Post by Old Jimma on 2012-08-25
Hi Cryptotheslow:

Your recommendation:

> sudo apt-get install indicator-sound

Worked perfectly!

Thanks!
Old Jimma


ps. I uninstalled and reinstalled pulse. The "unistallation" removed the indicator, and reinstalling pulse did not restore it. Thank your helpful and accurate suggestion!

---

### Post by cryptotheslow on 2012-08-25
I guess that indicator-sound has the pulseaudio package as a dependency - so remove pulseaudio and apt takes out indicator-sound with it. When re-installing pulseaudio - I guess it does not depend on indicator-sound (no logical reason why it would) so indicator-sound does not get re-installed.

If you have a look at /var/log/apt/history.log (open it in gEdit or any other text application) and find the entry for when you removed pulseaudio, you should find the other packages that got ripped out at the same time as dependencies in the entry above or below the pulseaudio removal. Consider that list if you find other sound related anomalies as there may be other packages you need to reinstall to get back full integration.

Happy to have helped and thanks for posting back your confirmation on the resolution.

---

