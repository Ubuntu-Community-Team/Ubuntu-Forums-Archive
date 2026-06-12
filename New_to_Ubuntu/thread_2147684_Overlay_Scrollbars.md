---
title: "Overlay Scrollbars"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by cmcanulty on 2013-05-22
I am running 12.04 and today I have the ***** overlay scrollbars in gksudo nautilus but the old scrollbars in regular nautilus. I hate them and have tried everything to get rid of them but now in gksudo nautilus they are back.

---

### Post by ubu_dynamite on 2013-05-22
Just remove the following and they should be gone i think.

overlay-scrollbar
overlay-scrollbar-gtk2
overlay-scrollbar-gtk3

---

### Post by Paqman on 2013-05-22
+1 for removing overlay-scrollbar. I just don't like them, removing those packages is one of the first things I do after installing Ubuntu.

---

### Post by cmcanulty on 2013-05-22
what do I do to remove those three files? I have done the remove scrollbars fix

---

### Post by ubu_dynamite on 2013-05-22
Open a terminal paste the following and press enter.

Ubuntu 13.04 Raring Ringtail
```
sudo apt-get remove overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3 
```

---

### Post by ubu_dynamite on 2013-05-22
Looks like precise has some other package names.

Ubuntu 12.04 Precise Pangolin
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0
```

Ubuntu 13.04 Raring Ringtail
```
sudo apt-get remove overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3
```

---

### Post by cmcanulty on 2013-05-23
Still there in gksudo nautilus I did log out and in but didn't restart

---

### Post by ibjsb4 on 2013-05-23
Will this work?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Disable_Overlay_Scrollbars](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Disable_Overlay_Scrollbars)

In your other thread you say that drag and drop wont work.  Me wonders if there is a bigger problem here.

---

### Post by cmcanulty on 2013-05-23
Drag and drop works for apps from menu. Are you sure it should work for a file? It doesn't even if I drag while holding win+alt

---

### Post by ibjsb4 on 2013-05-23
> **cmcanulty said:**
> Drag and drop works for apps from menu. Are you sure it should work for a file? It doesn't even if I drag while holding win+alt

For me, just left click and drag works on files and folders.  Im running meticily, if your running compiz that of course would be different.

---

