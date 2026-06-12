---
title: "Wow Graphics Error"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Samerious on 2008-11-20
Just made the switch from XP to Ubuntu! Wooo ... but I have some issues with my world of  warcraft ... the floor is kind of glitchy i have screenshots for specifics... I already went through and read 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
and a few other topics but cant find a solution... any other help?
Im using Ubuntu 8.04 and have the latest drivers for my graphics card. I have plenty of ram to run it and it ran fine on XP . I have the latest version of Wine also.

---

### Post by cobra741 on 2008-11-20
Your best bet would be to start by setting WoW to run in opengl by changing the following line in your config.wtf file

SET gxApi = "direct3d" or "opengl"
obviously replace direct3d with opengl. this usually fixes most graphical glitches with wow and should give you a good performance boost.

otherwise go here and have a good read. there's a plethora or information on helping you get wow running nicely in Wine

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

hope this helps you out mate :)

---

### Post by Samerious on 2009-01-20
I'm still having issues with my wow. The game floor is still glitchy and i've looked at both articles and put a lot of the stuff to use with no fix. Any other ideas?

---

