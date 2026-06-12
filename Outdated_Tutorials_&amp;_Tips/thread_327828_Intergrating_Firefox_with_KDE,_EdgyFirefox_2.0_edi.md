---
title: "Intergrating Firefox with KDE, Edgy/Firefox 2.0 edition"
date: 2006-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by NeoChaosX on 2006-12-29
Hey folks. I originally authored the original [integrate Firefox with KDE]("http://www.ubuntuforums.org/showthread.php?t=110353") how-to, which has helped quite a few folks get Mozilla's browser to play a bit better with KDE. However, since the release of Firefox 2.0, some of the solutions need to be updated.

So, if you want a Firefox that looks and feels a bit more like a KDE app than a GNOME app, follow along...

**1. Get rid of the GTK file picker**
This one is a big one for most folks. Thanks to the Red Hat developers that have worked on Firefox, the GTK filepicker is the one used in Linux Firefox. This one looks out of place in KDE, so you have two alternatives when changing the file picker.

**1.1. Use the old XUL filepicker**
This will replace the GTK file picker with the custom Mozilla-developer filepicker that was used in pre-1.0 versions of Firefox. This hack used to take a bit of hacking, but if you use Firefox 2.0, Mozilla has now made it easy to switch to this file picker. Simply go to your Firefox address bar and type in ```
about:config
``` Now, search for the config entry *ui.allow_platform_file_picker*. If such an entry doesn't exist, create a new boolean option with that name. Now, set this entry to *false* and restart Firefox. You will now get the simple old filepicker; not too fancy, but it beats the GTK filepicker.

*Note: If you use Firefox 1.5 or ealier, please refer to my older thread on how to get the XUL filepicker. The previous instructions only work for Firefox 2.0.*

**1.2. Use the real, honest-to-god KDE filepicker**
Yes folks, thanks to some enterprising hackers, you now can have the KDE file picker used in Firefox rather than the GTK or Mozilla file picker. This is achieved through the [KGtk]("http://kde-apps.org/content/show.php?content=36077") program, which you can get an Ubuntu Dapper (it also works with Edgy) deb at the following address: [http://www.insulae.com.ar/tmp/kgtk/kgtk_0.8-1_i386.deb](http://www.insulae.com.ar/tmp/kgtk/kgtk_0.8-1_i386.deb).

Now, install this package. This package installs a set of scripts that force a program to use the KDE filepicker whenever the GTK filepicker is called (It can be run on any GTK program, not just Firefox). To run this script with Firefox, run
```
/usr/local/kde/bin/kgtk-wrapper firefox
```This will get you an instance of Firefox that will open KDE file pickers whenever you need to open or save a file. However, **you must run Firefox with this script every time you want to run the browser to get the KDE dialogs**. That means you have to modify any Firefox shortcuts you have to include the KGtk script, otherwise you'll get just get the old GTK file pickers otherwise.

**2. Use a theme that matches your KDE theme and icons**
The new Firefox 2.0 theme is a bit controversial, but I've found that it blends in a bit better with the Plastik theme used in Kubuntu. As for icons, if you're like me and use the default Crystal iconset with KDE, you can get a Firefox 2.0-compatible theme with the current Crystal icons in [KDEFF]("https://addons.mozilla.org/firefox/3652/"). The only other Firefox 2.0-compatible theme with Crystal icons, Mostly Crystal, uses an older version of the iconset and doesn't fit in with KDE so well.

Sadly, if you use something other than Plastik + Crystal icons, you're going to have to search hard for some Firefox themes to match. Very few of the KDE-compatible themes (most notably Plastikfox) have been updated to work with FF 2.0 yet.

**3. Use KPrint as the printing interface for Firefox**
I'll just point to [this thread](http://www.ubuntuforums.org/showthread.php?t=205050) that explains it a lot better than I could. I prefer Firefox's default printing device (which works better in getting to the Samba-shared printer I use), but for those who like KPrint's options, you'll like the results of these steps.

This should help you get Firefox look and work a bit more like a KDE app.

---

### Post by NeoChaosX on 2006-12-30
bump for some updates

---

### Post by mjpoetic on 2007-01-01
> **NeoChaosX said:**
> set this entry to *false* and restart Firefox.

Nice HOWTO but you don't have to restart firefox

---

### Post by nrwilk on 2007-01-05
Just thought you might like to see what the people over at the Gentoo wiki have put together.  They've instructions on several other aspects of firefox/KDE integration.  Maybe something you'd like to include here too.

Anyway, here it is:
[http://gentoo-wiki.com/HOWTO_Integrate_Firefox_with_KDE](http://gentoo-wiki.com/HOWTO_Integrate_Firefox_with_KDE)

nrwilk

---

### Post by mexlinux on 2007-01-27
Than You!
Those gtk dialogs really lack of usefull options. This is great!

---

### Post by win32blows on 2007-05-04
Gnome's file viewer sucks balls... Too bad Firefox uses it. Anyways, that's fixed now!

gg

---

