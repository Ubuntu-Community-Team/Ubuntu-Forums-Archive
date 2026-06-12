---
title: "Mini-HOWTO: Migrate Xfce-Settings (Xubuntu)"
date: 2006-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by mättu on 2006-11-01
This describes how to migrate your settings from one machine / install to an other, same version given.
This has not been tested between different versions of Xubuntu / xfce.

Close all applications.
Choose "show hidden files" from "view" in thunar (file browser)
On your old install back up all config directories. They all begin with a dot:
.config, .xmms, .xxx
You will need them later on for your new install.
On your new install backup all config-direcotries (for safety reasons..)

The following steps are done on the new install.

Panels, settings etc
--------------------
Erase .config
copy "old"/.config -> .config
Quit session using alt+ctrl+backspace 
(This is important because some settings are overwritten when exiting through "log-off-button", even if you unchoose to "save session".)

Themes
------
You need to copy
.themes and .icons
if you have special themes and icon-themes installed.
If your theme uses a special gtk-engine, you may need to install it. 
Search for "engine" in .themes/"your-theme"/gtk-2.0
There may be more than one engine needed.
If unsure, you may want to install "all" gtk-engines using synaptic:
Search for: gtk2-engines, choose them & install. As far as I know it does not harm to have too many engines installed.

Fonts
-----
Copy ".fonts" from the old install.
There seems to be an issue with openoffice replacing some standard-fonts (arial e.g.). Fix for arial:
erase all arial-fonts from .fonts and install msttcorefonts

Other settings
--------------
I succeeded to restore nearly all of my application settings by just copying their settings folders, .mozilla for firefox, .mozilla-thunderbird for thunderbird, .openoffice.org2 for openoffice ...
Just be careful to keep the original settings in a safe place if anything goes wrong. (new versions etc.)

Warning
-------

There are folders you possibly shouln't move, because they contain information about your install. So just move what you need and don't copy everything to your new install. Remind that if you screewed up something on your old install it might be a config-issue. 
If you copy the "bad" config-files to your new install it may stop to work as well..

As always in live: Be careful and have fun.
:m)

---

