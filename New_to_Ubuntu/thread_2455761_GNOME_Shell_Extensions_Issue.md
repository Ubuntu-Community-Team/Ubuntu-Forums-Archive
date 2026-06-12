---
title: "GNOME Shell Extensions Issue"
date: 2020-12-26
forum: New to Ubuntu
---

### Post by iamdarthmole on 2020-12-26
So I'm trying to install some GNOME Shell Extensions. I'm running Ubuntu 20.04 on the Dell XPS 9310 Developer Edition (so Ubuntu came preinstalled).

I followed the instructions found on here ([https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation](https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation))

When I use the install chrome-gnome-shell command I get the following result: chrome-gnome-shell is already the newest version (10.1-5).

I have installed the Chrome browser extension on the Chromium browser. 

I have restarted the machine and also followed instructions to ALT+F2 and then r and enter to restart GNOME Shell.

However, I'm still getting the following error when I load extensions.gnome.org "Although GNOME Shell integration extension is running, native host connector is not detected. Refer documentation for instructions about installing connector."

I'm not syncing my google account and I'm not logged in. I'm also not logged in to gnome.org (I though I read that is only needed for commenting). 

I've tried searching for the solution but everything save for a couple of sites I tried the steps on simply say to install chrome-gnome-shell which I've already done. Sorry if I've missed something simple and thank you in advance for any help and your time!

---

### Post by deadflowr on 2020-12-27
It's this:
[https://forum.snapcraft.io/t/chrome-gnome-shell-does-not-work-with-chromium-snap/3377/2]("https://forum.snapcraft.io/t/chrome-gnome-shell-does-not-work-with-chromium-snap/3377/2")
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1741074]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1741074")
In simple terms Ubuntu ships chromium as a snap package which does not have access to the chrome-gnome-shell functions, currently.
The solution is to run a non-snap version of a browser that can access the chrome-gnome-shell such as firefox or even google-chrome.
(For firefox is must be the non-snap version Ubuntu ships by default.
For google-chrome you can only get that from Google directly, as it is not packaged in Ubuntu archives.)

There are probably other workable browsers that can do it too as long as they are not snap versions.

---

### Post by dino99 on 2020-12-27
Via 'synaptic' (install it if not yet done) search for 'gnome-shell-extension-the.one.you.want' and select it for installation.
'gnome-shell-extension-ubuntu-dock' will install a few extensions.
This works with the default snap chromium package, but only after activation via gnome-tweaks (install it too).

---

