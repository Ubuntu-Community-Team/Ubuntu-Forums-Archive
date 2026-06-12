---
title: "suspend works only on one computer"
date: 2019-06-07
forum: New to Ubuntu
---

### Post by findiklun on 2019-06-07
Hi 
Running Ubuntu on USB stick and suspend works only on one computer, i have three laptops. When sent to sleep the screen turns off, but the fan is spinning. There is only one option to press and hold power button until it shuts down.

---

### Post by kurt18947 on 2019-06-07
I make no claim this will work but there's no harm as far as I know. I have some 18.04 installs where shutdown is slow and after some reading found this. When you say you're running Ubuntu on a USB stick are you running a live distro or a full install on a USB stick? That might matter, I don't really know. Anyway, here's a command to try in a terminal:

```
systemctl suspend -i
```

I set up a keyboard shortcut so I press one key or an easy-to-remember combination that is not used for another keyboard shortcut. I assigned this shortcut to my 'pause' key. Pause doesn't appear to do anything else.

---

### Post by findiklun on 2019-06-10
Hi I'm running a USB with persistence, will try this thanks a lot.

---

### Post by findiklun on 2019-06-11
no still the same.

---

