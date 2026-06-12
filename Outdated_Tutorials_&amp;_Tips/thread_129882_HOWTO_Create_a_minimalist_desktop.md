---
title: "HOWTO: Create a minimalist desktop"
date: 2006-02-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Gimbo on 2006-02-14
This is just the result of some messing around, so it's not spectacular and it's not difficult. I've attached a screenshot of how it looks when it's finished.

1. **Clear all icons off your desktop.** Delete any icons/shortcuts you've created yourself, then go to System Tools>Configuration Editor>apps>nautilus>desktop. Untick all the boxes you find there. This is for an *absolute minimalist* desktop. In reality, you'll probably want at least trash_icon_visible and volumes_visible.

2. **Delete all but one of your GNOME panels.** This can be done by right-clicking on an empty space on the panel you want to delete and selecting "Delete This Panel..." from the menu (don't worry, GNOME will prevent you from removing your last panel).

3. **Remove all panel items.** Right-click a panel item and choose "Remove From Panel". If the item itself won't let you right-click it (e.g. the "Window List" item), try right-clicking *just* next to it on the panel.

4. **Add just the panel items you need.** Right-click on the panel, choose "Add to Panel..." I've chosen a Main Menu, a Clock, a Menu List and a Notification Area.

5. **Tweak the panel's Properties to your liking.** Right-click on the panel and choose "Properties".
I've chosen:
Orientation: Bottom
Size: 23 pixels
Expand: Ticked
Autohide: Unticked
Show hide buttons: Ticked
Arrows on hide buttons: Ticked
Background: None (use system theme)
(My system theme is Clearlooks - go to System>Preferences>Theme from the GNOME menu to choose a them)

6. **Choose a minimalist wallpaper.** Go to System>Preferences>Desktop Background. I've gone for [this Clearlooks-inspired wallpaper]("http://www.ubuntuforums.org/gallery/showimage.php?i=922") by [dngpng]("http://ubuntuforums.org/member.php?u=40882").

7. **Minimise all windows and hide your panel.** Hold down Ctrl and Alt and press D. Finish by clicking on one of the panel's hide buttons. You should be left with just your wallpaper and a tiny little icon that pulls out your panel.

This isn't by any means the most practical of set-ups, but it does demonstrate how customisable GNOME is without needing any extra software.

---

### Post by Gustav on 2006-02-15
A tip can be to have two panels at the bottom (one to the left and one to the right) and have the stuff you use little more (for example main menu) on one of them and the rest on the other one. 

Then you can be little more flexible and chose just to show the main menu for example. (And you don't have to wait that long for the panel to unhide)

---

### Post by william_nbg on 2006-02-15
Or you could just run Blackbox or Fluxbox with a little gnome on the side. My Blackbox loads from the gdm in about 1 second.

[IMG]http://www.moonpad.net/images/bbscreenshot2.jpg[/IMG]

---

### Post by bluevoodoo1 on 2006-02-15
[QUOTE=Gimbo]
3. **Remove all panel items.** Right-click a panel item and choose "Remove From Panel". If the item itself won't let you right-click it (e.g. the "Window List" item), try right-clicking *just* next to it on the panel.

4. **Add just the panel items you need.** Right-click on the panel, choose "Add to Panel..." I've chosen a Main Menu, a Clock, a Menu List and a Notification Area.

7. **Minimise all windows and hide your panel.** Hold down Ctrl and Alt and press D. Finish by clicking on one of the panel's hide buttons. You should be left with just your wallpaper and a tiny little icon that pulls out your panel.[/QUOTE]

My question is... If you're just going to hide your panel, why must one have only a few items on it? Why not load it up?? Are you going for looks or for speed? I love the minimalist look, but shouldn't it also be [somewhat] fully functional?

If it's speed, then I agree totally with william_nbg, check out one of the *Box window-managers... Fluxbox, Openbox.... and my favorite Blackbox. It is awesome! :KS

---

### Post by Rev. Nathan on 2006-02-15
[QUOTE=william_nbg]Or you could just run Blackbox or Fluxbox with a little gnome on the side. My Blackbox loads from the gdm in about 1 second.

[IMG]http://www.moonpad.net/images/bbscreenshot2.jpg[/IMG][/QUOTE]
I have to agree. Coming from I, a GNOME user who doesn't dig the simplicity at all, a -box is the way to go. And if you still want that GNOME feel, go with Openbox ('sudo apt-get install openbox' from the universal repo). It's so minimalist... its naughty. :twisted:

---

### Post by benplaut on 2006-02-16
along with the *box's, Enlightenment is worth a try... it's a bit heavier, but looks so damn good :cool:

---

### Post by Yezinki on 2008-08-25
> **Gimbo said:**
> This is just the result of some messing around, so it's not spectacular and it's not difficult. I've attached a screenshot of how it looks when it's finished.

1. **Clear all icons off your desktop.** Delete any icons/shortcuts you've created yourself, then go to System Tools>Configuration Editor>apps>nautilus>desktop. Untick all the boxes you find there. This is for an *absolute minimalist* desktop. In reality, you'll probably want at least trash_icon_visible and volumes_visible.

2. **Delete all but one of your GNOME panels.** This can be done by right-clicking on an empty space on the panel you want to delete and selecting "Delete This Panel..." from the menu (don't worry, GNOME will prevent you from removing your last panel).

3. **Remove all panel items.** Right-click a panel item and choose "Remove From Panel". If the item itself won't let you right-click it (e.g. the "Window List" item), try right-clicking *just* next to it on the panel.

4. **Add just the panel items you need.** Right-click on the panel, choose "Add to Panel..." I've chosen a Main Menu, a Clock, a Menu List and a Notification Area.

5. **Tweak the panel's Properties to your liking.** Right-click on the panel and choose "Properties".
I've chosen:
Orientation: Bottom
Size: 23 pixels
Expand: Ticked
Autohide: Unticked
Show hide buttons: Ticked
Arrows on hide buttons: Ticked
Background: None (use system theme)
(My system theme is Clearlooks - go to System>Preferences>Theme from the GNOME menu to choose a them)

6. **Choose a minimalist wallpaper.** Go to System>Preferences>Desktop Background. I've gone for [this Clearlooks-inspired wallpaper]("http://www.ubuntuforums.org/gallery/showimage.php?i=922") by [dngpng]("http://ubuntuforums.org/member.php?u=40882").

7. **Minimise all windows and hide your panel.** Hold down Ctrl and Alt and press D. Finish by clicking on one of the panel's hide buttons. You should be left with just your wallpaper and a tiny little icon that pulls out your panel.

This isn't by any means the most practical of set-ups, but it does demonstrate how customisable GNOME is without needing any extra software.

Hi there,

Cant locate System tools in KD 4.1?

Thanks!

---

### Post by ~LoKe on 2008-08-27
Minimalism is great, but not at the cost of functionality.  I'd prefer to go with a lighter WM to achieve a more practical effect.

---

### Post by Crafty Kisses on 2008-08-29
Nice tutorial. :)

---

