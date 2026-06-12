---
title: "[SOLVED] minimize to titlebar"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by tomehb on 2008-09-18
Hi guys,

i saw that one of my friends could minimize a window to the titlebar of the window, how would i get this feature working within Ubuntu 8.04, i have tried changing a few settings within the Configuration Editor, but have yet to find the correct options.. Any ideas? or know of any posts that detail how to do this? 

Cheers

Thomas

---

### Post by Linteg on 2008-09-18
Presuming you are using metacity (and not compiz-fusion) I believe the setting you are looking for is: ```
/apps/metacity/window_keybindings/toggle_shaded
``` (in the Configuration Editor of course)

---

### Post by karlr42 on 2008-09-18
Hmm, I can do that, you have to install the emerald theme manager, it's a feature of that. Assuming you mean this:
[http://i523.photobucket.com/albums/w351/karlr42/Screenshot1.jpg](http://i523.photobucket.com/albums/w351/karlr42/Screenshot1.jpg)
This  works in Compiz

---

### Post by anotherdisciple on 2008-09-18
> **Linteg said:**
> I believe the setting you are looking for is: ```
/apps/metacity/window_keybindings/toggle_shaded
``` (in the Configuration Editor of course)

+1

but to keep you from searching... you launch the configuration editor by hitting Alt+F2 and typing:
```
gconf-editor
```

---

### Post by lian1238 on 2008-09-18
Try opening up the Keyboard shortcuts in system->preferences.
or type this:
```
gnome-keybinding-properties
``` in Run dialog or terminal.
Look for "Toggle Shaded State" under Windows. Set the shortcut key to your desire.

If you use emerald though, I think scrolling your mouse while pointing to the titlebar will shade and unshade.

---

### Post by karlr42 on 2008-09-18
> **lian1238 said:**
> 
If you use emerald though, I think scrolling your mouse while pointing to the titlebar will shade and unshade.
Yep, confirmed, that and double-clicking the titlebar.

---

### Post by lian1238 on 2008-09-18
Also, if you want to toggle shade with your mouse (double-click or right-click), open up gconf-editor then go to apps/metacity/general. There you can set the double/middle/right-click actions.

---

### Post by tomehb on 2008-09-18
> **Linteg said:**
> Presuming you are using metacity (and not compiz-fusion) I believe the setting you are looking for is: ```
/apps/metacity/window_keybindings/toggle_shaded
``` (in the Configuration Editor of course)

Hi,

Thankyou for the quick reply this worked a treat

Thanks

Tom

---

### Post by anotherdisciple on 2008-09-18
Good... can you mark this as solved good sir?

---

