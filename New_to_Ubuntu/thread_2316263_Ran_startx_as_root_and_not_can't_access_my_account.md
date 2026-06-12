---
title: "Ran startx as root and not can't access my account"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by Andrei_Bleortu on 2016-03-06
Hi. I ran startx as root ( ](*,) ](*,) ) and now I can't access my account (graphically, I can use the text tty thing). I can enter the guest account. I don't have a live cd. I deleted my xauthority file (or this is what I believe). PLEASE HELP MEEEE!!!

---

### Post by Bashing-om on 2016-03-06
Andrei_Bleortu; Hello .

Let's see what we can find out.
What release are your running ?
What desktop are you running ?

Be aware that "startx' is mostly depreciated and is applicable in only a few instances ,, depending on the DE .

Post back the outputs - Between Code Tags - of terminal commands ( ctl+alt+F1 at the login screen) :
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /var/run/lightdm/root/ ##assuming you are running lightdm as the (D)esktop (M)anager##
ls -al /home/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And we see where we go from here.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]always fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

