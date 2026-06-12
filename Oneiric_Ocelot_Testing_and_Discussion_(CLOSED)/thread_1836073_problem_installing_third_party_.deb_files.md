---
title: "problem installing third party .deb files"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tadcan on 2011-08-30
Can anyone else confirm this?

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/836984](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/836984)

---

### Post by mc4man on 2011-08-30
While more common in Natty when lintian was a recommend, (lintian checks will still be run if installed), S-C (aptdaemon) still runs some basic checks on package quality.
So your packages are likely failing one or more of these ck.'s - to see which run 
software-center-gtk3 /path/to/whatever.deb

If you know the package is good and/or want to install anyway then use gdebi or dpkg

Ex.  if you were trying scrivener-beta_1.7beta-9_all.deb without lintian installed then - 
> The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

The package doesn't provide a valid Installed-Size control field. See Debian Policy 5.6.20.'


If lintian was installed then a whole host of errors...

---

### Post by tadcan on 2011-08-30
I was able to install it with Gdebi. That command you game threw up some issues as well. Still wasn't available in the dash. So looking in the terminal output I found where the icon was stored and could then launch it.

Edit, seems the deb doesn't have to be bad to have an error
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/712377](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/712377)

---

### Post by Enigmapond on 2011-08-30
You can also just create a launcher...

---

