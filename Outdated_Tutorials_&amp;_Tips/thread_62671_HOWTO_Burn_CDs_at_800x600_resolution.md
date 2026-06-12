---
title: "HOWTO: Burn CDs at 800x600 resolution"
date: 2005-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by eivind on 2005-09-05
This howto may be useful only for very few nowadays. :razz: It's about finding a good CD burning application when you are limited to an 800x600 display, e.g. an elderly laptop or desktop. One would think it simple to burn CDs on such machines, but surprisingly enough, few such apps are fit to run at 800x600.

My demands for a good CD burning application in 800x600:
- Must at least fit on screen without the need for scrolling sideways
- Must work without acting too much like a vacuum cleaner :wink: 
- Must find my CD burner
- Must be able to copy from CD to CD, and to burn audio CDs from ogg/mp3
- Must be available as a Debian/Ubuntu package, installable on Ubuntu 5.04
- Must not be entirely command line driven

Only Graveman fills all of these demands, but Arson, Gcombust and Bashburn come rather close. Below follows a full list of all the apps I've tried, so you can see what fits you. Personally, I alternate between Graveman and Bashburn.


**Graveman.** Pros: Well... all! It fills my entire list of demands, and it looks nice. This is powerful and simple enough for me. Nice work. It deals with data DVDs too, and although I personally don't need that, it's definetely a bonus.

**Gcombust.** Pros: Fits nicely in 800x600, fills almost all demands, but has one big con: doesn't burn directly from mp3/ogg.

**Arson.** Pros: The main window fits somehow in 800x600, and it works nicely in most ways. Cons: The preferences window doesn't fit on screen at all, and you have to fiddle an awful lot to make changes to the setup. Also, as this is a KDE package, it brings about 97 MB of kdelibs with it on a standard Ubuntu install.

**Bashburn.** Pros: Nicely laid out app, easy to use and like, small and effective, fits on screen. Cons: Isn't a Debian/Ubuntu package, so it has to be downloaded and installed manually. While that isn't too hard, it has to be done, and I prefer to use apt-get/synaptic for installing and removing things. There are Debian packages available - for some Debian variant that doesn't go well with Ubuntu, and has all sorts of silly dependency problems. This should definetely be an Ubuntu package, but for now, you have to download it from bashburn.sf.net.

**K3b.** Pros: A beautiful cd burning app, sleek and easy to use. Cons: Has too much graphics to go well on my screen, and brings even more dependencies than Arson with it.

**Gnomebaker.** Pros: Works reasonably well, installs cleanly, as it is a Gnome app. Cons: Doesn't fit on my screen, and has had some issues.

**Gcdw.** Pros: Seems to work, fits nicely on screen. Cons: You can't change the preferences when you work in gterm, because it wants you to use f10 - and that's the File menu shortcut in gterm! Argh. Looks ugly, too.

**Xcdroast.** Pros: Works in other resolutions... Cons: Won't even start in 800x600, and I don't intend to fiddle about to find out how! I don't use apps that tell me I can't use them. Argh.

**Eroaster.** Pros: Slightly usable. Cons: Doesn't fit well in 800x600, and looks ugly.


Well. Hope this can be of use to 2 or 3 of you  ;-) - I'm happy if it can be!


Cheers,

Eivind

---

### Post by njmf on 2005-12-10
Excuse me for idiotic question, but why is Gcombust in red?

---

