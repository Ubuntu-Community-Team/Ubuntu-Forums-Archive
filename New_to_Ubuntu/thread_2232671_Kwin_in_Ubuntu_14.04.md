---
title: "Kwin in Ubuntu 14.04"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by misswham2 on 2014-07-03
I am using Ubuntu 14.04 now and I lost a lot of my effects with compiz like fire and exploding windows.  I saw a video this morning on KWIN and it said it was a good alternative to compiz, my question is, can I use KWIN with 14.04 instead of compiz and I think im using gnome?

---

### Post by philinux on 2014-07-03
Install the compiz-plugins package. It's not installed by default.

---

### Post by misswham2 on 2014-07-03
I did install it and the fire and explode arent showing up in 14.04.

---

### Post by QIII on 2014-07-03
If it's any consolation, I don't see them in Kubuntu either.

There is a "Fall Apart" effect, but no pyrotechnics.

---

### Post by grahammechanical on 2014-07-04
Kwin, I understand is the window manager/compositor for KDE. It does for Kubuntu (KDE-Ubuntu) what Compiz window manager/compositor does for Ubuntu. I do not think that the KDE developers are designing Kwin to be a replacement for Compiz on the Gnome desktop environment. Be prepared to re-install as trying to fix any problems will be more trouble than its worth.

[http://userbase.kde.org/KWin](http://userbase.kde.org/KWin)

Regards.

---

### Post by Rob Sayer on 2014-07-04
I may not be the best person to comment on eye candy programs because when I install ubuntu that's one of the first things I turn off, not only on this little 1gb netbook running xubuntu but the laptop I mostly use at home, which runs kubuntu and is actually powerful enough to reasonably use effects.  I don't use unity myself either.

But I can definitely agree that kwin is the KDE window manager, and installing it for some effects isn't going to help matters in unity.  I'm not necessarily saying it couldn't be done but it'd be a real bucket of worms, and trying to find a plugin designed for the task as mentioned before would be much better.

Just be careful about setting up ppa's for something like that.  Some aren't reliable.

I'm not surprised it didn't make any difference.  Just installing it wouldn't.  You'd have to reconfigure your system.  Which I am NOT suggesting you do.

You also probably also installed most of the KDE desktop runtime environment along with kwin.  KDE  is a highly integrated DE.  You can't avoid that.  I actually use dolphin for a file manager in everything linux and it pulled in a ton of it, which is worth it for me because I just don't want to use any other file manager.  I also install the KDE archiver and terminal so the file manager services don't have to be configured for something else.

Myself, I'd just purge kwin and autoremove.  But be careful about that if you haven't done it before.

---

