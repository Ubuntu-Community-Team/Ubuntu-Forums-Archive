---
title: "Turn off gnome-search-tool?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by entropism on 2008-05-21
OK, asked this a few days ago, maybe rewording it will help my issue:

Is there any way to either turn off Gnome-Search-Tool, or remap the mouse button that launches it?  Right now it's launching when I hit my middle mouse button, which I'd LIKE to use to open a new tab in firefox.

Thanks in advance!

---

### Post by wrgb2 on 2008-05-21
You can turn it off with System>Administration>Search and Indexing, under Indexing Options, uncheck Enable Indexing and Enable Watching.  You'll have to restart to apply this.  I'm not sure how you can turn of the middle-mouse-button launch once Tracker is loaded.

---

### Post by entropism on 2008-05-22
Not finding "search and indexing" under administration.  This is starting to get frustrating.  :(

---

### Post by Inxsible on 2008-05-22
System>>Preferences>>Sessions. In autostarted apps, remove the one called tracker or trackerd

---

### Post by entropism on 2008-05-22
Tried your suggestion, restarted, and hitting the middle mouse button starts the search tool anyways.  Is this a new thing to Hardy?  I never had this problem in Gutsy or Fiesty

Just wanted to thank everyone who came up with suggestions, even if they didn't work.  I do appreciate the help.  =)

Edit, fixed.  Went into gnome-keybindings and disabled search from there.

---

### Post by Mortuis on 2008-06-05
Thanks, was having the same problem and went to System->Preference->Keyboard Shortcuts, clicked on the shortcut for Search and used backspace to delete the value in there.  Got my middle mouse button back!

---

