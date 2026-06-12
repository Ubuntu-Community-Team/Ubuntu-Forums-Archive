---
title: "add .mp3 extention"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by drofart on 2011-11-03
Hello friends,

i have downloaded some songs with . extension ,i want to add .mp3 extension to these files in terminal or gui.
How to ? Any help!

Thanks 

Mrinal.

---

### Post by Mark Phelps on 2011-11-03
Typically, MP3 files come with the .mp3 extension.  How do you know these files are MP3's?

---

### Post by haqking on 2011-11-03
> **Mark Phelps said:**
> Typically, MP3 files come with the .mp3 extension.  How do you know these files are MP3's?

+1

you dont make a .mp3 by putting the extension on the end.

if they are .mp3 then you can use the rename or mv command

```
man rename
```

ore the mv command

```
man mv
```

---

### Post by BBQdave on 2011-11-03
> **drofart said:**
> Hello friends,

i have downloaded some songs with . extension ,i want to add .mp3 extension to these files in terminal or gui.
How to ? Any help!

Thanks 

Mrinal.

Not sure what file type you have (no extension).  So maybe try Audicity or your favorite audio program to load file and convert to mp3:confused:

---

### Post by aeiah on 2011-11-03
find out if your files are mp3 or not by using 'file' in a terminal:```
file nameoffile
```

if they aren't, you'll have to convert. if they are, any batch renaming program will do it.

---

### Post by nerdybrunette on 2011-11-03
Your best bet is to do a batch rename. 

See here: [http://scottlinux.com/2011/04/24/batch-rename-files-with-rename/](http://scottlinux.com/2011/04/24/batch-rename-files-with-rename/)

---

### Post by drofart on 2011-11-03
First of all Thanku very very much to every one.
> **Mark Phelps said:**
> Typically, MP3 files come with the .mp3 extension.  How do you know these files are MP3's?
Ya may be but the root problem i faced is that banshee did not detect those files i downloaded from internet.
You can see my last post [HERE]("http://ubuntuforums.org/showthread.php?t=1872822") & after many here & there i found that i just have to add  a .mp3 to the name.
& thats why i started this thread. 

Thank you.

                          > **haqking said:**
> +1

you dont make a .mp3 by putting the extension on the end.

if they are .mp3 then you can use the rename or mv command

```
man rename
```ore the mv command

```
man mv
```

Ya thats why i was looking for

Thank you.

> **aeiah said:**
> find out if your files are mp3 or not by using  'file' in a terminal:```
file nameoffile
```if they aren't, you'll  have to convert. if they are, any batch renaming program will do  it.
  
Thank you dear


> **nerdybrunette said:**
> Your best bet is to do a batch rename. 

See here: [http://scottlinux.com/2011/04/24/batch-rename-files-with-rename/](http://scottlinux.com/2011/04/24/batch-rename-files-with-rename/)

Thank you dear for the link.

Have a nice time all , Take care

Mrinal

---

