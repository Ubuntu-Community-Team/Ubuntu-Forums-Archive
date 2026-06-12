---
title: "tar.gz Files, How Dya Open Them?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by londonlad on 2008-06-02
hi all,
 
i may of found a driver that i need, but its in tar.gz format, how do i open it?

---

### Post by rampageoberon on 2008-06-02
```
tar -xzf <filename>
```

This will extract in the current dir

---

### Post by vamsibethapudy on 2008-06-02
use an archive manager.
if it doesnot open on clicking, then right-click, open with other application & choose archive manager.
If u dont have it install it

---

### Post by T2manner on 2008-06-02
right click it
extract here

---

### Post by bumanie on 2008-06-02
That is a compressed binary file that needs to be extracted and then has to be compiled. To get the compiler > sudo apt-get install build-essential Go [here]("http://monkeyblog.org/ubuntu/installing/") for instructions on installing.

---

### Post by ericartman on 2008-06-02
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

one of my fav's

good luck

Cart

---

### Post by Sinkingships7 on 2008-06-02
> **bumanie said:**
> That is a compressed binary file that needs to be extracted and then has to be compiled. To get the compiler  Go [here]("http://monkeyblog.org/ubuntu/installing/") for instructions on installing.

Not that your advice wasn't good, but it's important to know that tar.gz is just a compression format; like zip or rar. It doesn't always mean it's source code.

---

### Post by menschtx on 2008-06-02
I tried your link about now to install anything and followed information for using the terminal upon which I received an error:  Couldn't find any package whose name or description matched "ngplant-0.9.7.tar.gz"
I can see the item in a folder, what gives?

---

### Post by menschtx on 2008-06-02
once the extraction is done and the folder is availible shouldn't it open and begin running - I see the folder for ngplant-0.9.7.tar.gz but then theres about 15 mini-folders inside, I have read the install info, but don't understand. help

---

### Post by Dougie187 on 2008-06-02
What did you type to get that error?

---

### Post by bumanie on 2008-06-02
Could you post a copy of the install instructions. Also have you downloaded and extracted the tar.gz to your desktop, if not where have you extracted it?

---

### Post by SteveNorman on 2008-06-02
are you using these instructions?
[http://www.opendimension.org/blender_en/ngplant_from_source.php](http://www.opendimension.org/blender_en/ngplant_from_source.php)

to extract the tar file, make sure you are in the directory you downloaded the tarball to

If there is a file on your desktop for it then in a terminal type

```
cd Desktop
```

then unpack it, and do the rest of the instructions on the webpage, but replace ngplant_version_number with what ever it is named in the tar file

---

### Post by spike_naples on 2009-03-23
Thank you. Sounds complicated to a newbie like me but I hope to make sense of all this.

---

### Post by theozzlives on 2009-03-23
Double click on them.

---

### Post by caph1993 on 2011-06-24
Check this app, It installs the common packages of linux, its easy and very simply.
Its growing and starting being developed, but it’s very good!!!
supports:
.tar.gz
.tar.bz2
.tar
.tgz
.deb
.rpm
.bin
Its name is  “EPI installer” (EasyPackageInstaller)
google “EPI installer”  or follow this link to download:
 [http://sourceforge.net/projects/epiinstaller/files](http://sourceforge.net/projects/epiinstaller/files)
 Recommended, if you prefer clicking than writing, download it!, sure it solves your problems:D

---

