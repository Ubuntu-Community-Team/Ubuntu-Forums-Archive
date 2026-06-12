---
title: "lost max min close rt cl"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-08-25
I finally got brave and ran clonezilla today on my Ubuntu 12.04 classic. I was careful to exit just as they said to. Now I have numerous problems 1) on all apps the max min close buttons are gone.2) rt click doesn't work 3) at boot I get disk #long number is missing then it boots OK. I am currently logged into xfce session and that doesn't have the above problems.This is a huge irritant as I can't close firefox or gnome tweak. I can't even use the firefox or chrome menus as when I click on a menu it disappears as soon as I try to select something.Also all my firefox bookmarks bar items are gone but again only in classic not xfce However firefox works fine in xfce so it isn't a firefox issue. It is somehow related (I think ) to the window manager for gnome classic but not for xfce. I need some commands to try. I tries restoring through Ubuntu Tweak to no effect.I also just reinstalled gnome-fallback to no effect. Thank you PS below is a copy of my
cat /usr/share/gnome-session/sessions/gnome-classic.session[GNOME Session]

```
 [GNOME Session]
Name=GNOME Classic
RequiredComponents=gnome-panel;gnome-settings-daemon;
RequiredProviders=windowmanager;
DefaultProvider-windowmanager=gnome-wm
DefaultProvider-notifications=notify-osd
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
FallbackSession=gnome-fallback
DesktopName=GNOME
```

---

