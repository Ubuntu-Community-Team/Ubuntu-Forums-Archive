---
title: "[SOLVED] horizontal scroll the easy way"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-05
is there a way to scroll a page horizontally that is easier than grabbing the scrollbar in firefox?

---

### Post by ajmorris on 2008-10-05
> **adamogardner said:**
> is there a way to scroll a page horizontally that is easier than grabbing the scrollbar in firefox?

only if you have a mouse with a scroll wheel that you can push sideways, or a laptop with a virtual scrolling configured for the touchpad.


AJ

---

### Post by xreaper on 2008-10-05
Isn't it possible to move the mouse to the bottom bar (the one you want to use to scroll horizontally) and use the middle mouse button to scroll it sideways?

---

### Post by ajmorris on 2008-10-05
> **xreaper said:**
> Isn't it possible to move the mouse to the bottom bar (the one you want to use to scroll horizontally) and use the middle mouse button to scroll it sideways?


yes... but isnt that as much hassle as draging the bar?

---

### Post by Dr Small on 2008-10-05
If you are using vimperator in Firefox, it's as easy as pressing either h or l

---

### Post by unutbu on 2008-10-05
Open Firefox and type about:config in the URL text field.

In the Filter field type 'general'

Right-click on general.autoScroll and select Toggle
to set it to True.

This enables the middle button or mousewheel-click to grab the Firefox page. Simply moving the mouse (wherever it happens to be) will now move the page.
Left click to release the page.

---

### Post by adamogardner on 2008-10-06
> **unutbu said:**
> Open Firefox and type about:config in the URL text field.

In the Filter field type 'general'

Right-click on general.autoScroll and select Toggle
to set it to True.

This enables the middle button or mousewheel-click to grab the Firefox page. Simply moving the mouse (wherever it happens to be) will now move the page.
Left click to release the page.

the problem then is that I use my touchpad not a mouse.  It's a little different than holding down the midddle scroll wheel unless there is a wayaround it
I'm gonna checkout vimperator too

---

### Post by ajmorris on 2008-10-07
> **adamogardner said:**
> the problem then is that I use my touchpad not a mouse. It's a little different than holding down the midddle scroll wheel unless there is a wayaround it
I'm gonna checkout vimperator too
 
Which touchpad do you have? Most touchpads will have the ability to do horizontal, and vertical, virtual scrolling, once using the correct X11 mouse driver :)
 
AJ

---

### Post by ymra on 2008-10-07
Use the arrow keys on your keyboard.

---

### Post by DirtDawg on 2008-10-07
If you are using a touchpad, and it sounds like you are, you can adjust it so the very bottom of your touchpad acts as a horizontal scrollbar.

Go to System>Preferences>Mouse, then navigate to the "Touchpad" tab, then click the "enable horizontal scrolling" checkbox. You may need to log out. Not sure.

After you finish, the very bottom of your touchpad will act as a scrollwheel (as the very right side does if "enable vertical scrolling" is enabled). Simply run your finger along the bottom of your touchpad to activate the horizontal scroll.

It can take some getting used to, but once you do, touchpad scrolling is a must have. Hope this helps.

---

### Post by adamogardner on 2008-10-07
> **DirtDawg said:**
> If you are using a touchpad, and it sounds like you are, you can adjust it so the very bottom of your touchpad acts as a horizontal scrollbar.

Go to System>Preferences>Mouse, then navigate to the "Touchpad" tab, then click the "enable horizontal scrolling" checkbox. You may need to log out. Not sure.

After you finish, the very bottom of your touchpad will act as a scrollwheel (as the very right side does if "enable vertical scrolling" is enabled). Simply run your finger along the bottom of your touchpad to activate the horizontal scroll.

It can take some getting used to, but once you do, touchpad scrolling is a must have. Hope this helps.

there is no touchpad tab.

what about this x11 mouse driver?

---

### Post by adamogardner on 2008-10-07
ok, that was easy.  I already had horizontal scroll installed.  I never considered that the touchpad would function that way, but it does.  Thanks for your help.

---

### Post by Virgofenix on 2008-11-22
> **DirtDawg said:**
> If you are using a touchpad, and it sounds like you are, you can adjust it so the very bottom of your touchpad acts as a horizontal scrollbar.

Go to System>Preferences>Mouse, then navigate to the "Touchpad" tab, then click the "enable horizontal scrolling" checkbox. You may need to log out. Not sure.

After you finish, the very bottom of your touchpad will act as a scrollwheel (as the very right side does if "enable vertical scrolling" is enabled). Simply run your finger along the bottom of your touchpad to activate the horizontal scroll.

It can take some getting used to, but once you do, touchpad scrolling is a must have. Hope this helps.

I did this but the scrolling I get from the horizontal scroll area is vertical. What's wrong?

---

