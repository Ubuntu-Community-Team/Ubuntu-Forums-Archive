---
title: "gnome panel running; no panels appear"
date: 2018-12-04
forum: New to Ubuntu
---

### Post by mwwilson72 on 2018-12-04
I have updated to various revs of ubuntu for about 10 years, but not for the joy of it. However, I've been working on this update for 5 days or so. Briefly, using the gnome metacity wm in ubuntu 18.04 (from 16.10 or so), I get nothing but background and a cursor - no panels, no time, no thing. I see gnome-panel is running, but if I killall it, it stays dead. sylog shows
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]: WARNING : Shell not installed or running
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]: WARNING : Error detecting shell
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]: Traceback (most recent call last):
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]:   File "/usr/lib/python3/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 216, in __init__
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]:     raise Exception("Shell not running or DBus service not available")
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]: Exception: Shell not running or DBus service not available
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]: WARNING : Shell not running
Dec  4 15:43:23 mwilson-MS-7817 gnome-panel.desktop[1862]: NoneType: None

I've removed and reinstalled it and am getting nowhere.

I'd be grateful for any help/

---

