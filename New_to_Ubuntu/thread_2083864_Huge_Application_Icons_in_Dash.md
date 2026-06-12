---
title: "Huge Application Icons in Dash"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by pmwalton on 2012-11-13
Hello all,
 
For some reason in my dash on Ubuntu 12.04 I have some huge application's icons for particular applications. Does anyone know what might have caused this?
Attached is a screenshot.
Thanks

---

### Post by audiomick on 2012-11-13
Wow, that's amazing... ;)

Those programs are not default programs, are they? I don't know for sure, but what occurs to me is the the image that is used for the icons, probably and .svg, I think, for some reason doesn't allow itself to be shrunk down small enough. That is just a wild guess, though. If you can work out how to change the icon associated with the program, which I don't know how to do in Unity, you might be able to put in a different one that let's itself be appropriately sized. That is what I would try, anyway.

---

### Post by pmwalton on 2012-11-13
> **audiomick said:**
>  Those programs are not default programs, are they? 
 
No they're not, I think they're all related to PostgreSQL. So I somehow need to find it's application icon... anyone know where it would be located/searched for?

---

### Post by monkeybrain2012 on 2012-11-13
I think it is the problem with the program. Here is a dirty way to fix it. Find the .desktop file for the program (depending on how you installed it it may be in /usr/share/applications, /usr/local/applications or /home/yourusername/.local/share/applications. Note that .local is a hidden folder in your home directory so you have to make the file manager to show it first, open your home directory in Nautilus and press ctr+h,or View > show hidden files)

Once you find it open with gedit, there is a line like Icon=pathtoicon. First check the path, it may be that the program has several icons of different sizes, pick another one. If not just find some icon online which you think makes sense in representing the software, store it somewhere (like .local/share/icons or /usr/share/icons) then change the Icon=pathtoicon line to the path of the new image.

EDITED: You actually don't need to open it with gedit, if you right click the .desktop file and choose properties, there should be a box on the upper left corner showing the icon, right click it and you can choose another icon which you have stored somewhere.

---

### Post by pmwalton on 2012-11-13
That looks like it's worked!
The properties method didn't seem to work so I used gedit instead and it worked like a charm. Thanks heaps

---

