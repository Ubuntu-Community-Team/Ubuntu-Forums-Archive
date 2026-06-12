---
title: "Folder sizes?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by shoaibi on 2008-07-18
Why does ubuntu shown 4.0K as sizes of folders in nautilus and in terminal when i do ls -lh???
Should i show the sum of sizes of all files inside that folder? i even have that "Count files" enables to "Always" inside nautilus Edit  Preferences...
Any idea on how can i get it to work the way i want it to be???

---

### Post by canthus13 on 2008-07-18
ls -lh simply converts the size of a file from bytes to kilobytes.  ls will show (at least in my experience) the size of the directory object itself, and not the size of the contents.  Nautilus also reports this in detailed view.  If you right-click on the directory and select properties in Nautilus, you will get the file count and total size. 

Hope that helps....

--Me

---

### Post by shoaibi on 2008-07-18
well i am not talking about that....
If we view the icons, say in 150% zoom, even then we get the 4K size, which isnt good, i suggest that it should show the actual size...

---

### Post by schauerlich on 2008-07-18
The 4KB you see is not the size of the contents of the folder, but the size of the folder itself. A folder is really just a small file that tells the computer that there are some files inside of it. Those 4KB are what the computer needs to know about where the folder is and such.

---

### Post by shoaibi on 2008-07-18
but i wanna see the total size :( :'(

---

