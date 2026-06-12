---
title: "usb sound adapter"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by hifen on 2008-06-09
i was just wonding if there is any way to get a usb sound adapter,
ie: USB 2.0 to MIC Speaker 5.1 Audio Sound Card Adapter 552

to be the default sound card, or atleast work with media, and firefox.  It is detected in device manager, however not in system>prefernces>sound.

---

### Post by Xiong Chiamiov on 2008-06-10
Take a look through [the gigantor guide]("http://ubuntuforums.org/showthread.php?t=205449") on sound problems.

If you do a
```

asoundconf list

```
and see your card (probably listed as usb-something, it'll have to be plugged-in), then you can run
```

asoundconf set-default-card [card]

```
with [card] being what you saw you wanted in the previous command.

---

