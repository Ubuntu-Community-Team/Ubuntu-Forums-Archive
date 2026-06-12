---
title: "[SOLVED] Help with firefox"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by famous3warriors on 2008-05-11
I am about to do an upgrade from gutsy to hardy heron i386.  I am going to do a complete brand new install.  I was wondering is there any way to keep the websites that you bookmarked in Firefox without having to rebook mark them.  I was taking a look at the prefences and I did not see anything.  Thanks I really do appreciate you help.:guitar:

---

### Post by drs305 on 2008-05-11
You can find and save your entire profile or just save the bookmarks.html file. One way to save the bookmarks is Bookmarks, Organize Bookmarks, File, Export and save them to a flash drive or another partition.

You can find where your bookmarks (and profile) are with:
```
sudo find / | grep bookmarks.html
```

The profiles are often in /home/yourusername/.mozilla/firefox/some8charactername.default/ unless you have created one by another name.

---

### Post by famous3warriors on 2008-05-11
Thanks drs305 I really do appreciate your help.:guitar:

---

### Post by thiebaude on 2008-05-11
If you want you can save your bookmarks to a floppy disk, like i do.

---

### Post by Tsurugi13 on 2008-05-11
If you're using firefox 2, try getting the [Foxmarks Bookmark Synchronizer]("https://addons.mozilla.org/en-US/firefox/addon/2410"). It backs up Bookmarks to a URL that you can get them from with or without the addon installed!

---

