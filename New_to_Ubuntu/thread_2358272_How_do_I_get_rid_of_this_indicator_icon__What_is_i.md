---
title: "How do I get rid of this indicator icon?  What is it?"
date: 2017-04-11
forum: New to Ubuntu
---

### Post by Weltall900 on 2017-04-11
Here's a photo of my desktop.  Can someone tell me what this icon is?  Running Lubuntu.  Whenever I click it, it does nothing.  [https://snag.gy/MFZvIA.jpg](https://snag.gy/MFZvIA.jpg)

I really just want to get rid of it

[IMG]https://snag.gy/MFZvIA.jpg[/IMG]

---

### Post by vasa1 on 2017-04-11
[LIST]
[*]Please use the forum's attachment facility to post images rather than some third party image hosting site. To do so, click on the paper clip icon above the posting area.
[*]The icon you want us to look at is indistinct!
[*]Have you hovered your mouse pointer over that icon? Don't you see an explanatory tooltip?
[*]What happens if you right-click that icon?
[*]What happens if you right-click on lxpanel and then open "Add/Remove Panel Items"? Is it listed there?
[/LIST]

---

### Post by Weltall900 on 2017-04-11
It's actually for dropbox.  I figured that out by isolating it in the autostart.  Whenever I hover over it or click on it, nothing happens.   I still want the Dropbox program to autostart, but I don't need it showing in the system tray.  so how do I disable the indicator icon?  especially since its not displaying correctly anyways.

---

### Post by vasa1 on 2017-04-11
How did you install Dropbox? Do you know its version number? What version of Lubuntu are you on?

If it's really the Dropbox icon, right-clicking should offer quite a few options. Just hovering over it should give you the version number.

Which icon set are you using? Is it the default that comes with Lubuntu?

I don't know that one can prevent an icon for a running application from showing up in the system tray. Maybe someone else has thoughts on the matter.

---

### Post by Weltall900 on 2017-04-11
I installed Dropbox from downloading it via the dropbox website.  Latest dropbox & lubuntu build.  Just installed both today.  It doesn't give any options.  Whatever is default in lubuntu

---

### Post by vasa1 on 2017-04-11
I can confirm what you see: image attached. For whatever reason, there's no response by left-clicking or right-clicking on that weird icon (fourth icon from the left)! I just checked that by logging into a Lubuntu session. I normally use the Openbox session and, in that, I use tint2 rather than lxpanel. There, the Dropbox icon is decent and responsive though I haven't tried making it vanish. I prefer to have it visible.

---

### Post by Dennis N on 2017-04-11
Right click on indicator applets area and select "Indicator Applets Settings". A dialog appears with various check boxes. Uncheck one and see what disappears (if anything). Some applets like power manager have their own dialog if you right click on the icon, which may have an option to show or not show system tray icon.

---

### Post by vasa1 on 2017-04-11
I killed my tint2 panel and launched lxpanel instead in my Openbox session. The Dropbox icon is behaving normally, the way it does in my tint2 panel. And, as I said before, I'm not sure there's a simple way to selectively *not show* something in the system tray.

Edit: I could confirm the image is what I think by starting dropbox via the terminal and seeing which icon appeared.

---

### Post by vasa1 on 2017-04-12
If I look at the dropbox icons provided by the Lubuntu icon theme (in /usr/share/icons/Lubuntu), this is what I see:
```
grep -ir dropbox
Binary file icon-theme.cache matches
apps/48/dropbox.svg:   sodipodi:docname="dropbox.svg">
apps/24/dropbox.svg:   sodipodi:docname="dropbox24.svg">
apps/64/dropbox.svg:   sodipodi:docname="dropbox.svg">
apps/22/dropbox.svg:   sodipodi:docname="dropbox22.svg">
apps/16/dropbox.svg:   sodipodi:docname="dropbox16.svg">

```So the Lubuntu icon theme provides images as svg files. Further, there's just the one image (scaled differently).

Now, if the user installs Dropbox directly from dropbox.com (no *sudo* involved), there'll be *~/.dropbox-dist/dropbox-lnx.x86_64-23.4.18/images/hicolor/16x16/status* with the following files (on my system):```
-rw-r--r-- 1 vasa1 vasa1  942 Apr  6 22:30 xdropboxstatus-blank.png
-rw-r--r-- 1 vasa1 vasa1 2016 Apr  6 22:30 dropboxstatus-busy2.png
-rw-r--r-- 1 vasa1 vasa1 2016 Apr  6 22:30 dropboxstatus-busy.png
-rw-r--r-- 1 vasa1 vasa1 2034 Apr  6 22:30 dropboxstatus-idle.png
-rw-r--r-- 1 vasa1 vasa1 1778 Apr  6 22:30 dropboxstatus-logo.png
-rw-r--r-- 1 vasa1 vasa1 2026 Apr  6 22:30 dropboxstatus-x.png

```They are all png files, not svg. At some point, svg images stopped working.
Secondly, there are six different icons. The Lubuntu icon theme provides only one!

---

