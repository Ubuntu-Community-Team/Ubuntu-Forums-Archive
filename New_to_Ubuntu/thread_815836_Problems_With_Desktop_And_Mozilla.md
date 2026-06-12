---
title: "Problems With Desktop And Mozilla"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by itsvan on 2008-06-02
Hey everyone,,i have a series of weird peculiar problems,,to start,,this kinda started happening after i did an update with the update manager,,,,,when i save a file unto my desktop nothing shows on my desktop at all,,for example lets say i save an image file,,nothing will show up,,the my mozilla firefox has gone berserk,,,all my saved sites are gone,,,and it wont let my save anything else on it as a short cut,,i cant set an image as a desktop background through Mozilla,(set as desktop backround)i have to actually save it and set it through the properties tab and all that,,,,i can tell my ubuntu is running rather akward,,but i dont know how to fix it or what it is. any tips,,greatly appreciate it.!!!

---

### Post by ConMan318 on 2008-06-02
As for the desktop, something may have gotten screwed up in a config file.  Try doing:
```

sudo gedit ~/.config/user-dirs.dirs

```

in the command line, and making sure the first uncommented line says something like
```

XDG_DESKTOP_DIR="$HOME/**Desktop**"

```

Make sure that bold part is in there; my only guess is that your directory is not set to put desktop files on the desktop, so adding in that bold part if it isn't there would fix it.

If that is already set correctly, you could try:
```

sudo dpkg-reconfigure ubuntu-desktop

```

If neither of those work, then I don't know how to help you.

And as far as Firefox being unable to set a desktop background, I have the same problem and have heard of others having it; I think it's just a glitch in the Beta version.

Good luck, hope you get it fixed.

---

### Post by Bubba64 on 2008-06-02
> **itsvan said:**
> Hey everyone,,i have a series of weird peculiar problems,,to start,,this kinda started happening after i did an update with the update manager,,,,,when i save a file unto my desktop nothing shows on my desktop at all,,for example lets say i save an image file,,nothing will show up,,the my mozilla firefox has gone berserk,,,all my saved sites are gone,,,and it wont let my save anything else on it as a short cut,,i cant set an image as a desktop background through Mozilla,(set as desktop backround)i have to actually save it and set it through the properties tab and all that,,,,i can tell my ubuntu is running rather akward,,but i dont know how to fix it or what it is. any tips,,greatly appreciate it.!!!

Have you opened desktop from places, there is a setting somewhere that I can't remember that keeps the basic desktop clean but if you open it from places the downloads are there. If your talking about bookmarks do a save with the bookmark drop down then hit bookmark and there is a drop down of 4 different places it can be saved, this is in FF3 you probably have saved them but in a different place. Are you using the launchpad release of ff3 rc1 it was updated to rc2 today and this might have changed where you save the bookmarks to. Also if anything was saved look in the home folder-in Mozilla are multiple bookmark backups.

---

### Post by itsvan on 2008-06-03
hey i already tried fixing it with (sudo dpkg-reconfigure ubuntu-desktop)
the problem is,,it comes and goes,,for example right now that problem seems to be doing ok,,i havent received it anymore,,but my mozilla is really messing up from time to time,,how can i update mozilla to fix it?,,,another thing that is starting to happen,,is after a while if my computer is on without it being used,,lets say half an hour,,il come back,,and everything messes up,,stretches, and rips through out everywhere,,its pretty insane,,i connect this with my video card, but i dont know what it can be,,any ideas?

---

