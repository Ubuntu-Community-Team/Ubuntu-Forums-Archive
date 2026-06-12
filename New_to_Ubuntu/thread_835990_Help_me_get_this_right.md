---
title: "Help me get this right"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by jenova_skill on 2008-06-21
Ok a few things here..... The sticky post's are very helpfull and all the guides. 
I got my sound 2 work.......reloaded some things ( from a post)  My headphone jack however doesn't.....
I notice on my *unsupported* restricted driver deal i only have a display/network/hal  driver
No sound driver or nething else.... Is this supposed 2 be this way?
Would this be lack of driver? or somethin simple or tough 2 get done?

---

### Post by rudihawk on 2008-06-21
Which version of ubuntu are you using?

---

### Post by Nepherte on 2008-06-21
What is your soundcard? What laptop if it is one?
```
lspci | grep audio
```

What is the codec of your card?
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

