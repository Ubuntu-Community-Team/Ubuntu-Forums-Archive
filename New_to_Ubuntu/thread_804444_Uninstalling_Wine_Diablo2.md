---
title: "Uninstalling Wine Diablo2"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Vigh on 2008-05-23
Hi im trying to uninstall diablo2, i typed uninstaller from the terminal, click on diablo 2 and hit uninstall and it came up with the msg-

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

All I want to do is uninstall it so I can follow the guide on installing it properly. I went blind the first time and I dont think I installed it correctly. Now it wont even uninstall. Any help would be appreciated. Cheers Anthony

Also I want to open Open Office Formula, how do I do this? I cant find the executable file anywhere according to add/remove applications it is on the system. Please help.

---

### Post by Xiong Chiamiov on 2008-05-26
If you can't run the uninstaller, then you can delete the files and, if you need to, purge the keys related to it out of the registry.  Your fake C drive is located at .wine/drive_c in your home directory; you can get to it from the wine menu (browse C drive).

The formula part of OOo isn't standalone; it is part of Writer.  You can get to it by going to Insert -> Object -> Formula.

You really shouldn't ask multiple questions in one thread like that.  There may be someone who would be able to answer your OOo question, but doesn't look at the thread because they think it's just about Wine.

---

