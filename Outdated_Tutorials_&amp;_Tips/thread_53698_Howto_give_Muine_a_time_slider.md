---
title: "Howto: give Muine a time slider"
date: 2005-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by kanem on 2005-08-01
I've recently been convinced of Muine's greatness. But what I don't think is so great is that to change to a different point in a song you have to press "t" on the keyboard and use a pop-up.

So I edited some code and put the slider on the main panel. Here's a [before and after](http://www.ubuntuforums.org/attachment.php?attachmentid=1816&stc=1).

To have this yourself download the Muine source code from [GnomeFiles](http://www.gnomefiles.org/app.php?soft_id=244). Make sure you have all the required dependencies to compile it. Then download the edited code [here](http://www.ubuntuforums.org/attachment.php?attachmentid=1817&stc=1).

The PlaylistWindow.glade file goes in muine-0.8.3/data/glade and the PlaylistWindow.cs goes in muine-0.8.3/src. If you don't trust code from strangers just do a 'diff' command to see what I've changed.

Finally, in the muine-0.8.3 folder, do a ./configure, make, checkinstall and that's it.

---

