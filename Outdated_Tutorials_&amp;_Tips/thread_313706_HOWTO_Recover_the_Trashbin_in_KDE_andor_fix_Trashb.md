---
title: "HOWTO: Recover the Trashbin in KDE and/or fix Trashbin icon (always full/empty)"
date: 2006-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Apostata on 2006-12-06
This one had me for the longest time - I can't remember how it happened, but I found that I'd lost the Trashbin on my KDE desktop. I could use the tray-applet Trashbin, but (dammit!) I wanted my Trashbin back.

Here's where I stumbled upon a solution:
[http://lists.kde.org/?l=koffice&m=112334215507025&w=2]("http://lists.kde.org/?l=koffice&m=112334215507025&w=2")

To recap:

1. Right click on the desktop, and from the menu select "Create new" and then "Link to location (URL)"

2. In the window that pops up, enter the following url:  trash:/
 
3. Name this url: Trashbin (or whatever)
 
4. click Ok

This will make the Trashbin appear automagically on the Desktop - but wait! It doesn't fix another bug: sometimes the icon won't change if the Trashbin is empty or full. Aesthetically frustrating.

This is what you need to do:

1. Open Konqueror.

2. Navigate to ~/Desktop

3. Click View -> Show Hidden Files

4. Open 'Trashbin.desktop' in Kate (or Kedit). Save the existing file as 'Trashbin.desktop_old' just to be safe.

5. Make sure the following is there:

> [Desktop Entry]
Comment=Contains removed files
EmptyIcon=trashcan_empty
Encoding=UTF-8
Icon=trashcan_full
Name=Trash
Type=Link
URL=trash:/
 
6. Save and close. Et voila.

---

### Post by RagingOcelot on 2007-01-20
I'm having the same problem in Gnome, if someone knows how to fix it.

---

### Post by bg1256 on 2007-07-04
Thank you for posting this!  I realize it's old, but I'm happy to find it!

---

