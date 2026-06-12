---
title: "change value in xorg.conf using an instruction"
date: 2007-07-31
forum: Programming Talk
---

### Post by byenary on 2007-07-31
Hello,

Im changing some software (touchscreen calibration), i want to change values in the xorg.conf, is there an easy way to do this without using instructions like sed and all that..
I think there must be some package that can be used to change the values no ?

Grts

---

### Post by renzokuken on 2007-07-31
```
sudo nano /etc/X11/xorg.conf
``` to edit it manually

or

```
sudo dpkg-reconfigure xserver-xorg
``` to use the built in wizard

---

### Post by byenary on 2007-07-31
That was already a part of my knowledge, maybee i was not clear in my message,
For instance I have got a section in xorg.conf containing som options like 
option maxX = "300"
option maxY = "6000"

and more like that, now what i want to do is change these values using a script, so not manualy and not trough wizards...

---

### Post by AlexThomson_NZ on 2007-07-31
I can't think of a way without using sed.  Is there a reason (other than complexity) why you don't want to use bash commands?

---

