---
title: "Customize Applications Menu"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by JacoLouw on 2008-07-03
Hi there,

Is there a way to permanently remove a launcher from the Applications Menu?

I know about the Main Menu Editor, but it does not completely remove the item because in the /home/<username>/.config/menus/settings.menu file, all it does is append a '<Deleted/>' token to the end of the menu item. So, is there a way to completely remove this Launcher, instead of just 'disabling' it via Main Menu Editor?

---

### Post by AliTabuger7 on 2008-07-03
I believe it does this because updates to the package will place the launcher back on the menu.
It'll be quite a hassle, but I think you could just delete the entire entry for that launcher in the menu file.
Why do you need to remove it from the menu?

---

### Post by JacoLouw on 2008-07-03
Yeah, I tried that. It ends up that it leaves it on the menu after you deleted the entry. If you then go into Edit menu and disable it, it ends up adding that entry back into the list with the diabled tag again.

I used Wine and the uninstall program (remove applications) did not remove the entries in the Programs directory. Is there a direcroy in the Virtual Drive of Wine were you can delete these launchers so they disappear from the Menu?

I remember there was a directory in Windows to remove/add items on the Start Menu, is it the same for Wine?

---

### Post by AliTabuger7 on 2008-07-03
If the program you are trying to remove is from wine, and you are willing to destroy wine to get it off, you can go to synaptic and "completely remove" wine, but it will effect other users too.

There must be like a master menu configuration file somewhere, because other/new users will receive menus that have the installed applications too.

If you would like to disable it for all users, you can run "gksu alacarte".

---

### Post by gettinoriginal on 2008-07-03
Confused as to what you are asking.  I just right click on Applications on panel, edit menu, and uncheck what I don't want there, and poof, gone. :)

---

### Post by JacoLouw on 2008-07-03
Ok. I finally figured it out thanks to the directories listed in the applications.menu configuration file.

I deleted all the '<deleted/>' tags from the /home/jacobus/.config/menus/applications.menu file. Therefore, all the deleted items deleted by Edit Menu appeared again.
I then went into the /home/jacobus/.local/share/applications/wine/Programs directory and deleted the files I didn't want. 
Finally, I went into /home/jacobus/.config/menus/applications-merged and deleted all the .menu files of the items I deleted in the Programs directory.

Now it doesn't appear in Edit Menu's as italic and is removed completly from the applications.menu file.

---

