---
title: "Recent Update Put Arduino Files in my Home Folder"
date: 2017-09-20
forum: New to Ubuntu
---

### Post by electrosteam on 2017-09-20
Looking for a few installs of interest recently, Librecad and KiCad are installed and running, Adobe Flash Player and VLC are there but not confirmed as running.
Just noticed there are a couple of Arduino files in my Home folder - 'Socket_Arduino_Nano.3dshapes' and 'Socket_Arduino_Nano.pretty'.

Can anyone inform me what the two extra files do, or are used by ?

Edit: Lubuntu on 17.04
John

---

### Post by wyliecoyoteuk on 2017-09-21
they are Kicad templates

---

### Post by electrosteam on 2017-09-21
Thanks for the confirmation, I suspected something like that.
A bit annoyed, however, that they are in my Home folder.

 Is it normal for applications to put anything in my Home folder ?
Just seems odd to me.

KiCad did one other interesting thing, I also have an icon for it in my Launch Window.
As I get more knowledge on how to modify Linux, I will try to fix these two anomalies.
I think it better to have a category in the Launch Window labelled "Applications" to hold all the installed applications.

John.

---

### Post by wyliecoyoteuk on 2017-09-22
Probably an oversight when compiling the package.
Some applications will create a folder for storage of templates etc, and yes, they would put it in your home folder so that you can access it.
If you go to "view" in the file manager and select "show hidden files" you will see a lot of folders and files that begin with a dot .
These are config files, mail storage, internet cache etc, which are personal to you and need to be in your home folder so that you can access them without using su .

---

### Post by oldos2er on 2017-09-23
> **electrosteam said:**
> Is it normal for applications to put anything in my Home folder ?

I can't speak to arduino as I haven't used it, but yes, it's absolutely normal. Firefox and Thunderbird both keep their data in ~/.mozilla/; many other applications store info in ~/.local/, ~/.config/, and other folders.

---

