---
title: "Gnome keyring manager- Default password????"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by ionizd on 2008-10-05
Hello all,
  I have been trying to configure a WEP passphrase for my wireless network, but whan I enter the passphrase, a window pops up asking for the gnome-keyring default password.  
When I enter my password, the window pops back up in a few seconds asking for it again.  I've only had one password on this laptop- EVER.  Does anyone know what the default password for the keyring is, or how I can either find it or change it?

---

### Post by BandD on 2008-10-05
I had this same problem a while back.  It was really frustrating!  After a lot of googling and what not, it seemed that with Hardy the Ubuntu team basically replaced gnome-keyring-mansger with a program called seahorse.  

The fix was to open Nautilus (the file browser) go to your home directory.  Hit Ctrl+h (to show hidden files and folders).  Go to .gnome2.  Then go to keyrings. And from there delete the default.keyring file.

Or in a terminal:

```
rm ~/.gnome2/keyrings/default.keyring
```

You can look [here]("https://answers.launchpad.net/ubuntu/+source/gnome-keyring-manager/+question/17929") to see a slightly older discussion about this.

---

