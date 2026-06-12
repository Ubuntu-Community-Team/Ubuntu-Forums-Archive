---
title: "default download manager"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by fazillatheef on 2008-05-20
Hi
I just got ubuntu hardy heron ... I wanted to know if there is a download manager in ubuntu by default.. the one with download accelerator..

if No ,Please provide me information on where I can get it... I used something called d4x but that was confusing... I used to use free download manager in windows

---

### Post by EXCiD3 on 2008-05-20
There isnt one included with Ubuntu by default. You should try gwget. You can install it by searching Synaptic or typing this in terminal:

```
sudo apt-get install gwget
```Once installed, it will be listed as &#8220;Download Manager&#8221; in your Applications->Internet menu.[]("http://gnome.org/projects/gwget/FireGet-0.6.xpi")

KGet is another download manager, but is geared for KDE integration. You can still run it on Gnome. Just search Synaptic for kget. Kget and the flashgot plugin in Firefox will allow you to automatically have the files download using Kget.

KGet is probably your best option if you dont mind installing part of the KDE libraries to allow it to run.

---

