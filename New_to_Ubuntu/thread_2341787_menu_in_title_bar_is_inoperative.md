---
title: "menu in title bar is inoperative"
date: 2016-10-31
forum: New to Ubuntu
---

### Post by aajax on 2016-10-31
I used the Behavior tab of Settings>Appearance to specify that I want to "Show the menus for a window - in the window's title bar".  The result is that the menus do show in the title bar but when you select items on them with the mouse nothing happens.  In that there is no drop down menu from which to select an action.  Completely useless setting as is!

Is it possible to make this work correctly?

---

### Post by ajgreeny on 2016-10-31
Tell us which version of Ubuntu or it will be more difficult to help you.

Hardware could also be relevant so let us know that as well.

---

### Post by Geoffrey_Arndt on 2016-10-31
Had that same issue in 14.04 although I see you're now running 16.04. I went back to the standard global menu as it works 100% of the time.   The Windows Title option just wasn't consistently functional.

---

### Post by aajax on 2016-11-02
The attached screen shot is from "About This Computer"!

---

### Post by aajax on 2016-11-02
Geoffrey_Arndt says > I went back to the standard global menu ...

I'm afraid it is not clear to me what the "standard global menu" refers to.

---

### Post by CantankRus on 2016-11-04
Are menus inoperable only when the window is maximized.
This happens to me occasionally with maximized windows and logging out fixes.
I can also go to the  top right , click on the cog wheel to open a menu.
Leave the menu open then slide across to the application menus which open as the mouse hovers on them.

"standard global menu" means the default which can be restored the same place you set it.

---

### Post by Geoffrey_Arndt on 2016-11-04
Herr aajax,

By "Global Menu" . . . I am referring to the standard Ubuntu menu design for the Unity desktop . . . in that the application window that is active (the focused window) controls the specific menu dialog that you see.   Similar to a Mac, you move the cursor/arrow to the very top menu bar of the whole desktop, and then you will see the Menu for that focused app.    If you click on a different app (let's say Libre Calc versus gThumb Image Viewer), you'll then see the Calc menu versus the gThumb Image Viewer.   Those global menus work 100% of the time, meaning, if I click on the Edit option, I see a dropdown list of the edit options, etc.

EDIT:  Some use the term "Universal Menu" versus Global Menu to refer to this UI design.   After some limited checking, I can get Local Menus to function "most" of the time, but I have no issue with the default method.

---

### Post by CantankRus on 2016-11-07
Try this solution [**[COLOR="#B22222"]HERE[/COLOR]**]("https://ubuntuforums.org/showthread.php?t=2342233&p=13565878#post13565878") where the grab-wait time was set too low.
If menus don't open at all, try ruunning this command to reload the panel...
```
unity
```

---

