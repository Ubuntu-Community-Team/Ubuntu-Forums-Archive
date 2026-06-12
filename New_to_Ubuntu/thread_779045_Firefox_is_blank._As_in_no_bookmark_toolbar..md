---
title: "Firefox is blank. As in no bookmark toolbar."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by fraser_m on 2008-05-02
My Firefox is borked. When I open it, there is no homepage, and the Bookmarks Toolbar does not show. There is no address in the Location Bar, and I am at a loss at what to do. Help me please, oh gracious ubuntu community!

I've attached a screenshot. Help.

---

### Post by fraser_m on 2008-05-02
I'm trying the old "blast it to oblivion" technique (purge!) and then reinstalling. Hope it goes well.

---

### Post by Golem XIV on 2008-05-02
Close Firefox and open Nautilus to your home folder, press Ctrl-h to show hidden files and find the .mozilla folder.

Copy this folder somewhere for backup purposes and then delete the original (or even better, rename it and remove the period in front - this will make it visible if you need to restore later).  This will remove all previous settings in Firefox.

Restart Firefox.  It will create a new .mozilla folder with default settings and (hopefully) fix your problem.  You can then copy things like your bookmarks from the old backed up folder to the new one.

Good luck!

---

### Post by fraser_m on 2008-05-02
I'm assuming that your method is just an easier method than mine, but I forgot to back it up just in case...

Oh well, TimeVault will save me!

My method doesn't work. I'll try yours.

---

### Post by sailor2001 on 2008-05-02
did you "view/show/hide" your tool bars?

---

### Post by fraser_m on 2008-05-02
Thanks, it's fixied by removing the .mozilla folder!

It's all perfecto now!

---

### Post by tylerross546 on 2008-12-18
Thanks so much.  Deleting the .mozilla folder worked for me.

-Tyler

---

