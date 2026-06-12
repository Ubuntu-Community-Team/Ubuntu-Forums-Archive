---
title: "Google Music Manager missing from Unity application lens."
date: 2011-07-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-07-23
So, I installed the new Google Music Manager, but after restart, it's no longer listed under my applications. The software center says that it's a command-line  application, but when I try to start it, all I get is a status indicator with an empty menu.

---

### Post by PhantmKllr on 2011-07-24
Alright, something else I've just noticed:

Any application I install from the Ubuntu Software Center disappears from the Unity applications lens after restart, and is only accessible from the command line. What's going on?

---

### Post by mc4man on 2011-07-24
> **PhantmKllr said:**
> Alright, something else I've just noticed:

Any application I install from the Ubuntu Software Center disappears from the Unity applications lens after restart, and is only accessible from the command line. What's going on?

You haven't mentioned - 
are you using the 'add to launcher' option in U-S-C?

What apps, (other than Google Music Manager) are you referring to?

Are your icons, when initially visible, showing 'keep in launcher' enabled
The favorites icon's in the launcher are basically shortcuts to existing .desktops, do your disappearing apps have a .desktop and if so where?

---

### Post by PhantmKllr on 2011-07-24
> **mc4man said:**
> You haven't mentioned - 
are you using the 'add to launcher' option in U-S-C?

What apps, (other than Google Music Manager) are you referring to?

Are your icons, when initially visible, showing 'keep in launcher' enabled
The favorites icon's in the launcher are basically shortcuts to existing .desktops, do your disappearing apps have a .desktop and if so where?
I'm not just talking about the "launcher" (I call it the sidebar), but the applications in question are completely inaccessible from Unity. Period.

I believe that it only happens when I install an external .DEB file (downloaded from the internet) using the Ubuntu Software Center. So far I've tested Google Music Beta, Libdvdcss, and the SpiderOak client.

Also, this behavior may have been triggered by a recent update, because I had successfully installed VirtualBox and VLC yesterday (or the day before).

---

### Post by mc4man on 2011-07-24
Don't know about google music
libdvdcss(2) is a library not an app (unless you've gotten some app named that?

As far as  SpiderOak client - try browsing to /usr/share/applications and d. clicking on the "SpiderOak Backup" desktop file
It should startup and appear in the launcher, pin it and see if it survives a logout/in. (should

---

### Post by PhantmKllr on 2011-07-24
> **mc4man said:**
> Don't know about google music
libdvdcss(2) is a library not an app (unless you've gotten some app named that?

As far as  SpiderOak client - try browsing to /usr/share/applications and d. clicking on the "SpiderOak Backup" desktop file
It should startup and appear in the launcher, pin it and see if it survives a logout/in. (should
Libdvdcss, lol! I meant to say Handbrake.

Both Google Music Manager and SpiderOak appear in /usr/share/applications, I pinned them to the sidebar, and they survived reboot. But they're still not showing up with the other applications in the applications lens.

IDK, this doesn't seem like too much of a problem, but I'm afraid that this behavior will continue even after the stable release.

It's just perfectionism I guess...

---

### Post by mc4man on 2011-07-24
> but I'm afraid that this behavior will continue even after the stable release.
It shouldn't - atm there can be a wide variation between people's installs, -  (on a fresh install just now I installed it, your Spider Oak shows in a general dash search and directly in the internet category menu

---

### Post by MonolithImmortal on 2011-07-25
I had a similar problem eariler using Gnome shell. For a while whatever I installed past a certain point wouldn't show in Gnome Shell's dash and the only way to get it to work was to use alt+f2. After an update some days later everything started working fine again.

Wait it out for a while and see if an update fixes it. If not, reinstall from a newer image.

---

### Post by PhantmKllr on 2011-07-25
> **MonolithImmortal said:**
> Wait it out for a while and see if an update fixes it. If not, reinstall from a newer image.

Looks like I'll be doing just that... :popcorn:

---

