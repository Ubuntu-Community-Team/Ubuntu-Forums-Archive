---
title: "Err.... Day of Defeat game goes black..."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by kulotzy on 2008-04-28
I dunno if this is the correct forum for this, but i have little knowledge with ubuntu and linux... i was able to install WINE and the propriety driver (Im using ATI) but **_whenever i run Day of Defeat source, the game loads to the menu and then it goes black_**. I can hear sounds but i cant see anything? Any help please?

---

### Post by kulotzy on 2008-04-28
Ive been searching the forums for hours but i cant find anything... so if anyone know of a solved thread, or anything, any help would be appreciated

---

### Post by kulotzy on 2008-04-28
:confused:

---

### Post by Dark Aspect on 2008-04-29
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571")

Odd the game is suppose to work,try making a virtual desktop.Go to the terminal and type winecfg then click on the graphics tab.Under that tab you should see a Emulate a virtual desktop box,check it and type in something like 1024x768 or 800x600.

If that fails start the game up with wine via terminal to see the output with:

> wine /link/to/file/filename.exe

Post the output,it might be something simply like a missing dll.

Edit: BTW,you might wanna use this forum for games: 

[http://ubuntuforums.org/forumdisplay.php?f=93]("http://ubuntuforums.org/forumdisplay.php?f=93")

---

### Post by kulotzy on 2008-04-29
> **Dark Aspect said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571")

Odd the game is suppose to work,try making a virtual desktop.Go to the terminal and type winecfg then click on the graphics tab.Under that tab you should see a Emulate a virtual desktop box,check it and type in something like 1024x768 or 800x600.

If that fails start the game up with wine via terminal to see the output with:



Post the output,it might be something simply like a missing dll.

Edit: BTW,you might wanna use this forum for games: 

[http://ubuntuforums.org/forumdisplay.php?f=93]("http://ubuntuforums.org/forumdisplay.php?f=93")

Thanks for replying. 

I tried setting the virtual set up to both you suggested, but neither worked because Day of Defeat would run in full screen anyway.

And how do i use WINE to run the game? Post what output?

And yeah, i thought this mightve been the wrong forum... duly noted...

---

### Post by LieToPurify3 on 2008-06-17
Did you get this to work? I have the same problem :(

---

