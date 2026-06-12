---
title: "Python script file (*.py) on USB drive"
date: 2013-12-09
forum: Programming Talk
---

### Post by Resistent on 2013-12-09
I have a Python script program on the harddrive. Executing works, program starts. OK


[IMG]http://loerincz.eu/ubuntu/Screenshot from 2013-12-09 18:15:52.png[/IMG]


Copying the same program to an USB stick, [COLOR=#ff0000]Execution don't work[/COLOR]. [COLOR=#FF0000]--> Why ?[/COLOR]
(but I also did ```
chmod +x keryx
```



.. That's in the LXTerminal 0.1.11 of Lubuntu. I don't know yet why colors are different handled...
must not because keryx is not executeable.. the AUTHORS and COPYING for example are also not green on the USB drive)


[IMG]http://loerincz.eu/ubuntu/Screenshot from 2013-12-09 18:17:44.png[/IMG]


thx for your answers

---

### Post by steeldriver on 2013-12-09
Probably because the USB drive is formated with a filesystem (FAT / NTFS etc.) that doesn't support Unix-style permission bits. You should still be able to execute it by specifying the python interpreter on the command line i.e.

```
python keryx
```

---

