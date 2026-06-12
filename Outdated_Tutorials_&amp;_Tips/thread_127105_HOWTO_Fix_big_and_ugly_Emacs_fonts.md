---
title: "HOWTO: Fix big and ugly Emacs fonts"
date: 2006-02-08
forum: Outdated Tutorials &amp; Tips
---

### Post by katmandu on 2006-02-08
This one is simple. In file **/etc/X11/xorg.conf**, in sections "Files", put all 75dpi fonts dirs right before the 100dpi fonts dir, like this:

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/X11/fonts/100dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

This will make Emacs fonts smaller and better looking, without any changes in **.emacs** file, in wich some cases makes Emacs start slowly.

---

### Post by bryan.taylor on 2007-03-05
Thanks very much for the tip.  It's not as pretty as I would like, but I can live with it.

---

### Post by TheSoko on 2007-03-12
katmandu's fix didn't work for me. But apparently you can change the font emacs uses with the -fn argument, so I went into KDE's menu editor and changed it to this:

```

/usr/bin/emacs21 -i -fn -*-clean-*-*-*-*-14-*
```

---

