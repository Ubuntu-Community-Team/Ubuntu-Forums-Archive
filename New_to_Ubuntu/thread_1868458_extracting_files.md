---
title: "extracting files"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by rockford86 on 2011-10-24
"Use ImgBurn** to burn the extracted ISO file..." is what i'm being told, however i just discovered the Terminal today and have no idea how to do this operations equivilant on linux? i mean, what do i use and how do i get my downloaded file "extracted" and ready to burn? And will the Brasero Burner work?

---

### Post by Jaybyrrd on 2011-10-24
I take it the file is in a .zip or .rar and the ISO is within it?
 
Edit:

If so try downloading 7-zip:
 
```
 sudo apt-get install unrar p7zip p7zip-full 
```
 
Then right-click it and there should be an "unpack" in the selection. For more info see: [http://ubuntuforums.org/archive/index.php/t-782668.html](http://ubuntuforums.org/archive/index.php/t-782668.html)

---

### Post by roton on 2011-10-24
What type of file is it? To be honest you shouldn't need terminal. Just double click the file to get extract option, and then open it with Brasero to burn.

---

### Post by Jaybyrrd on 2011-10-24
Ubuntu does have a built in Archive Manager, but 7-Zip File Manager makes life that much better.

---

### Post by sandyd on 2011-10-24
> **rockford86 said:**
> "Use ImgBurn** to burn the extracted ISO file..." is what i'm being told, however i just discovered the Terminal today and have no idea how to do this operations equivilant on linux? i mean, what do i use and how do i get my downloaded file "extracted" and ready to burn? And will the Brasero Burner work?
If your burning an iso, right clicking on the iso, and choosing brasero will work.

If your extracting an archive, just double click to open the archive manager.

If your extracting a rar, make sure you install unrar or rar

---

### Post by mike555 on 2011-10-24
Be sure to burn the .iso as an image ......  I'm assuming your talking about a Linux .iso

---

