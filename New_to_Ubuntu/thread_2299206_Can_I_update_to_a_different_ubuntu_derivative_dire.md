---
title: "Can I update to a different ubuntu derivative directly?"
date: 2015-10-16
forum: New to Ubuntu
---

### Post by MMarauder on 2015-10-16
Hi all,

All ubuntu installation medias offer "update" option, but will that work when I want to switch ubuntu derivative? For example, can I update from Kubuntu 15.04 to Xubuntu 15.10 directly, while keeping all my data and /home configuration?

---

### Post by ian-weisser on 2015-10-16
That's not an update. That's not what the updater is for.
That's a very different sort of change, and complex to undo if you change your mind..

My experience with multiple Desktop Environments (DEs) has been that they sometimes interfere with each other (settings conflicts).
If you simply want to try a new DE, download a Live environment to try...or fire up a VM.

Each DE  is much more than just a theme or appearance. Each is a whole different workflow, with  different goals and different settings. Your old settings may not  apply, or may be ignored.

The simplest solution to replace one DE with another is to reinstall using the Live media for the new DE.
Backup your data first. While the installer will try to preserve your /home, it's an *installer*. It's primary function is to overwrite data.

---

### Post by Topsiho on 2015-10-17
You could install a different -desktop version, using synaptic, such as:

kubuntu-desktop
lubuntu-desktop
mate-desktop
xubuntu-desktop

and while booting choose the one you want to use this time.

It's a long time since I did that myself, and I would be reluctant to do so now on my main computer, but I remember that all went very well, except that the latest installed desktop was the one that showed it's login screen when booting.

It is always pure wisdom if you backup your precious data first.
And read ian-weissers remarks too, his experiences seem to be a bit different from mine :)

Topsiho

---

