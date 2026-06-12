---
title: "How do I delete a file or dir on my C:/ drive from Terminal?"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by RayArdia on 2014-05-13
I have Sketchup installed in Wine, ie on drive C:/. How do I delete it, as I want to install an older version of SU?

---

### Post by HiImTye on 2014-05-13
use```
wine uninstaller
```to remove it with the least breakage, unless you wish to just remove your wine files, in which case you would```
rm "$HOME"/.wine -R
```be very careful when using this command, and make sure it is typed correctly.

---

### Post by monkeybrain20122 on 2014-05-13
> **HiImTye said:**
> .. unless you wish to just remove your wine files, in which case you would```
rm "$HOME"/.wine -R
```be very careful when using this command, and make sure it is typed correctly.

  Well if you have to be very careful with the command then just don't use it. :) just open the file manager, show hidden file, right click and delete .wine, that's it. 

In that case OP would also need to go to .local/share/applications to delete the wine folder as you don't want launcher icons for non existing wine applications to lie around (this step should be taken even with the wine uninstaller as it doesn't remove the icon as far as i can remember)

---

### Post by RayArdia on 2014-05-13
> **monkeybrain20122 said:**
> Well if you have to be very careful with the command then just don't use it. :) just open the file manager, show hidden file, right click and delete .wine, that's it. 

In that case OP would also need to go to .local/share/applications to delete the wine folder as you don't want launcher icons for non existing wine applications to lie around (this step should be taken even with the wine uninstaller as it doesn't remove the icon as far as i can remember)

Thank you monkeybrain, I'm trying to follow your advice as it sounds less dangerous.
Don't understand ref to OP, what's that?
In file manager I don't have the option to delete Wine, just send it to trash, is this right?
When I do manage to delete wine will I delete the Sketchup files too?

Sorry to be obtuse, but I'd just like to get it right!

---

### Post by grahammechanical on 2014-05-13
If we want to un-install an Windows application that we installed using wine then we can use the wine utility that was installed when we installed wine. It is called Uninstall Wine software.

There is also a folder/application called Browse Drive C: That will open Nautilus at .wine/dosdevices/c: and it is there we find everything connected to wine and applications install with wine.

Regards.

---

### Post by monkeybrain20122 on 2014-05-13
> **RayArdia said:**
> Thank you monkeybrain, I'm trying to follow your advice as it sounds less dangerous.
Don't understand ref to OP, what's that?
In file manager I don't have the option to delete Wine, just send it to trash, is this right?
When I do manage to delete wine will I delete the Sketchup files too?

Sorry to be obtuse, but I'd just like to get it right!

.wine (see the dot) is a hidden file, you need to display it first. Open nautilus, press ctr+h or in the menu choose show hidden files. 

You are correct that by default you don't have the delete option. I hate the trash, it is stupid, probably inspired by Windows. When you delete something you want it gone, not to be moved to another folder. So to correct this, open nautilus, go to Preferences > Behaviour and check the box "include a delete option.." which will bypass trash. Sorry for forgetting this, since adding delete is always one of the first things I do when installing any Linux, I kind of forget that it is not the default behaviour. :) You can also do 'shift+delete' and that should delete without going to trash.

If you delete .wine you basically remove everything. If that is not what you want, as grahammechanical said use uninstall. You can find it from the dash, just type "uninstall" and click "uninstall wine software", which looks like Windows' add/remove.

Now after that go to .local/share/applications/wine (again note the dot, it is hidden) and  delete the subfolder for the app you just uninstalled so it won't show up in the menu any more.

Edited: I assume you are using standard Ubuntu with Unity. If not you need to modify the steps a bit. I think in all file managers there are options to bypass trash, also "uninstall wine software" should be in the menu if your desktop environment uses a menu.

---

### Post by HiImTye on 2014-05-13
> **monkeybrain20122 said:**
> Well if you have to be very careful with the command then just don't use it. :)
my response was based on[quote=the thread title]from Terminal?[/quote]which implies the user wanting to have a better understanding of his system. my mistake.

---

### Post by RayArdia on 2014-05-14
Thanks to all, especially to monkeybrain for such a clear explanation - I think I've got it now!

I totally agree with comment about 'Trash', glad to get rid of it!

---

