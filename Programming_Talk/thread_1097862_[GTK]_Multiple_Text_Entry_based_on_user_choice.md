---
title: "[GTK] Multiple Text Entry based on user choice ?"
date: 2009-03-16
forum: Programming Talk
---

### Post by sujoy on 2009-03-16
I am coding a sort of contacts maintaining application using GTK. Doing the design in glade now, actually.

Now, any of my contacts can have multiple phone-numbers or email address, which is pretty common. So I normalised the backend database structure to cope with it. 

However, the app I am writing now will be used to enter the informations into the database. The question is, how do I add more text entry fields based on user choice? 

Like, I have one text entry labelled "email". Now, if the contact has more email addresses, then I would just click <add one more> button/link or something like that, and then have another text entry added in just beneath the original one. I have seen this done in many websites, where I understand javascript will be of help. However, for a standalone app, I am really out of ideas. :confused:

---

### Post by imdano on 2009-03-16
Why not just make the button-click callback call a method that creates another Gtk.Entry?  You would just create a VBox in glade that could hold all the entries, and maybe one entry to go in the VBox by default.  Then you would write code yourself (instead of relying on glade) that would add more gtk.Entry widgets to the VBox as the user clicked the Add button.

---

### Post by sujoy on 2009-03-16
Yes that would work nicely, thanks. I have always just used glade to make the GUI, so kinda need to get some tutorials now :)

will post back later how it went ...

---

