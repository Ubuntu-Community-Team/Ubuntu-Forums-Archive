---
title: "Wine Unintall but still showing on the program list"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-24
Hi all,

I uninstalled a program in wine but wheni check in program list it is still there. when i check uninstaller nothing is on list. who do i clear the list?

---

### Post by Hospadar on 2008-05-24
the reason those shortcuts don't get removed is because wine (not the actual program running under wine) created the shortcuts, and so the uninstaller (which is a windows program run through wine) doesn't really know where to remove them, and wine doesn't really keep track of them.  To remove them from your start menu, right-click->edit menues (on the Applications/Places/System menu), go down to wine, and either uncheck (hide) or delete the unwanted shortcuts.

Hope this helps

---

### Post by bartkl on 2008-05-24
Thanks it was helpful for me too. :)

---

### Post by JohnsShadow on 2009-03-04
ok but how do i remove the directorys after they are deleted?
im trying to clean out my system and save as much space as possible


how do we fix this from happening in the future?

---

### Post by nachos99 on 2009-03-05
i had a similar problem and the terminal commands below helped me uninstall cleanly.

[https://help.ubuntu.com/community/Wine#Uninstalling%20Wine%20Applications](https://help.ubuntu.com/community/Wine#Uninstalling%20Wine%20Applications)


5. Uninstalling applications

5.1. How do I uninstall Windows applications?

Wine has its own built-in uninstaller - the equivalent of Windows' "Add/Remove Programs" function for running standardized uninstallers. In recent versions, a shortcut has been added to Wine's menu, along with a shortcut to winecfg.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

---

### Post by ArinSky on 2009-11-15
> **nachos99 said:**
> i had a similar problem and the terminal commands below helped me uninstall cleanly.

[https://help.ubuntu.com/community/Wine#Uninstalling%20Wine%20Applications](https://help.ubuntu.com/community/Wine#Uninstalling%20Wine%20Applications)


5. Uninstalling applications

5.1. How do I uninstall Windows applications?

Wine has its own built-in uninstaller - the equivalent of Windows' "Add/Remove Programs" function for running standardized uninstallers. In recent versions, a shortcut has been added to Wine's menu, along with a shortcut to winecfg.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

A helpful hint, if you have a program that isn't deleting, you don't have to completely uninstall. Instead, delete the folder of the program from your ~/.wine/drive_c/Program Files folder, then remove all instances in your ~/.config/menus/applications-merged folder that have your program name, and do the same for the ~/.local/share/applications and ~/.local/share/desktop-directories folders as well. 

This removes the program data, as well as the menus wine created for the program. you can also look through ~/.local/share/icons and delete the icon from the file if you want, though it wont display either way.

---

### Post by Shaun_Yute on 2012-07-20
> **nachos99 said:**
> i had a similar problem and the terminal commands below helped me uninstall cleanly.

[https://help.ubuntu.com/community/Wine#Uninstalling%20Wine%20Applications](https://help.ubuntu.com/community/Wine#Uninstalling%20Wine%20Applications)


5. Uninstalling applications

5.1. How do I uninstall Windows applications?

Wine has its own built-in uninstaller - the equivalent of Windows' "Add/Remove Programs" function for running standardized uninstallers. In recent versions, a shortcut has been added to Wine's menu, along with a shortcut to winecfg.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

Thank you, this even helped me in Ubuntu 12.04. That was so annoying removing everything then still having the icons. Thank you for your expertise.

---

