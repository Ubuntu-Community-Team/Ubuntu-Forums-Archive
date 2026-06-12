---
title: "[SOLVED] Could not uninstall Wine because Add-Remove froze"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by L a r r y on 2008-07-04
Hello,
[SIZE="5"]PROBLEM:[/SIZE]
I was not having much luck with Wine on my Ubuntu 
8.04, maybe because I hadn't read enough about how to
use it, and had some configuration issues.

I decided to uninstall Wine, but Add-Remove sat there
locked-up after I confirmed my decision to remove 
Wine.  The next window was supposed to pop up and 
sweep the progress bar back and forth while removing 
the software.  That window never appeared, and the 
mouse busy indicator just ran and ran whenever 
positioned over the stalled add-remove window.

I could move the stalled window to the next desktop 
workspace, and I could use other programs.  I could 
log out or restart and kill the add-remove process, 
but next time I tried to remove Wine again, it did 
the same freeze.

[SIZE="5"]SOLUTION:[/SIZE]
I discovered that Sudo could not resolve my host.  I 
had done some work with my networking configuration, 
and that is an area that I am not knowledgeable in.

Remembering I once before had asked about Sudo not 
resolving my host, in Terminal I performed a ```
sudo gedit /etc/hosts
``` and in gedit, I performed a find for: ```
127.0.1.1
```
There, I found the culprit:```
127.0.1.1 AMD.AMD
```
Supposed to be just **[SIZE="4"]AMD[/SIZE]**.

After fixing the host name, Wine was quickly removed.

I hope this helps somebody.

---

### Post by lazyart on 2008-07-04
I've been having problems with sudo hanging on me.  Unfortunately this didn't help.  I usually end up killing sudo via system monitor (from which a sudo window opens to confirm the kill-- which then gets the original sudo working again).

Anyhow, just to nitpick, when calling a gui app via sudo, one should use gksudo instead, so it should be```
gksudo gedit /etc/hosts
```Thanks for the tip.

---

