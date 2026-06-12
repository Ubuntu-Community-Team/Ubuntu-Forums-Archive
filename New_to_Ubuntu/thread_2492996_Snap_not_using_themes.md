---
title: "Snap not using themes?"
date: 2023-11-29
forum: New to Ubuntu
---

### Post by Scott O'Nanski on 2023-11-29
I just installed the GIMP snap package and I can't install my themes. Why is that? Normally, I would just put the file in the theme folder.

Is there an easy 'drop and drag' solution to this? Or should I just use a Flatpak version instead? I would normally use the *.deb version, but Ubuntu went and messed around with something and python in 22.04 which screws all my plugins. Needless to say that's out of the question.

---

### Post by #&amp;thj^% on 2023-11-29
Please try this first:
```
/snap/bin/gimp
```
Any better?
I have no issues with:
```
apt policy gimp
gimp:
  Installed: 2.10.36-1
  Candidate: 2.10.36-1
  Version table:
 *** 2.10.36-1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```
I don't use snaps.

---

### Post by Scott O'Nanski on 2023-11-29
> **1fallen said:**
> Please try this first:

```
apt policy gimp
gimp:
  Installed: 2.10.36-1
  Candidate: 2.10.36-1
  Version table:
 *** 2.10.36-1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

What's this?

I just have a bunch of weird-ass named folders in the the snap folder. I found one called themes, but it's not doing anything.

---

### Post by #&amp;thj^% on 2023-11-29
> **Scott O'Nanski said:**
> What's this?

I just have a bunch of weird-ass named folders in the the snap folder. I found one called themes, but it's not doing anything.
It's a .deb and not a snap.
```
systemctl status snapd
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)
TriggeredBy: &#9675; snapd.socket

```
As I mentioned I un-snap at installation, it's just my preference.
Did you try the command I showed?

---

### Post by ian-weisser on 2023-11-29
> **Scott O'Nanski said:**
> I can't install my themes. Why is that? Normally, I would just put the file in the theme folder.

Customization and theming of Snaps is a known problem.
However, is it also a complex problem. It is the intersection of sandboxing, read-only applications, and customization.
Developers are working on it, and I'm sure that eventually they will solve the problem. But it won't be immediate.

> **Scott O'Nanski said:**
> should I just use a Flatpak version instead?
That's up to you.

> **Scott O'Nanski said:**
> I would normally use the *.deb version, but Ubuntu went and messed around with something and python in 22.04 which screws all my plugins.
Please file a bug report. They cannot fix if nobody tells them about it. However, nothing wrong with my 22.04 Gimp (deb), so your problem is not universal. Be sure that it's not self-inflicted before filing a bug report.
Perhaps one of the three releases since 22.04 has fixed it.

---

### Post by Dennis N on 2023-11-29
> **Scott O'Nanski said:**
> I just installed the GIMP snap package and I can't install my themes. Why is that? Normally, I would just put the file in the theme folder.

Is there an easy 'drop and drag' solution to this? Or should I just use a Flatpak version instead? I would normally use the *.deb version, but Ubuntu went and messed around with something and python in 22.04 which screws all my plugins. Needless to say that's out of the question.

The theme must be in a snap package. There is a default snap called gtk-common-themes with some common application and icon themes. There are also some individual snaps for themes that you can find in the snap store and install. 

Try: **snap search theme | grep theme** to see extra themes.

Flatpak applications use themes that are Flatpaks. There are a lot of these available.

---

