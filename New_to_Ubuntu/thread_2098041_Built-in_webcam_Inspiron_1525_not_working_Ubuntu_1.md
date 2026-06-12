---
title: "Built-in webcam Inspiron 1525 not working Ubuntu 12.04"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Roosmarijn on 2012-12-25
Hi,

A friend of mine installed ubuntu 12.04 after my laptop crashed. Now he cant recognize my webcam in skype or cheese (no device found). I've tried the following command:

[INDENT]**[FONT=Verdana]sudo rmmod uvcvideo[/FONT][FONT=Verdana]sudo[/FONT]** [/INDENT][INDENT][B][FONT=Verdana]modprobe uvcvideo

[/FONT][/B][FONT=Verdana]I get the following error:

ERROR: Module uvcvideosudo does not exist in /proc/modules
ERROR: Module modprobe does not exist in /proc/modules
ERROR: Module uvcvideo does not exist in /proc/modules

I'm not really familiar with ubuntu so I'm a bit lost.
Hope someone can help:)


[/FONT][/INDENT]

---

### Post by candtalan on 2012-12-25
Check that all updates are downloaded and installed? I find that camorama is better than cheese (from the Ubuntu software centre).
If no joy, maybe try a live 12.10, see if it is better?
hth

---

### Post by chris-rowanhome on 2013-10-06
I have the same problem.

Inspiron 1525

lsusb does not reveal camera

[FONT=Verdana]ERROR: Module uvcvideo does not exist in /proc/modules

[/FONT] camera not detected.

If this is not fixable - and as yet, I have found no help on internet, is there a workaround?

If I but a webcamera, is it likely to work? (considering uvcvideo does not exist message)

Help much appreciated

---

