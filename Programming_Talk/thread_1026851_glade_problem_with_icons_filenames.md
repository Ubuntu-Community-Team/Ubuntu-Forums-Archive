---
title: "glade problem with icons filenames"
date: 2008-12-31
forum: Programming Talk
---

### Post by giuspen on 2008-12-31
Seems that glade can point only to icons that lay exactely in the same directory where the ".glade" file is; if I try to point to images in other directories, glade creates a local copy and points to the local copy.
I tried to edit the glade (xml) file through text editor changing the images path between the tags, the funny thing is that the gtk application works correctly pointing to the images wherever they are but as soon as I edit again the glade file through glade, glade automatically resets all paths to point to the same directory where the ".glade" file is.
This is not a big deal, just I would like to place the icons in the standard gnome place for icons.
If anybody found a workaround please tell me.
Thanks, regards.

---

### Post by rich1939 on 2008-12-31
> **giuspen said:**
> Seems that glade can point only to icons that lay exactely in the same directory where the ".glade" file is; if I try to point to images in other directories, glade creates a local copy and points to the local copy.
.

This is not ideal, but if you use a Development Environment, such as Code::Blocks, you could create a pre-build script to move the relevant icons to the .glade file's directory, and then also a post-build script to move them back.

I'm using Code::Blocks and see that my icon files are also in the same directory as my .glade file, and it would be better to have them in an "Images" folder...but it's not *that* big a deal for me.

---

### Post by giuspen on 2009-01-01
> **rich1939 said:**
> This is not ideal, but if you use a Development Environment, such as Code::Blocks, you could create a pre-build script to move the relevant icons to the .glade file's directory, and then also a post-build script to move them back.

I'm using Code::Blocks and see that my icon files are also in the same directory as my .glade file, and it would be better to have them in an "Images" folder...but it's not *that* big a deal for me.

I program with Geany, good both for Python and C/C++.
Yes it's not a big deal that glade can't see icons more far than its own nose, just strange... I can't realize if it's a bug or if it's something wanted.
Regards.

---

