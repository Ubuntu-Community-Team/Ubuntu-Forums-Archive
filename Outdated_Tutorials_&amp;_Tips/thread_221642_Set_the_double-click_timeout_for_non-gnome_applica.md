---
title: "Set the double-click timeout for non-gnome applications"
date: 2006-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Cruxic on 2006-07-23
I recently installed Netbeans, (a Java Swing IDE), and was annoyed at how darn fast the double click speed was.  Changing the double-click timeout in Ubuntu's mouse preferences had no effect.  Research revealed that the mouse preferences dialog only works for Gnome applications.  So what we must do is specify a double-click rate for all X applications until this behavior is fixed.

[LIST=1]
[*]Open "Text Editor" from Accessories
[*]Type: *multiClickTime: 400
[*]Save the file directly in your home directory as .Xresources
[*]Log Out and then Log back on
[/LIST]

Substitute 400 with your prefered time (in milliseconds).  Keep in mind that the above  assumes you do not already have a .Xresources file.  If the file already exists, open it and add the line to the existing contents.

Hopefully this can be fixed in a future release of Ubuntu.

---

### Post by MountainX on 2010-10-23
Thanks for posting this. I actually found your original thread here: 
[http://forums.sun.com/thread.jspa?threadID=585358](http://forums.sun.com/thread.jspa?threadID=585358)

Amazing this is still an issue after so many years. I almost could not even use Netbeans without fixing this according to your post.

---

### Post by tulskiy on 2010-11-12
Since Oracle broke old Sun forums, this thread seems to be the only place to find solution to this problem... Thank you.

---

