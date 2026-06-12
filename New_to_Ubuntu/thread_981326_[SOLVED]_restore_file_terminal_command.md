---
title: "[SOLVED] restore file terminal command"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by le singe on 2008-11-13
are there any terminal commands that will restore a deleted file?  I, for example, deleted a few files using 'rm' remove command and I now don't think I needed to remove them.  Is there an opposite-rm command?

basically, I have the same bug listed here:
[http://ubuntuforums.org/showthread.php?t=964498&highlight=places+folders](http://ubuntuforums.org/showthread.php?t=964498&highlight=places+folders)

and I tried deleting the inode-directory.png files in /usr/share/icons/gnome/.../places but that didn't seem to do the trick.

Anyone figure this out, or do we just have to wait until all the different icon themes eventually get rewritten for the new gnome?

---

### Post by igknighted on 2008-11-13
Unfortunately rm is permanent(like shift-delete in the GUI).  That is why so many people have warnings about using it in their signature, and it always asks you if you are sure before it deletes something (unless you manually disable it with -f).

In the future, use mv to move (essentially rename) a file before an rm.  That way you can mv it to "file.bak", and it will be ignored like it was deleted, but if you realize you need it you can mv it back to its old name.

---

### Post by le singe on 2008-11-13
> **igknighted said:**
> Unfortunately rm is permanent(like shift-delete in the GUI).  That is why so many people have warnings about using it in their signature, and it always asks you if you are sure before it deletes something (unless you manually disable it with -f).


ok.  Actually, I realize now that the code I used was in fact "rm -f" yet I don't know if that makes a difference.

Is there any way to get these files back (some kind of gnome or x refresh...?)

Thanks for your help.

---

### Post by le singe on 2008-11-13
oohhh.... I see now what the -f did.  Well.  I wonder if these files are important

---

### Post by igknighted on 2008-11-13
Whatever the package is that contains the icons (gnome-icons?  someone who knows help?), use 'sudo apt-get remove --purge <icon_package>', and then 'sudo apt-get install <icon_package>'.  It might remove 'ubuntu-desktop', but that's ok.  It doesn't actually mean anything (it's a fake package to make installing the default desktop from scratch easier), but you can reinstall it later if you want.

---

### Post by le singe on 2008-11-13
> **igknighted said:**
> Whatever the package is that contains the icons (gnome-icons?  someone who knows help?), use 'sudo apt-get remove --purge <icon_package>', and then 'sudo apt-get install <icon_package>'.  It might remove 'ubuntu-desktop', but that's ok.  It doesn't actually mean anything (it's a fake package to make installing the default desktop from scratch easier), but you can reinstall it later if you want.

If I do a complete remove of gnome-icon-theme in synaptic, then reinstall it, will that do the same thing, or is the terminal command better to use?

---

### Post by igknighted on 2008-11-13
> **le singe said:**
> If I do a complete remove of gnome-icon-theme in synaptic, then reinstall it, will that do the same thing, or is the terminal command better to use?

I don't know.  I never use the GUI package tools

---

### Post by le singe on 2008-11-13
yep, a simple reinstall did it.

---

