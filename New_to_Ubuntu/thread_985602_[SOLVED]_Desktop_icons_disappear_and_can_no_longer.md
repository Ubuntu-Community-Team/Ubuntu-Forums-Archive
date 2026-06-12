---
title: "[SOLVED] Desktop icons disappear and can no longer right click desktop?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by SlingerXL on 2008-11-17
Pretty much just as title says. My desktop icons have disappeared and I can't right click the desktop or drag files there anymore. Totally random occurrence. Everything has always worked fine before. I can still access the files by going to Places>Desktop and it's all there, but they don't show up on the desktop.

??

---

### Post by Bölvaður on 2008-11-17
Did you change any settings that might involve Nautilus or the Desktop?

---

### Post by smacattack on 2008-11-17
I would try pressing Alt+F2 then typing:

metacity --replace

Might work and it can't hurt anyways so it's worth a shot

---

### Post by SlingerXL on 2008-11-17
Didn't mess with desktop or nautilus and the metacity didn't help either. Thanks for the tries, though.

---

### Post by Papa-san on 2008-11-19
I had the exact same thing happen an hour ago. I have not changed anything in any of my settings, so I didn't make it happen. I have done software updates in the last couple of days... Whatever was released except for the firefox three ones.. I tried that browser and it really sux...

This problem exists even when I re-boot into an older kernel. 

I'll subscribe to this thread and wait to see if there is a solution offered.

---

### Post by sirjoebob on 2008-11-19
Just a shot in the dark from somone not experiencing the issue.... 

1. Alt+f2: gconf-editor
2. Apps>Nautilus>Preferences
3. In the right panel, make sure "Show desktop" is checked. Let us know if it works

---

### Post by Papa-san on 2008-11-19
There isn't an option there that says "Show Desktop".

There were some empty checkboxes by things like "show recycle bin", "show computer icon", "show home icon". I checked them, but nothing changed. I'll re-boot again to see if anything happened...

---

### Post by Papa-san on 2008-11-19
After doing that and re-booting, my stuff is back on the desktop, and it responds to the right-click again...

:-)

---

### Post by sarc on 2008-11-19
I'v had GDM do all kinds of weird stuff when my hard disk was almost full.  All back to normal when I cleaned out old files.  I'd check to see if you have enough space on your root directory.

---

### Post by SlingerXL on 2008-11-20
> **Papa-san said:**
> There isn't an option there that says "Show Desktop".

There were some empty checkboxes by things like "show recycle bin", "show computer icon", "show home icon". I checked them, but nothing changed. I'll re-boot again to see if anything happened...

Solved.

---

