---
title: "Configuring mouse"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by turtlecloud on 2008-07-21
I reccently upgraded to Hardy Heron and hen I use Firefox, I usually click the scroller to open a link in a new tab or close an existing tab. However, when I do this, there is a tendency to send the current page to the previous one. Is there anyway I can disable this?

---

### Post by turtlecloud on 2008-07-22
anybody?

---

### Post by brokenLockpick on 2008-07-22
> **turtlecloud said:**
> ...click the scroller...

Do you mean "center clicking" or clicking the scroll wheel on your mouse? I was looking in the drop down menus for mouse button assignments but then it occurred to me that you might be talking about something else, so I just wanted to make sure.

---

### Post by Rocket2DMn on 2008-07-22
I had the problem of clicking opening a link to whatever was stored on the clipboard.  I had to set "middlemouse.contentLoadURL" to "false" in about:config.

---

### Post by turtlecloud on 2008-07-22
I meant the scroller. I click down on the scroller to open new tabs but then if I angle it wrong it sends me to the previous page.

---

### Post by brokenLockpick on 2008-07-22
> **turtlecloud said:**
> I meant the scroller. I click down on the scroller to open new tabs but then if I angle it wrong it sends me to the previous page.

Well what ever you call it, when I click my scroll wheel (or center click)It opens a page in a new tab (never realized it did that), so I'm guessing that we're talking about the same thing. I believe that your mouse probably supports tilting "the scroller" left/right to use the back/forward browser commands. In windows the buttons were mapped as 4 & 5 I've yet to learn the Ubuntu equivalent but hopefully that info helps point you in the right direction.

---

### Post by turtlecloud on 2008-07-22
Is there any way to solve this? Even when I try to press th button strait down, it will open a new tab and send the current page back to the previous one. It is very annoying. Also, does anyone know how to adjust the screen brightness settings? I have the LCD brightness application on the top panel but whenever I turn on my computer or restart it, it always goes back to the lowest brightness setting and I have to readjust it every time. Is there a way to configure this? I didn't see an option in the preferences section.

---

### Post by Rocket2DMn on 2008-07-22
RE: screen brightness
first check what your BIOS has set for screen brightness, then run
```
gconf-editor
```
and go to apps->gnome-power-manager->backlight and check the brightness for ac and battery.  Change as needed.

---

### Post by brokenLockpick on 2008-07-22
[http://support.mozilla.com/en-US/kb/Mouse+buttons+do+not+work+as+Back+and+Forward](http://support.mozilla.com/en-US/kb/Mouse+buttons+do+not+work+as+Back+and+Forward)

This is a tutorial for mapping the page back and forward functions to different mouse buttons. It seems like it will at the very least put them somewhere other than the tilt sensors for your "scroller". I can't guarantee it'll work because my page forward and back mapped elsewhere by default and I have a strong suspicion that my mouse is a different model.

---

