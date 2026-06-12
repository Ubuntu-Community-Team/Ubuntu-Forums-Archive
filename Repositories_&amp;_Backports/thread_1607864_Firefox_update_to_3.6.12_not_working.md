---
title: "Firefox update to 3.6.12 not working"
date: 2010-10-28
forum: Repositories &amp; Backports
---

### Post by Crazedpsyc on 2010-10-28
I see that 3.6.12 is not in the main repository, but when I turned my computer on this morning Update Manager showed that there was an update from the launchpad Firefox ppa which I added through Ubuntu-Tweak. When I tried to install it all of the firefox packages other than xulrunner failed to upgrade. When i browsed place it is supposed to be in that ppa, the /f/ folder was empty. the ppa's url is [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu). Why did it say it was there for a short time and then disappear? after running sudo aptitude update the updates were completely gone.

Also, firefox 4 beta 6 fails to use the gnome theme. it is all gray and square. Here's it's output from the terminal:
```
07:34:48> /home/mike/ffox4.0beta/ffox
/usr/share/themes/Elegant-GTK/gtk-2.0/gtkrc:155: error: unexpected identifier `handlestyle', expected character `}'
FBL Fails TypeError: Cc['@joehewitt.com/firebug;1'] is undefined
If the service @joehewitt.com/firebug;1 fails, try deleting compreg.dat, xpti.dat
Another cause can be mangled install.rdf.
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
arg[0] = -c
arg[1] = test -n "$DISPLAY"
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
main 


checkForUpgrade

Unable to get manager service: TypeError: ManagerComponentService is undefined

Unable to get manager service: TypeError: ManagerComponentService is undefined

undefinedundefined*** e = [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utilityOverlay.js :: getShellService :: line 307"  data: no]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
unload

Unable to get manager service: TypeError: ManagerComponentService is undefined


```
Here is the line from [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+packages?field.name_filter=&field.status_filter=&field.series_filter=lucid](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+packages?field.name_filter=&field.status_filter=&field.series_filter=lucid)
> [         [IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 3.6.12+build1+nobinonly-0ubuntu0.10.04.1       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/1347946/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+files/firefox_3.6.12%2Bbuild1%2Bnobinonly-0ubuntu0.10.04.1_source.changes")                                 [chrisccoulson]("https://launchpad.net/%7Echrisccoulson")                        2010-10-27     Deleted     Lucid     Web            [IMG]https://launchpad.net/@@/yes[/IMG]

---

### Post by lovinglinux on 2010-10-28
I stopped understanding your questions after "than xulrunner failed to upgrade".

Version 3.6.12 is already available in the repositories, is just not available on all [mirrors]("https://launchpad.net/ubuntu/+archivemirrors") yet.

Disable the ubuntu-mozilla-security ppa, purge Firefox, replace your preferred server in Software Sources with a [mirror that is up-to-date]("https://launchpad.net/ubuntu/+archivemirrors") and install Firefox again.

---

### Post by Crazedpsyc on 2010-10-28
Thanks lovinglinux i changed to the main mirror and got lots of updates I didn't know about, any ideas about that theme error with ffox beta? I have been using that same version since the day it was released and it worked just fine until now.

UPDATE: this problem only occurs when using Elegant-Gtk controls theme.

---

