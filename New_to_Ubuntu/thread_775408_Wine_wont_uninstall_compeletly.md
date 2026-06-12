---
title: "Wine wont uninstall compeletly"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by leotemp on 2008-04-30
I went to install photoshop cs and it worked but then i accidentally delete the exe and due to another problem at the time i couldn't access my trash can (I know, im terrible) so i decided to just reinstall photoshop, unfortunately i get a giant FAIL for this as photoshop wouldn't install after i uninstall it and i get a dll crash error after the install completes preventing it from working.

The point here is that i think if i could completely remove the remnants of photoshop and wine i could start over and get back to when it worked. I cant test my theory though as even after i completely remove wine via the PM i still have it as a menu item with photoshop as an option (which of course doesn't work). Is there a way i could remove it more thoroughly like manually and would anyone have any advice on how to do that?

---

### Post by kesman on 2008-04-30
```

sudo apt-get purge wine
sudo apt-get autoremove
sudo apt-get autoclean
sudo rm -r ~/.wine
sudo apt-get install wine

```

The second-last line will remove a hidden directory .wine from your /home that contains all the installed applications and wine settings. It will be re-created when you reinstall wine. Also remember to run **winecfg** or wine configuration from the wine-menu.

---

### Post by gandaran on 2008-04-30
you can remove by editing, system»preferences»main menu or go to home/user/.local folder and delete the corresponding entries.

---

### Post by Laser Dude on 2008-04-30
Actually just deleting your ~/.wine directory will reset all Wine's settings, registry keys, etc.

```
rm -r ~/.wine
```

Then reinstall Photoshop as you normally would.

Sudo is not neccessary as it is in the home directory.

---

### Post by Wolfhere on 2008-12-11
Fixed my problem. Thanks

---

