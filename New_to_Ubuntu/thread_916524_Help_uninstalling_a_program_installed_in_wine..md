---
title: "Help uninstalling a program installed in wine."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Squall1617 on 2008-09-11
I was trying to install iTunes using wine and I only got as far a QuickTime installing. iTunes refused though so I gave up and ran the uninstall for QuickTime. However it never uninstalls, it just says that it does but it is still in the program folder in wine. Anyone have a suggestion on how I can get rid of it??

---

### Post by iaculallad on 2008-09-11
Excerpt from Ubuntu Wiki:

> Open up a terminal window and type "uninstaller" - this will open up a program similar to Windows' "add/remove programs" control panel, allowing you to uninstall applications from a Wine installation. Running uninstall programs directly via Wine should also work normally. Alternatively, you could also simply delete the folder of the application. However, as when done in Windows, this method will be "unclean" and will not remove the program's configuration from the Wine registry like using an uninstaller will.

---

### Post by Elephantman5 on 2008-09-11
> **iaculallad said:**
> Excerpt from Ubuntu Wiki:
Also delete it from menu edit.

---

### Post by Squall1617 on 2008-09-11
> **iaculallad said:**
> Excerpt from Ubuntu Wiki:

I tried the uninstall in the terminal command and this came up in the terminal.
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050 for L"C:\\windows\\temp\\msie68b.tmp"

---

### Post by Gannon8 on 2008-09-11
Or you could go to the C drive and just delete the program from the Program File's directory. :) Not the best solution, but it works.

---

### Post by Elephantman5 on 2008-09-11
> **Squall1617 said:**
> I tried the uninstall in the terminal command and this came up in the terminal.
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050 for L"C:\\windows\\temp\\msie68b.tmp"
Just do what Gannon said. wine programs are only stored in their directory.
Delete it from the .wine directory in your Home, and delete its entry in Edit Menus

---

### Post by Squall1617 on 2008-09-12
Thanks guys. I think that did it.

---

### Post by Elephantman5 on 2008-09-12
> **Squall1617 said:**
> Thanks guys. I think that did it.
No problem man.

---

