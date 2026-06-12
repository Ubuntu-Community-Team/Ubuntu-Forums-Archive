---
title: "Firefox 3 keeps crashing on gmail and when closing tabs"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Stefanie on 2008-06-13
Firefox 3 is crashing all the time, especially when i close a tab with CTRL-W and when i open gmail or close a gmail tab. it is really driving me crazy, i hope somebody knows a fix. 

I tried running firefox from the terminal and this was the output after a crash:
```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805f170: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f170: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f170: NP_GetValue
GCJ PLUGIN: thread 0x805f170: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f170: NP_GetValue return
GCJ PLUGIN: thread 0x805f170: NP_GetValue
GCJ PLUGIN: thread 0x805f170: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f170: NP_GetValue return
Segmentation fault

```

---

### Post by Joeb454 on 2008-06-13
I can't see why it would be segfaulting :confused:

Do you have any plugins enabled? If so try disabling these and seeing if the issue persists :)

---

### Post by Stefanie on 2008-06-13
i think i only have the default plugins that come with hardy, here's the list:
- default plugin
- demo print plugin
- DivX web player
- GCJ web browser plugin (using IcedTea)
- Helix DNA plugin
- iTunes application detector (i don't use itunes, though)
- quictime plugin
- shockwave flash
- totem web browser plugin
- VLC multimedia plugin
- Windows media player plugin

shoudl i really disable one of those? i still want to be able to watch vids and listen to streams...

btw i'm running firefox 3 RC1, the standard repository version.

---

### Post by Stefanie on 2008-06-13
i removed the GCJ plugin which was causing errors (using java SE 6.0 now), but that doesn't solve the problem.

---

### Post by MariusSilverwolf on 2008-06-13
There's another thread regarding this issue open here: [http://ubuntuforums.org/showthread.php?t=765322](http://ubuntuforums.org/showthread.php?t=765322)

Please reference my suggestions there.

---

### Post by Stefanie on 2008-06-13
according to the java site my java installation works fine. i'm already running FF RC1, i'll upgrade to RC 2 but i don't know if it will work. i had the same issue with beta5, and it didn't get any better with RC1...

---

### Post by Stefanie on 2008-06-13
i installed RC2, but it didn't help. same getvalue varible errors, same segmentation fault.

---

### Post by Joeb454 on 2008-06-13
You could try moving your ~/.mozilla folder - which would create a new profile, though I don't think that would help

---

### Post by Stefanie on 2008-06-13
i tried it, but it didn't help. i had exactly the same error after less than a minute (open three tabs, one of them gmail, close the gmail tab and it crashes) :-(

---

### Post by Joeb454 on 2008-06-13
This is strange.

Sorry I can't be of more help :( I've tried fiddling with many tabs (and a couple of gmails) but nothing unexpected happens.

---

### Post by Stefanie on 2008-06-13
i googled a bit and apparently the fault is with gmail's new version. the errors don't occur when i go to [http://mail.google.com/mail/?ui=1](http://mail.google.com/mail/?ui=1)  , which uses the old version instead of the newer one. 

check out this link: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/214817](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/214817)

> Marked invalid due to it being a google API issue not a Firefox bug, There isnt anything we can do about this at this time, Im waiting on responce fro google about support for Gecko/XULrunner-1.9

:-(

---

### Post by fakeollie on 2008-06-13
I have the exact same problems as Stephanie. Every single time I close a gmail tab, firefox crashes with a "Segmentation fault" error. I've tried disabling each plugin and extension, even using a blank state firefox (moving .mozilla elsewhere) the problem still occurs.

Steps to reproduce: 1) open firefox. 2) open a new tab. 3) load gmail in either of those tabs. 4) close the gmail tab. Firefox crashes.

Besides being incredibly annoying, I've noticed it also happens on other pages too, either while loading or closing tabs. It's really bad. I don't mean a crash once in a while bad. I mean, several crashes of firefox a day. I honestly don't remember the last time I actually closed firefox by myself.

---

