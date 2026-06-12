---
title: "Can I create just a plain tab bar with Glade?"
date: 2007-03-24
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2007-03-24
So here I am, building my first remotely adventurous Gnome / GTK program using Glade 3. (Great piece of work by the way. The Glade developers should be very proud).
In my UI, I have a big list of stuff divided into sections. I am hoping to have these sections switchable using Tabs on the side of a list box, since it looks pretty and makes sense for this particular situation.
The problem, however, is that these sections are actually tags that are created by the user; the tab bar must have items added and removed. Note that the actual list box that the tabs are associated with does not need to change anything except its contents.

Unfortunately, it seems that the only tabs Glade will do for me are Notebooks, which seem to be built around a very different idea where each Page contains totally different widgets. I do not need this! (Or want it for this situation). I just need the tab bar to communicate a simple little bit of information in the same way as a list box would. (Except prettier and easier to figure out. I don't know if you've had the pleasure, but my all-too-familiar experience with them says: Navigating dual list boxes is ridiculous!)

So what is a nice way with Glade to have just a simple, independent tab bar to which tabs can be easily added / removed on the fly?

---

