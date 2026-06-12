---
title: "[SOLVED] panel/drawer items are sideways"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by gordon55y on 2008-11-28
I have added a drawer to the panel.
But when I move items from the panel to the drawer,
the appear rotated 90 degrees.
How can I create items in the drawer that are not rotated?
gordon

---

### Post by Michael.Godawski on 2008-11-28
Perhaps it is only me... but I do not get it. :)

Could you perhaps provide me/us with a screen-shot?

---

### Post by gordon55y on 2008-11-28
Attached is a screenshot.
I see that the icons are upright, it is the text that is sideways.

By the way, my intention was to have only one panel.
And the system admin stuff would go into one drawer.
The "Applications Places System" item uses a lot of panel space.
Is there another way to do this?

---

### Post by drs305 on 2008-11-28
If you right click the panel, select Properties, and move the panel to the top does it do the same thing? Either way, you can check it and then move it back to the bottom. 

I looked through gconf-editor and cannot find a setting for drawers that sets how the menu expands. Nor can I find anything in the drawer properties, but the drawer I added to the panel does not exhibit the same sideways behavior as does yours.

---

### Post by gordon55y on 2008-11-28
drs305,
  When I move the panel to the top, the sideways text in
the drawers is the same.

  Apparently people do not commonly use drawers?
How do others solve this problem?
That is, how do you reduce the panel space used
by "Application Places System"?

gordon

---

### Post by drs305 on 2008-11-28
> **gordon55y said:**
> drs305,
  When I move the panel to the top, the sideways text in
the drawers is the same.

  Apparently people do not commonly use drawers?
How do others solve this problem?
That is, how do you reduce the panel space used
by "Application Places System"?

gordon

I make my own menus although it is more work - the effect is the same as just adding a drawer (although my menus display properly ;-)  ). You have to manually add each item and it's run command. 

If you want to try it to see if it displays better, here is how I set up a menu on the panel:

1. Right Click on the Main Menu icon and select 'Edit' (or run 'alacarte').
2. To make a new folder, in the right column, click 'New Menu' and name it.
3. Add at least one item - highlight the new folder on the left; on the right, select 'New Item' and add the name and command.
3a. Add as many new items as you wish.
4. On the panel, select 'Add to panel'.
5. Double-click 'Application Launcher'. You will see your new folder in the list of available applications. Drag it to the panel and release.
6. Cross your fingers and see if it displays correctly.

---

### Post by gordon55y on 2008-11-28
drs305,

>1. Right Click on the Main Menu icon and select 'Edit' (or run 'alacarte').

Where is the Main Menu icon?
I see a Main Menu icon in System/Preferences
But I don't think that is the right one.
I do not see a Main Menu icon in System/Administration
Which is where I would have expected to see it.
And, I cannot find it in Applications

gordon

---

### Post by drs305 on 2008-11-28
> **gordon55y said:**
> drs305,

Where is the Main Menu icon?


I don't know which version your are using, but in ubuntu it is the red/yellow/orange ubuntu symbol at the top left of the top panel. If you are in ubuntu and don't have it, you can right click the panel, Add to Panel, and add the 'Main Menu' icon.

You can also access the menu editing function in ubuntu by running this in the terminal:
```
alacarte
```

---

### Post by gordon55y on 2008-11-28
drs305,
  This is ubuntu 8.10.
Thanks for the explanation.
You have to create each item (and icon) manually, right?
That is, you cannot copy an existing menupick, like: Applications
or Places or System?

I guess that you have moved Applications Places System
to the desktop in order to get it off the panel?

gordon

---

### Post by drs305 on 2008-11-28
I created each one manually (I said it was more work!). I tried *briefly* to drag & drop items into my new folder but didn't find a way to do it.

For me, *Applications Places System* just takes up too much space, so I have the Main Menu, individual icons, and self-created drawers.

---

### Post by gordon55y on 2008-11-28
drs305,

> For me, Applications Places System just takes up too much space, so I have the Main Menu, individual icons, and self-created drawers. 

   Oh, your description seems different than mine.
Can you somehow display only the Main Menu icon without
the lengthy Applications Places System text?

gordon

---

### Post by drs305 on 2008-11-28
> **gordon55y said:**
> drs305,

> For me, Applications Places System just takes up too much space, so I have the Main Menu, individual icons, and self-created drawers. 

   Oh, your description seems different than mine.
Can you somehow display only the Main Menu icon without
the lengthy Applications Places System text?

gordon
Yes. You can add the "Main Menu" icon (Add to Panel, "Main Menu") and then eliminate the "Apps Places System" menu. 

When you first click on the "Main Menu", the first 2/3 of the dropdown is what you would normally see under Applications. Then comes "Places", followed by "System". It occupies only one icon-width on the panel which is why I prefer it.

---

### Post by gordon55y on 2008-11-28
Thanks, that is what I wanted.
gordon

---

