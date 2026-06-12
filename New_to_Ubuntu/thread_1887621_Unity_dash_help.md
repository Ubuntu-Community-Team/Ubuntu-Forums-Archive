---
title: "Unity dash help"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by James.A.Parnell on 2011-11-27
I have a problem with unity, i have created a .desktop launcher for Portal (running through wine) and i have added it into the launcher and ticked "Keep in launcher"

but if i remove the shortcut on the actual desktop, it gets removed...what can i do to fix this? 

Im running 11.10.

Please help if you can :)

---

### Post by JazzPotato on 2011-11-27
Do you mean the actual files for portal get removed? And could you please tell me how you've got portal working? Is it steam or a disc, i could never get mine to work...

---

### Post by James.A.Parnell on 2011-11-27
No steam or install. just downloaded a torrent ( will send you link in pm) and ran with a .bat file via wine. And no, just the shortcut i created vanishes. not the desktop one (the once you actually create) the one that i dragged into the launcher. then when i followed up by removing the desktop icon, the launcher icon vanishes also..

---

### Post by James.A.Parnell on 2011-11-27
Attached some screenshots to roughly show you what i mean

---

### Post by JazzPotato on 2011-11-27
Perhaps it is just a bug with launchers. You could try reporting it or try making a launcher to something different and seeing what happens. 11.10 is still quite a young release so bugs are to be expected! Thanks for the link :D

---

### Post by JazzPotato on 2011-11-27
Ah i see what you mean. You want it on the launcher and not on the desktop. Perhaps you could create it in the documents folder where it wont show up on the desktop and then drag that one into the launcher.

---

### Post by James.A.Parnell on 2011-11-27
Ive just tried it with a random launcher to a random image..and same result.

Thanks for trying to help though lol, much appreciated. Let me know if it works, all i know is with the Beta of wine and that torrent, it runs perfectly. (i do have to use the "Mypcsucks.bat though because the other one doesnt play sound for me :( )

---

### Post by JazzPotato on 2011-11-27
Ah i see what you mean. You want it on the launcher and not on the desktop. Perhaps you could create it in the documents folder where it wont show up on the desktop and then drag that one into the launcher.

---

### Post by James.A.Parnell on 2011-11-27
Ive just tried it with a random launcher to a random image..and same result.

Thanks for trying to help though lol, much appreciated. Let me know if it works, all i know is with the Beta of wine and that torrent, it runs perfectly. (i do have to use the "Mypcsucks.bat though because the other one doesnt play sound for me :( )

---

### Post by VeeDubb on 2011-11-27
The desktop is not the best location.

instead, save it to:

/home/yourusername/.local/share/applicaitons

From there, it will show up in the dash, and like any application in the dash, you can drag it from the dash to the bar.

---

### Post by James.A.Parnell on 2011-11-27
Woooo, thanks. worked straight away :D :D :D

---

### Post by James.A.Parnell on 2011-11-27
Ooh no, i got a bit carried away, my original question is answered but when i click on it it just flashes..and i still have to load the .bat manually from its original folder


When i changed it from "Application" to "Application in terminal" (it runs a term command to start up) i get a permission denied error ;/)

---

### Post by corncob on 2011-11-27
> **VeeDubb said:**
> The desktop is not the best location.

instead, save it to:

/home/yourusername/.local/share/applicaitons

From there, it will show up in the dash, and like any application in the dash, you can drag it from the dash to the bar.

All that is in that folder on my system is one file, mimeapps.list who's content is
```
[Default Applications]
x-scheme-handler/mailto=thunderbird.desktop

[Added Associations]
x-scheme-handler/mailto=thunderbird.desktop;
```

I'd like to be able to put apps on the desktop

---

### Post by James.A.Parnell on 2011-11-27
I managed to get it onto the list thing (dash?) *see attachment*

but when i click it..... sweet nothings

Edit: the icon below it (Portal.bat) is what i actually have to click on to get it to work

---

