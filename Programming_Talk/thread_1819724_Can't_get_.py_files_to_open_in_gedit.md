---
title: "Can't get .py files to open in gedit"
date: 2011-08-06
forum: Programming Talk
---

### Post by donsy on 2011-08-06
I would like to be able to edit my .py source files with a text editor. However when I right click the icon in Nautilus, select properties -> open with, and add Text Editor it has no effect. If I select it and click the reset button it adds Notepad (Wine installed) to the list but otherwise has no effect. How can I get my .py files to open in gedit?

BTW I never want to use Notepad for anything at all. Is there a way I can keep it from being added as an 'open with' application?

Edit: The problem has to do with the executable bit being set. I wish there was a way around this. When I execute I do it from the command line but most always I edit a script after browsing in Nautilus.

---

### Post by cgroza on 2011-08-06
So when you double click it, does it present a dialog with the Display option in it?

I think your file association may need a little tweaking.

---

### Post by donsy on 2011-08-06
> **cgroza said:**
> So when you double click it, does it present a dialog with the Display option in it?


This reminded me of the behavior I had set in Nautilus. Under preferences -> behavior I had it set to "Run executable text files when they are clicked". I changed this to "View ..." and problem solved. Thanks.

---

### Post by mendhak on 2011-08-07
> **donsy said:**
> 

BTW I never want to use Notepad for anything at all. Is there a way I can keep it from being added as an 'open with' application?


Go to ~/.local/share/applications/wine.  You should find a lot of Wine related 'shortcuts' there.  Delete the ones that belong to Notepad (there may be multiple) and Notepad should no longer appear in your list.  Another way is to right click on the Applications menu, edit, then go to 'other', and start removing all the notepad entries.

---

