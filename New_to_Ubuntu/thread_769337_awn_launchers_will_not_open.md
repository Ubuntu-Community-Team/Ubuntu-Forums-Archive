---
title: "awn launchers will not open"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by phoenix23 on 2008-04-26
I'm running awn from the hardy repo, but whenever I drag/drop a launcher onto the dock, awn adds %u to the end ofthe command, and then they won't open when I click on them. Also, when I go into awn-manager to correct the command, my revisions will not save.

So why won't awn launch my launchers?

---

### Post by -|Veni_Vidi_Vici*- on 2008-07-13
I'm having a similar problem with the latest awn. 
[list][*]I can drag and drop and it works, but the launchers disappear when I restart. Nor does the launcher show up in awn manager (this fits with the launchers not saving, a manual theme save doesn't preserve all of my dock items, just the ones that show up in awn manager)
[*]If I use awn manager to create a launcher from scratch, it doesn't show up on the awn dock.
[*]dragging and dropping sometimes results in the inability to change the icon (I can change it, but it doesn't take effect when I open the icon file)
[/list]
I'm thinking that my problem is that awn manager and awn dock are having trouble communicating with each other, and/or that there is a problem saving launchers. Though I'm about as clueless as you as to what to do.

---

### Post by paulderol on 2008-07-13
what other apps are you using? there are some wierd combos that don't like AWN. keytouch for one, others i'm unsure of.

are you using the trunk version?

---

### Post by nothingspecial on 2008-07-13
The secret to get your launchers to stay on the awn dock when you restart is thus -
Create a file in your home folder. 
Call it anything you like, mines called (inventively) "launchers".
Right click on any launcher in your menus and choose add to desktop.
Or use the create launcher option by right clicking on the desktop.
Open your new launchers folder.
Drag and drop the launchers from your desktop into your folder.
From your folder drag and drop them onto your awn dock.
They will stay in your launchers folder.
Now every time you restart awn they will be there.
                           :guitar:

---

### Post by tjwoosta on 2008-07-13
i have the same exact problem


my solution was to add the launcher manually from the awn preferences, and only add one at a time then close and re-open awn between each one

(kind of a pain but it works)

---

### Post by TimPJones on 2008-07-17
I'm having the same problem. Tried all the solutions suggested but still no joy adding launchers. Has anyone else got any suggestions.

This problem only occurred after updating.

---

