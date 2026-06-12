---
title: "Todays updates killed unity"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-08-11
Done todays updates and now unity just totally died on me, i cant get a desktop and much to my surprise unity 2d has gone and instead my desktop manager options are unity (not working), gnome3 or gnome-classic, i havent installed gnome3 so i was quite surprised to see canonical put this into the default install,

definitely wasnt there before todays updates because i only just logged into unity2d this morning

---

### Post by jbicha on 2011-08-11
Sorry about your difficulties, but be aware that today is a Unity transition and it's not complete yet. The new unity-place-applications for instance has not been packaged yet for instance.

Just be a bit more patient and please read what update-manager or sudo apt-get dist-upgrade is telling you before clicking to continue. The new unity-2d on amd64 is just now finishing being built so yes, a full upgrade at this moment would remove unity-2d since it is compatible with the new Unity.

---

### Post by zekopeko on 2011-08-11
Try installing unity-2d and unity package. Be careful in the future when using dist-upgrade. I got bitten by last week.

---

### Post by CaptainMark on 2011-08-12
Sorry I didn't mean to give the impression this is a nagging post, I love alpha testing, and the roulette wheel that comes with it, I know it will all piece together soon, I was just canvassing an opinion, 

Any one know if canonical is planning on including gnome3 on a default install, last I heard they were against the idea

---

### Post by lucazade on 2011-08-12
> **CaptainMark said:**
> 
Any one know if canonical is planning on including gnome3 on a default install, last I heard they were against the idea

oneiric is based on gnome3, only the shell installed by default is a different one (gnome-shell <> unity).
all the applications of gnome3 are included in this release.

---

