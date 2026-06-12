---
title: "All process in background"
date: 2007-11-04
forum: Programming Talk
---

### Post by hithwen on 2007-11-04
To my surprise since a few days ago all the -window- processes you launch from a terminal are executed in background with no need of  '&', so you launch  $gedit  and  you get the prompt waiting for a new order without waiting gedit to finish.  This is causing me a little trouble because I'm programming a small shell at class (we have last year fedora installed) and I cannot test it properly at home (waitpid sentence simply doesnt wait)

Is that a bug or the last tencence?:confused:
The manpages about wait are from 2004, i think they'll need a bit update ;)

---

### Post by ankursethi on 2007-11-04
Try running those GUI apps in xterm instead of GNOME Terminal and see if the same problem occurs. Hit ALT+F2, type in 'xterm' and hit Return.

---

### Post by hithwen on 2007-11-04
Yes. it happens too, I tried before posting,( I must have told) and I also tried with my flatmate's computer with the same result :(. We both have an updated gusty installed

---

