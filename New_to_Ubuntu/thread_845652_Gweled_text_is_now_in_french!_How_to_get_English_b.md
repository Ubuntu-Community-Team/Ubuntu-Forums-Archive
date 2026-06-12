---
title: "Gweled text is now in french! How to get English back?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by jondecker76 on 2008-06-30
After installing 8.04, I noticed that Gweled has all of its text in French. I seen this on a fresh install, as well as an upgrade from 0710 to 0804.

How can I change this back to English?

---

### Post by sayakb on 2008-06-30
I have no idea about the app. But you can try this: Press Alt+F2 and type in **gconf-editor** and press Enter. Navigate to /apps/gweled and check for any language related variables there.

---

### Post by jondecker76 on 2008-06-30
no gweled listed...
No hidden .gweled folder either in home

---

### Post by KIAaze on 2008-06-30
I installed gweled from the source package on their website and have a hidden ~/.gweled text file.

But it only contains "00".

I got the menu in English, but the game itself didn't work at all: no game and unresponsive menu.
(Lots of "(gweled:10311): libglade-WARNING **: could not find signal handler 'drawing_area_button_event_cb'." errors...)

But since I'm running Intrepid, I won't even bother trying to find out why now.

---

