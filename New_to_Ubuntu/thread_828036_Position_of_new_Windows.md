---
title: "Position of new Windows"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by speedemonV12 on 2008-06-13
Hi guys, 
whenever i open a new window of any sort, or a popup come us from an open aplication, and i click like file -> open, all of my new windows open in the top left of the screen, and the top of the window is under the gnome panel ( i keep it on the top) so I have to move every window that opens down in order to see the top of the window, is there anyway to change this by default, so that i doesnt open under the gnome panel?

---

### Post by sdennie on 2008-06-13
Are you running compiz?  If so try the following:

```

sudo apt-get install compizconfig-settings-manager

```

Then, go to System->Preferences->Advanced Desktop Effects and make sure that Place Windows is turned on (it's towards the bottom).  That should make windows placement more sane.

---

### Post by speedemonV12 on 2008-06-13
that did the trick thanks!

---

