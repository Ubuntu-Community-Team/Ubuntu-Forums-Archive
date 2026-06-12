---
title: "[gVim] Tear Off Menus Where?"
date: 2008-12-19
forum: Programming Talk
---

### Post by krinderlin on 2008-12-19
So, I've been fighting to get gvim to have tear off menus.  It's not working out too well.

At first, I found some documentation that said I needed to be using gtk or motif.  So I installed the vim-gtk package and uncommented some bit of black magic my .vimrc (a copy of the default .vimrc) that had a comment about tear off menus.  I still can't get it to work.

I'm 90% certain now that I don't know how to make/drag/pull off/whatever you do to make a tear off menu out of one of your menus.

I've tried using :tearoff but that doesn't work either.  Vim happily informs me that :tearoff is not available in this version.

](*,)

---

### Post by mssever on 2008-12-19
> **krinderlin said:**
> So, I've been fighting to get gvim to have tear off menus.  It's not working out too well.

At first, I found some documentation that said I needed to be using gtk or motif.  So I installed the vim-gtk package and uncommented some bit of black magic my .vimrc (a copy of the default .vimrc) that had a comment about tear off menus.  I still can't get it to work.

I'm 90% certain now that I don't know how to make/drag/pull off/whatever you do to make a tear off menu out of one of your menus.

I've tried using :tearoff but that doesn't work either.  Vim happily informs me that :tearoff is not available in this version.If you can tear off the menus, there will be dashes at the top of the menu. I believe that this is actually a Gnome setting. I set it so long ago that I don't remember how Idid it, but I'm pretty sure it wasn't a gvim-specific change. After all, I get tear-offs in GIMP as well. Search through gconf-editor and see if you can find anything that way.

---

### Post by krinderlin on 2008-12-19
> **mssever said:**
> If you can tear off the menus, there will be dashes at the top of the menu. I believe that this is actually a Gnome setting. I set it so long ago that I don't remember how Idid it, but I'm pretty sure it wasn't a gvim-specific change. After all, I get tear-offs in GIMP as well. Search through gconf-editor and see if you can find anything that way.

For reference of anyone else who reads this thread:

Open gconf-editor.

Navigate to /desktop/gnome/interface in the directory tree.

Find "menus_have_tearoff" in the list of keys.

Tick the tick box.

At this point, I had to reboot the X server (and hence GNOME) with a Ctrl+Alt+Backspace.  However, others may or may not have to do this.

Marking the thread solved and many thanks to msserver for getting me headed in the right direction.

---

