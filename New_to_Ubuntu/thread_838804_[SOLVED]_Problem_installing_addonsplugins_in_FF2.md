---
title: "[SOLVED] Problem installing addons/plugins in FF2"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by stalkier on 2008-06-23
I believe I found a bug in FireFox 3 that was causing my system to crash. I installed FF2 and totally uninstalled FF3. I am trying to get addons/plugins installed on my ff2 but it comes up with an error. Here is a screenshot of an error.

[IMG]http://www.godsallaroundus.com/Screenshot.png[/IMG]

I am confused as why this would happen. Thanks for the help.

---

### Post by sharks on 2008-06-23
did u file the bug at launchpad.net

---

### Post by stalkier on 2008-06-23
> **sharks said:**
> did u file the bug at launchpad.net

No because I don't know the exact cause of the bug. Should I still send it?? And how?

---

### Post by sharks on 2008-06-23
yes try filing the bug.

---

### Post by stalkier on 2008-06-23
> **sharks said:**
> yes try filing the bug.

Bug #242534 in Ubuntu

Posted

---

### Post by stalkier on 2008-06-23
Ok so here is how I solved this.

Uninstalled and reinstalled. Again. Again. Still same problem. All this was done in Package Manager. All done with Complete Removal. When I would open it the bookmarks etc would still show even in a fresh install of FF2. I completely removed it. Rebooted. Then opened up the /home. I hit CTRL+H and then navigated to .mozilla. I deleted the firefox folder, closed the dir and then reopened Package Manager. I reinstalled FF2 and tried to install a plugin.  Boom worked like a charm. 

So now you know. Just in case you have this problem in the future. :D

---

