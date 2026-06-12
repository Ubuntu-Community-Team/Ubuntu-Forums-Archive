---
title: "HOWTO: Reinstall Compiz -- clean slate --"
date: 2007-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Ateo on 2007-05-11
As a fan of eye candy and to further the development of Compiz (hopefully, in some way), I've invested a few hours into Compiz. Needless to say, I've run into several issues giving way to simply reinstall Compiz from scratch and with a clean slate.

I wrote this because I had issues with Compiz saving settings between sessions and other odd anomalies so I thought I'd share my little method of 'starting from scratch'.

Ubuntu seems to be good at cleaning up when removing packages. So really, the trick to starting over with Compiz is clearing out all traces of it in the gconf database.

**NOTE**
I take no responsibility for anything that may incur to your computer if you follow this guide. Just back up your stuff before doing anything. That's always the safest.

**Step 1:** BACK UP YOUR DATA (your user directory at least)

**Step 2:** Shut off Desktop Effects
System -> Preferences -> Desktop Effects

Click on the big button that says "Enable Desktop Effects"

Yes, it says "Enable Desktop Effects" whether it is enabled or not. Just toggle it.

**Step 3:** Remove Compiz and Emerald, if applicable
```
$ sudo apt-get remove --purge compiz-core libemeraldengine0
```

This will remove the package desktop-effects and the metapackage ubuntu-desktop. This is fine as we will be reinstalling ubuntu-desktop later.

**Step 4a:** Clear Beryl from gconf database
If you experimented with Beryl, as I did, you might want to clear it from the database too.
```
$ gconftool-2 --recursive-unset /apps/beryl
$ gconftool-2 --recursive-unset /schemas/apps/beryl
```

**Step 4b:** Clear Compiz from gconf database
```
$ gconftool-2 --recursive-unset /apps/compiz
$ gconftool-2 --recursive-unset /schemas/apps/compiz
$ gconftool-2 --unset /apps/gnome-compiz-preferences
```

**Step 5:** Reinstall Compiz
```
$ sudo apt-get install ubuntu-desktop compiz-plugins
```

**Step 6 (optional):** Install Emerald for Compiz
You'll need to [start here]("http://ubuntuforums.org/showthread.php?t=423743") (Emerald for compiz-0.3.6 package). Mind you, this is completely unsupported. =)

FIN. That's it.

---

### Post by dansued on 2007-06-21
after unsetting the keys from the database, when I look in gconfiguration editor, the folder structures are still there. Is this ok?

---

### Post by midtown on 2008-06-15
Thanks for this nice thread! Any chance you or someone else could update it for Hardy? The references to the appearance dialog and beryl are dated.

---

