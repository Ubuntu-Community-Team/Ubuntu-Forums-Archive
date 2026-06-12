---
title: "Bleachbit erasing my Banshee Album Covers"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-08-04
Hi All

When I use Bleachbit, it erases some, but not all, of my Album Covers in Banshee music player. Where are these album covers stored, and how can I stop bleachbit from deleting them?

Glenn.

---

### Post by VMC on 2013-08-04
Go to Edit > Preferences > Whitelist. Then add your folder where these album covers exists.

---

### Post by kostkon on 2013-08-04
Propably they are stored in ~/.cache and I assume you are telling bleachbit to clear your cache.

---

### Post by Senior_Buckethead on 2013-08-04
Thanks for that.

I had a look and Banshee's Album Covers are in: **home>.cache>media-art**

But i've found a problem. When I open Bleachbit, and go to: Edit>Preferences>Whitelist And Select folder, it won't display the hidden folders in my home directory, of which cache>media-art, is.
Same effect when I select files in same directory.

I found out that the option to unselect in Bleachbit is **System>cache**. I was surprised that by leaving **Deep Scan>Thumbs.db** and **Thumbnails>cache** both erased the contents of the media-art folder.

I'll have to raise that with the Bleachbit people. Thanks everyone.

---

### Post by VMC on 2013-08-05
> **Senior_Buckethead said:**
> Thanks for that.

I had a look and Banshee's Album Covers are in: **home>.cache>media-art**

But i've found a problem. When I open Bleachbit, and go to: Edit>Preferences>Whitelist And Select folder, it won't display the hidden folders in my home directory, of which cache>media-art, is....
When you get to the Whitelist, just push the "pencil" icon "Location will pop up, then type "." , then all the ".folders" will appear. Click on the one you want.

---

