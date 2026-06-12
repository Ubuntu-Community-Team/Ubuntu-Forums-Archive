---
title: "Zipping files"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Polish Rifle on 2008-09-21
Is there a way to zip files without making them go to Evolution Email.  I actually don't have Evolution Email installed so Ubuntu won't allow me to zip files.

---

### Post by Mornedhel on 2008-09-21
In Nautilus (your file explorer), select the files you wish to compress, right-click and select "Create archive".

---

### Post by nowshining on 2008-09-21
they get put in tar.gz format by default and get put in the /home/username directory by default...

---

### Post by Mornedhel on 2008-09-21
Selecting ".zip" and changing the location will probably help :)

---

### Post by steveneddy on 2008-09-21
If it's on the Desktop, just right click, Create Archive, select destination and file type (.tar.gz, .jar, etc.)

---

### Post by Silent Ninja on 2008-09-21
Is there a way to zip / rar files with a password so you have to use it to see / extract the files ?

I've used to do it with winzip and winrar, but I've not understood how it works on Ubuntu. I was able to extract this files but not make them.

---

### Post by Mornedhel on 2008-09-21
Start file-roller (the Gnome default archiving application), create a new archive, Edit > Password.

Alternatively, use zip from the command line with the -e (as Encrypt) argument.

---

### Post by Polish Rifle on 2008-09-21
Ah yes, found it.  Man, I feel like an idiot, but then again...I've never used ubuntu before.  Thanks guys.

---

### Post by Polish Rifle on 2008-09-22
Sorry for the double post.  

So I zipped a folder and I checked the size and it was the same amount of MBs....

---

### Post by niteshifter on 2008-09-22
> **Polish Rifle said:**
> 
So I zipped a folder and I checked the size and it was the same amount of MBs....

What kind of files were in the folder? Some files - multimedia in particular - are already compressed (JPEG, JPG, MPEG, MP3, etc) and won't compress much further.

---

### Post by nowshining on 2008-09-22
> **niteshifter said:**
> What kind of files were in the folder? Some files - multimedia in particular - are already compressed (JPEG, JPG, MPEG, MP3, etc) and won't compress much further.

i disagree, sometimes i've had jpg files that were 1 megabyte +- when compressed it would be like 100-200 kilobyte :)

---

### Post by Polish Rifle on 2008-09-22
They were jpegs, and I take that back.  They were 14.8 MB uncompressed, 14.6 zipped :)


So, yeah....

---

### Post by niteshifter on 2008-09-22
> **nowshining said:**
> i disagree, sometimes i've had jpg files that were 1 megabyte +- when compressed it would be like 100-200 kilobyte :)

The JPEG spec allows for variable compression. Fire up The GIMP, load or create a large bitmap image (a few MB worth), save it as as JPEG - a dialog will pop up where you may set the "quality" (compression). Move the slider to the low end and save the file.

Now feed that file to zip / gzip / bzip. It won't compress much and the "compressed" file can even be larger than the original.

---

