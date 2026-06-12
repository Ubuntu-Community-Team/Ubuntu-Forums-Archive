---
title: "My mouse side buttons &amp; FF3B5"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by msayed2004 on 2008-04-28
I know about that related bug and I know that I have to manually edit my xorg but following some topics about it (topics found by Googling) I can't get it work :( !

Here is my mouse portion of the xorg :```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
        Option "Buttons"         "7"
        Option "ButtonMapping"   "1 2 3 6 7"
        Option "ZAxisMapping"    "4 5"
    Option "Emulate3Buttons" "no"
EndSection
```The current configuration work for Firefox 2 & Opera.

If needed my mouse is [A4Tech BW-26]("http://www.a4tech.com/ennew/product.asp?cid=1&scid=8&id=187").

I don't care about Nautilus, I just want this for Firefox 3

Thanks :)

---

### Post by cubiclegangsta on 2008-04-28
hmmm. not sure. BUT, there was an interesting how-to using app "btnx" over on lifehacker here: 

[http://lifehacker.com/384698/btnx-customizes-a-multi+button-mouse-for-linux](http://lifehacker.com/384698/btnx-customizes-a-multi+button-mouse-for-linux)

It looks relatively straight forward and may be worth a try.

Good luck.

---

### Post by msayed2004 on 2008-04-29
Amazing tool, it works & now the side buttons work for Firefox & Nautilus!

---

