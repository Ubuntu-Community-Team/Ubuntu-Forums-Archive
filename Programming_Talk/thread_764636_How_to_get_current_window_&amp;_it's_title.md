---
title: "How to get current window &amp; it's title?"
date: 2008-04-24
forum: Programming Talk
---

### Post by codecopier on 2008-04-24
I have google a lot.
But have not a clue.

thanks for any tips.

---

### Post by bran on 2008-04-24
> **codecopier said:**
> I have google a lot.
But have not a clue.

thanks for any tips.

might not be the ideal way but if you go to the compiz settings manager > window management > place windows plugin then the fixed windows placement tab.  click new on either you get an edit window hit the +  then you get an edit match window.  change window class to window title then grab the window of interest.

---

### Post by codecopier on 2008-04-24
> **bran said:**
> click new on either you get an edit window hit the +  then you get an edit match window.  change window class to window title then grab the window of interest.

Thank you~

But when I reach the place, I can't find "edit match window", "window class" or "window title".
My os is ubuntu 7.1.
It is just a plain edit control.

---

### Post by rickst29 on 2010-01-12
You have it 90% done already. Here's how to "grab" the title or class value of any Window which you have opened.... although the Window does need to be dragged into the same viewport as CSSM, because the "cross-hairs" target selector can NOT drag across over an edge to select a Window in another viewport. So, you must have at least a little bit of the Window for which you want to define "fixed placement" inside the same viewport as CSSM. (CSSM is showing the "Fixed Window Placement" tab of the "Place Windows" plugin.)

With that application window visible (to the side, or above/below CSSM's "Place Windows" window,) use either "New" or Edit" to open the definition panel for creating a "fixed position", or "fixed placement", or "fixed viewport" Window. This Panel is named ***Edit***.

Within the "Edit Pop-up, press the big plus sign to the right of the match criterion. This opens a child pop-up Panel, named ***Edit match***. Choose your criterion (I always use *"class",* it seems to work really well).Now, press the "grab" button. Your mouse pointer should convert into a targeting cross-hairs pattern. You don't need to hold a button down; just move into the body of the application Window (NOT it's title bar-- the actual body). Click and the value will be filled in auto-magically, and your mouse will be set back to it's normal pointer appearance.

BTW, you can define the exact same windows to be placed with both "fixed position" AND "fixed viewport". I do with all my favorite Apps (putting email in viewport #1, browser in viewport #2, and etc.) while they're also defined  with "fixed position" to keep them away from my taskbars and panels.

I'm not on Ubuntu, but like you, I searched Internet and didn't get a good answer. (Using Mandriva+KDE.) But Google showed this Thread near the top of my query results, so I registered in this forum to create this post after I figured out how to do it. I hope this info is useful for both Ubuntu programmers AND compiz users is general.

---

### Post by jpkotta on 2010-01-13
AFAIK, getting the focused window is dependent on the window manager, because the WM determines focus.  

It's easy to get info about a particular window.
```

xprop | grep "WM_NAME(STRING)"

```

The usual identifiers are WM_NAME, WM_ICON_NAME, WM_CLASS, and the window id.

---

