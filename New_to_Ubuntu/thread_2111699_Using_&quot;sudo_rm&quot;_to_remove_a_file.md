---
title: "Using &quot;sudo rm&quot; to remove a file"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by KunaKaranu on 2013-02-02
So Chrome won't load Adobe flash player at all and the supposed work around I found said to delete ~/.config/google-chrome/PepperFlash. Couldn't find it. Therefore looking at Chrome's plug in's I found PepperFlash at /opt/google/chrome/PepperFlash. Anyways now I'm trying to delete the folder and it's contents but it is root owned. Using "sudo rm" I try to delete the folder or even the individual contents and the terminal states "No such file or directory."
I'm frustrated but still determined to learn to use linux. Help please?

Lenovo Z570
Intel i3-2310m @2.1
Mem 4Gb
Stor 800Gb
Ubuntu 12.10
Gnome 3.6
Kernel 3.5.0-23

---

### Post by nothingspecial on 2013-02-02
But the workround said to delete ~/.config/google-chrome/PepperFlash

not

/opt/google/chrome/PepperFlash

---

### Post by Dodeca on 2013-02-02
> **KunaKaranu said:**
> So Chrome won't load Adobe flash player at all and the supposed work around I found said to delete ~/.config/google-chrome/PepperFlash. Couldn't find it. Therefore looking at Chrome's plug in's I found PepperFlash at /opt/google/chrome/PepperFlash. Anyways now I'm trying to delete the folder and it's contents but it is root owned. Using "sudo rm" I try to delete the folder or even the individual contents and the terminal states "No such file or directory."
I'm frustrated but still determined to learn to use linux. Help please?

Lenovo Z570
Intel i3-2310m @2.1
Mem 4Gb
Stor 800Gb
Ubuntu 12.10
Gnome 3.6
Kernel 3.5.0-23

if I wanted to see better what I was deleting I would go GUI ...

on a terminal ... gksudo nautilus

---

### Post by deadflowr on 2013-02-02
That particular workaround is somewhat silly.

The easier way is to open up chrome and in the address bar put:

```
chrome://plugins
```

click the plus sign next to details and then scroll to the adobe shock flash and click on the disable link for ver 11.5. This will disable it.

When disabled simply reload whatever page you're on.

If you've install flash on Ubuntu, either through the flashplugin-installer, or the Ubuntu-restricted-extras package, disabling pepperflash will have seemingly no adverse effect on viewing or using flash content.

Removing files should always be a last resort.

---

### Post by Frogs Hair on 2013-02-02
Thanks ! I just posted on another thread for the same issue and suspected Pepper but wasn't sure.

---

### Post by KunaKaranu on 2013-02-02
Thanks Deadflowr. At first just disabling libpepflashplayer didn't work because it disabled Adobe Flash as well, giving the standard "Need Adobe Flash 9 or above" Though by installing Adobe Flash from the Software center and then disabling libpepflashplayer did everything work. 
I feel so... ready for the next time everything goes to heck. Of course now I jinxed it and the root directory will delete itself and the computer will blow up.

---

### Post by deadflowr on 2013-02-02
> **KunaKaranu said:**
> Thanks Deadflowr. At first just disabling libpepflashplayer didn't work because it disabled Adobe Flash as well, giving the standard "Need Adobe Flash 9 or above" Though by installing Adobe Flash from the Software center and then disabling libpepflashplayer did everything work. 
I feel so... ready for the next time everything goes to heck. Of course now I jinxed it and the root directory will delete itself and the computer will blow up.

Yeah, disabling pepper and using the system-wide flashplugin only works if you have system-wide flash. Otherwise you get nothing.

---

