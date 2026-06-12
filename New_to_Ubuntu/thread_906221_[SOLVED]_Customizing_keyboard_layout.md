---
title: "[SOLVED] Customizing keyboard layout"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-08-31
How do I customize a keyboard layout in Ubuntu?

I use the azerty keyboard layout ("be") but it lacks a tilde key.

How would I add a tilde symbol?

[http://en.wikipedia.org/wiki/Tilde](http://en.wikipedia.org/wiki/Tilde)

---

### Post by Elfy on 2008-08-31
Not sure if this will help but...

I had the £ missing from mine and got that working with a hint from [here]("https://answers.launchpad.net/ubuntu/+question/1719")

[This]("http://ubuntuforums.org/showthread.php?t=550680") page also goes into changing by using the default file in /etc/gdm/PostLogin, my default now shows
kevin@kevin-desktop:/etc/gdm/PostLogin$ cat Default
> #!/bin/sh
#
<snip>

xmodmap -e 'keycode 12 = 3 sterling'


I ran xev to get the correct (for my kbd) key event for ~
> KeyRelease event, serial 33, synthetic NO, window 0x2000002,
    root 0x161, subw 0x0, time 8874566, (340,126), root:(453,256),
    state 0x1, keycode 51 (keysym 0x7e, asciitilde), same_screen YES,
    XLookupString gives 1 bytes: (7e) "~"
    XFilterEvent returns: False


mine has the xmod line in now to get me £

---

### Post by billgoldberg on 2008-08-31
> **forestpixie said:**
> Not sure if this will help but...

I had the £ missing from mine and got that working with a hint from [here]("https://answers.launchpad.net/ubuntu/+question/1719")

[This]("http://ubuntuforums.org/showthread.php?t=550680") page also goes into changing by using the default file in /etc/gdm/PostLogin, my default now shows
kevin@kevin-desktop:/etc/gdm/PostLogin$ cat Default



I ran xev to get the correct (for my kbd) key event for ~



mine has the xmod line in now to get me £

Thanks for the info, but it seems that pressing "page down" in the terminal gives me a tilde symbol, so this is solved for me.

---

### Post by Elfy on 2008-08-31
Didn't know it was just the terminal you wanted it for, that would have been a shorter post...

---

