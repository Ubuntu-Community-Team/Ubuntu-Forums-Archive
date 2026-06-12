---
title: "[SOLVED] how to update(new to kubuntu)"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-22
i just switched to kubuntu and no nothing about it!does it update the same as ubuntu,and what about software the package mgr seems sparse and it doesnt seem to go online to update like ubuntu???
rick:confused:

---

### Post by teamkiller87 on 2008-07-22
The only thing that's different is the desktop environment. Nothing else... To update from CLI, run:

```
sudo apt-get update
```

---

### Post by SunnyRabbiera on 2008-07-22
The package updater in kubuntu is a little flaky though, I really dont like adept.

---

### Post by northern lights on 2008-07-22
The standard KDE package manager is "adept" - the analogue to gnome's "Synaptic".

From the commandline, updating works exactly the same. Run ```
sudo apt-get update
sudo apt-get upgrade
```

and should you suspect leftover trash ```
sudo apt-get autoremove
``` afterwards.

---

### Post by tech0007 on 2008-07-22
> **northern lights said:**
> the standard kde package manager is "adept" - the analogue to gnome's "synaptic".

From the commandline, updating works exactly the same. Run ```
sudo apt-get update
sudo apt-get upgrade
```

and should you suspect leftover trash ```
sudo apt-get autoremove
``` afterwards.

+1

---

### Post by Paqman on 2008-07-22
> **SunnyRabbiera said:**
> The package updater in kubuntu is a little flaky though, I really dont like adept.

I've used Synaptic on KDE with other distros. Works just dandy.

---

### Post by rixtr66 on 2008-07-22
thanks guys!!!!:)
rick

---

### Post by SunnyRabbiera on 2008-07-22
> **Paqman said:**
> I've used Synaptic on KDE with other distros. Works just dandy.

Aye, usually if I give kunbuntu to others I give them synaptic.
Adept sucks in my opinion

---

### Post by northern lights on 2008-07-22
> **SunnyRabbiera said:**
> Adept sucks in my opinion

Agreed. But then again, I'd say the same, at least comparatively, about KDE. Why not stick to gnome in the first place?

N.B. gotta admit I haven't checked out KDE4 - is it powerful enough to make it worth it?

---

