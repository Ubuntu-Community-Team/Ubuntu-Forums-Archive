---
title: "Update Manager crashes X on show details"
date: 2006-07-12
forum: Repositories &amp; Backports
---

### Post by genzo on 2006-07-12
Basicly I clicked on the little orange icon in the system tray that said theres updates to install.. and it was 108mb worth of downloads, bit much. So i click on Show Details to see whats actually new in this update. And wham. screen goes black and Im back at the login screen???

Running Dapper 32bit on AMD X2 64bit. 2.6.15-25-k7

edit: Updated my kernel to 2.6.15-26-k7 and now it seems fine.

---

### Post by GeDaMo on 2006-07-12
I had the same thing happen to me this morning but it also happened a couple of weeks ago. I have the Show Details box open by default so the Update Manager caused a reset almost immediately after starting.

Dapper, 2.6.15-25-k7, Nvidia video card

---

### Post by rvanzon on 2006-07-25
I have the same problem with 2.6.15-26-386. I think it's something with the NVidia video card, but not sure yet. The problem didn't occur before.
If you still want to upgrade, do the next.

* Open a **terminal** (Applications/Accessories/Terminal)
* type **sudo apt-get upgrade** +enter, give your password and follow the instructions

The tray icon will dissapear afterwards.

---

