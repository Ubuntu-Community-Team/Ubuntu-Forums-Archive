---
title: "Start on insert..."
date: 2010-04-12
forum: Programming Talk
---

### Post by carrarin on 2010-04-12
Hey everyone,

Im looking to do something very specific. I have files on my flash drive that i want to keep synchronized with files on my hard drive. Also, I would like to run applications off my flash drive. I want to create something like PortableApps for linux. 

So what I was looking for was a script that would be exected as soon as I plug in my device. 

Thanks...

---

### Post by labinnsw on 2010-04-18
I run my portable apps on both Linux and Windows. I am able to do so because my Linux system has wine installed.

Whenever I plug the USB Drive in, Nautilus opens a new window to browse the drive. I keep portableapps Menu launcher in /media/KINGSTON/. (KINGSTON being the USB Flash drive)

[Further information can be found here.]("http://ubuntuforums.org/showthread.php?t=1383329")

Save the following script as autorun changing KINGSTON to the name of your flash drive.

```
#!/bin/sh
/media/KINGSTON/StartPortableApps.exe
```

Hope this helps.

---

### Post by labinnsw on 2010-04-20
The final element to answering your question is this ```
[AutoRun]
OPEN=StartPortableApps.exe
ACTION=Start Portable Apps
ICON=
LABEL=KINGSTON
``` which makes it auto run on Windows XP and Vista.

Feel free to fill in or delete the ICON field. Save as autorun.inf

[The full document is here]("http://www.samlogic.net/articles/autorun-usb-flash-drive.htm")

---

