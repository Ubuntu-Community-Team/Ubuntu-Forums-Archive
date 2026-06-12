---
title: "[SOLVED] I always out my foot into it! Fingerprint black screen"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-07-22
Could someone please tell me what terminal commands will restore the graphic interface on 8.04?
Background: Tried (unsuccessfully) to install Fingerprint Theme on usplash.  After reboot got only a black screen. Managed (thru Ctrl-Alt-F1) to restore Ubuntu splash screen but I can only get a tty for login and afterwards.  If I Ctrl-Alt-F7 I only get a black screen. Can toggle to tty1 etc.  GDM is running already but I can only see black.
Required: I have no idea how to restore graphics. Could anybody speak the magic words?:oops:

---

### Post by markjensen on 2008-07-22
If it is a bad X config, then **sudo dpkg-reconfigure xserver-xorg** wil probably do the trick.

---

### Post by HieroPosche on 2008-07-22
Have you tried 

```
$startx
```

Nevermind, note to self, read full post before making poor suggestions. :)

---

### Post by nuddernuby on 2008-07-22
Thank you, guys. What would we noobs do without you?

---

