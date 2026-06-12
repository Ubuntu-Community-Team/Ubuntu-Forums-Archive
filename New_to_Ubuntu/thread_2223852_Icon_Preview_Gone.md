---
title: "Icon Preview Gone"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-05-13
Not sure what this is called (sorry) but having been messing about with folder previewing my icons have changed appearence.  I have deleted my /.cash/thumbnail contents but notice that the /.cash/thumbnails folder has a lock symbol on it.  The attached shows what my Desktop icons look like.

---

### Post by Quarkrad on 2014-05-13
I've launched Dolphin and navigated to Home - Preferences/Preview and checked the Show Preview box.  Now I can 'see' the desktop icons.  However, I guess my normal desktop is managed by nautilus as there is no change - tried changed the nautilus proview optio to Aways or Local Files but it makes no difference.

---

### Post by Quarkrad on 2014-05-13
The solution was **sudo chmod -R 777 /home/x/.cache/thumbnails/**

---

