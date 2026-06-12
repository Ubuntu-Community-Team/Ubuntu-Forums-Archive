---
title: "How can I completely remove Thunderbird? settings, addons, etc"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by decktrio on 2012-03-12
Using thunderbird with a yahoo email, I had trouble saving a draft. This message pops up everytime thunderbird tries to sync with the yahoo servers:

[I]Thunderbird
The operation on 'Drafts' did not succeed. The mail server for account [EMAIL="myemail@yahoo.com"]myemail@yahoo.com[/EMAIL] responded: [TRYCREATE] SELECT error - Folder does not exist or server encountered an error.[/I]

I tried removing email accounts, and adding them back. That didn't help.
I've tried uninstalling thunderbird using: sudo apt-get remove thunderbird. However, after restarting my computer and reinstalling thunderbird, I realized that removing thunderbird doesn't actually remove any of my settings. So instead of the clean slate that I desired, I went back to having all the same add-ons and email addresses as before. In fact, now the problematic email address appears twice under my combined inbox.

I would ask at a Thunderbird forum, if I knew of a forum for Thunderbird 10+; I'm using 10.0.2. So instead I figured I'd ask for help here; I use Lubuntu 11.10. Does anyone know how I can ***completely*** remove Thunderbird, all my add-ons, settings, and anything else that I may have changed? ...So that I can reinstall and get back to an ideal "clean slate".

---

### Post by howefield on 2012-03-12
Try removing (or renaming which isn't quite so destructive ;-)) the .thunderbird folder from your /home folder. This folder contains all your settings.

Open Thunderbird and it will create a new .thunderbird folder complete with new profile.

---

### Post by audiomick on 2012-03-12
> **howefield said:**
> Try removing (or renaming which isn't quite so destructive ;-)) the .thunderbird folder from your /home folder. This folder contains all your settings.

Open Thunderbird and it will create a new .thunderbird folder complete with new profile.


Note that this is a hidden folder. You will have to select to view hidden folders in the "view" menu to see it.

---

### Post by decktrio on 2012-03-12
Thanks so much! Especially for responding so quickly.
side note: I'm ashamed that I didn't think of that... oh well.

---

