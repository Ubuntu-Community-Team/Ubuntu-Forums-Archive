---
title: "Update manager doesn't display update description"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by ENigma885 on 2012-04-21
As the title suggests, when I open the update manager, it displays the available updates normally and installs them properly as well. The problem is that nothing is displayed in the "Description of update" area except for a line saying "Downloading list of changes" and the mouse pointer turns into loading form when hovering over the update manager.

**[COLOR="Red"]what I tried:[/COLOR]**
**1- **Launched from command line and got the same result
```
CheMG@Melancholie-Notebook:~$ update-manager

(update-manager:458): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:458): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:458): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:458): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:458): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:458): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

```
**2- ** Tried to reach the change logs from command line, and as expected after app 3 min I got the following
```
CheMG@Melancholie-Notebook:~$ apt-get changelog flashplugin-downloader
Err Changelog for flashplugin-downloader (http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_11.2.202.233ubuntu0.11.10.3/changelog)
  Connection failed
0% [Waiting for headers]

```
**3- ** Changed my update server from my local one to US' and the main server, but didn't fix the problem.

---

