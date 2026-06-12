---
title: "adding entries to gnome-menu in postinst"
date: 2010-06-11
forum: Packaging and Compiling Programs
---

### Post by JakeFrederix on 2010-06-11
After having figured out how to package something to a .deb file, I'd like to know how I can make my program appear in the gnome menu.

I've already tried making a <name>.desktop file, and copying it to /usr/share/applications in an attempt to directly alter the menu. (this was done by the postinst script of course)
Sadly, this doesn't seem to work for me. The file is copied, but the menu does not change.

Kind regards,
Jake

---

### Post by dodle on 2010-06-11
I don't know how to do it from the post-install.  Could you post your .desktop file?  

If you want, you can use [debreate](http://debreate.sourceforge.net) to generate a .desktop file.  

1) Open debreate
2) Go to "Menu" tab
3) Fill out info
4) Click on "File" -> "Save .desktop"

---

### Post by JakeFrederix on 2010-06-11
I managed it on myself!
Turns out I forgot to do chmod a+x to make the .desktop executable.

Now the only step that's left is getting it into the repos :p

---

