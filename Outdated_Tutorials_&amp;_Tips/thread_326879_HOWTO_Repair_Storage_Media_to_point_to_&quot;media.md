---
title: "HOWTO: Repair Storage Media to point to &quot;media:/&quot; instead of &quot;/media&quot; in System Menu"
date: 2006-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by PacShady on 2006-12-28
Since this is a major problem in Edgy that many people have been unhappy with, and since it seems no one has found a way to fix it, after many hours Googling stuff on KDE I managed to find a way to change "Storage Media" in the System Menu of KDE to point Konqueror towards "media:/" instead of "/media".

The file lies in the /usr/share/apps/systemview directory, and is called "media.desktop". Open this file using root privileges and edit the line that says "Path=/media" (up near the top) to say "Path=media:/". Restart the X server (Ctrl-Alt-Backspace). Voila, fixed menu! You can also add stuff to this directory if you want to add new icons to the System Menu.

'Shady

---

### Post by Ranma on 2007-01-01
That was one of my biggest problems on Edgy and I also found the same solution, however another of my problems (unsolved until today) is that the device icons on desktop are also pointed to /media/mountpoint instead of media:/device, and when I do double click none of the devices are mounted, the only workaround to mount them is doing right click and then mount, but as the devices are pointed to /media/mountpoint instead of media:/device the mount monitoring is very poor and inacurate...
Have you been experiencing something similar like me?

Thanks in advanced and sorry to bother](*,) 

Ranma

---

### Post by PacShady on 2007-01-01
Unfortunately, I can't help you with that, since I usually use the Storage Media and only realised the same problem as you once you mentioned it and I checked for it. I'm still using Dapper (too many problems in Edgy for me to change over), but I recently upgraded KDE to 3.5.5 and now have similar problems within KDE as Edgy. I'll have to look into this, and see if I can find out what's causing it, and hopefully how to fix it.

'Shady

---

