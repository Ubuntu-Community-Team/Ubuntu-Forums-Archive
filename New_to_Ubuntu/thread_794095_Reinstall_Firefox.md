---
title: "Reinstall Firefox"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Hoom@n on 2008-05-14
Hi! How can I remove firefox completely and install it again? (I didn't use ubuntu for a while, but this time when I came to firefox it was very slow! So I wanna install it again.+I didn't install any new add-ons!)

---

### Post by SunnyRabbiera on 2008-05-14
Well the first thing you should do is try to uninstall firefox via synaptic, go up to system, then to administration and click on "synaptic package manager"
in that search for firefox
right or left click the box next to the installed firefox package (installed packages are indicated by a green box) and select makr for removal.
If it needs to remove extra packages click "apply"
and again "apply"
the rest should be straightforward.
also you may want to delete your firefox directory located in your home folder, hit ctrl+h to unhide the folder contents and delete your mozilla folder...
but if you have anything in it make sure to back up your bookmarks and coookies if you want to, you can find them inside the firefox folder, they will be inside another folder marked with a strange number next to it.

---

### Post by shifty_powers on 2008-05-14
```
sudo apt-get purge firefox

sudo apt-get install firefox
```

you can specify firefo-2.0 iirc, if you want that instead of firefox 3beta5

---

### Post by pricetech on 2008-05-14
Synaoptic will let you accomplish both the uninstall and the reinstall.  In between you need to delete the .mozilla folder in your home directory.

I took 3 off and put 2 in it's place because 3 was buggy for me.

---

### Post by philinux on 2008-05-14
Don't forget to backup or export your bookmarks first, if you delete your profile folder.

---

