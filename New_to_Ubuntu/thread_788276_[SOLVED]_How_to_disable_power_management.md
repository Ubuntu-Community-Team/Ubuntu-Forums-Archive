---
title: "[SOLVED] How to disable power management?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by ryth on 2008-05-09
Hi folks,

Despite the fact that I have disabled all the power management in the GUI, my new install of Hardy insists on entering suspend after 8 hours idle.  I have the suspend and hibernate times under preferences->screen saver->power management all set to "Never".

Is there a CLI file i could edit to disable power management completely so this doesn't happen, or some other work around that might be more effective?

I posted a similar thread in General but haven't heard a peep.  Is anyone else having a similar problem?

(I would actually love to use the power management but it seems to enter suspend when i have torrents downloading, and when i return from suspend my sound is non-functional, so if you have any ideas on that front I'm all ears)

My specs:

[SIZE="1"]i386 Hardy
AMD64 Dual 4200
ATI Radeon X1950XT[/size]

---

### Post by hotchkikr on 2008-05-09
that might just be the actual system, not as much gnome
because my doesn't suspend, but it does turn off the screen when I am in text only mode after so long

---

### Post by ryth on 2008-05-10
> **hotchkikr said:**
> that might just be the actual system, not as much gnome
because my doesn't suspend, but it does turn off the screen when I am in text only mode after so long

Before doing a fresh install of Hardy I never had this issue with Gutsy, and in my boot into XP I don't encounter the same issue which leads me to think there isn't a hardware/system power saving that is being invoked.

This is really getting frustrating because suddenly the problem has morphed that my system won't recover from the suspend so I end up having to do a reset.

There **must** be some sort of way I can even troubleshoot this?  Any suggestions at all are welcome.

Thanks.

---

### Post by ryth on 2008-05-26
Well after a few weeks of tinkering I was able to figure this out.

Here were the steps I followed to 100% disable all power management.

1.  Installed **Boot Up Manager**

```
sudo apt-get install bum
```

2.  De-select the following services
[LIST]
[*]powernowd
[*]apmd
[*]acpi-support
[*]acpid
[/LIST]

3.  Disable **Gnome-Power-Manager** from starting up when you boot into gnome.
```
System->Preferences->Sessions
```

Hope that helps anyone else who might be trying to trouble-shoot this.

Cheers.

---

### Post by Alchera on 2008-11-16
It might also be prudent to mention that [powernowd]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fdeater.net%2Fjohn%2Fpowernowd.html&ei=m5sgSei7F4nYsAOFlpDPCA&usg=AFQjCNHdIHUZhx5A_K4wx2KucJLEY0xIzg&sig2=o4tdb1t3HyyOXajPD-Ln7A") and [apmd]("http://linux.about.com/cs/linux101/g/apmd.htm") are specific to laptops and not required on a desktop system.

---

