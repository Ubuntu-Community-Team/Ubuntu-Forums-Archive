---
title: "How to combine RAR files"
date: 2007-05-29
forum: Programming Talk
---

### Post by oSunTERo on 2007-05-29
I  download game from bittorrent.. but it's a split files have to combine. It's many files about 98 files. I try to use Ark and Unrar but I don't know I use it correctly yet. I'm new on linux.

Please tech me to combine rar files please ... Thank you

---

### Post by yabbadabbadont on 2007-05-29
Open a terminal.  Applications->Accessories->Terminal  
Run:
```
unrar x mario_party_8.r00
```

Edit: By the way, if you are going to pirate a game, at least pirate a *good* game...  :p

---

### Post by oSunTERo on 2007-05-29
:p thank you very much...

I wonder .. I try this code in terminal before I post this topic...

But I get error extract files...  Now it's slove my problem  Thank you

---

### Post by ZaiFox on 2008-06-16
I got files going from r00 to r23 en when I try this:
```

sudo unrar e something.s01e08.r00

```

i get the following output:
```

Extracting from something.s01e08.r00

WARNING: You need to start extraction from a previous volume to unpack something.s01e08.avi

Extracting from something.s01e08.r01
.
.
.
Extracting from something.s01e08.r23

No files to extract

```

Any idea?

thx!

---

### Post by geirha on 2008-06-16
The first file usually has .rar-extention. ```
unrar x *.rar
```

---

### Post by ZaiFox on 2008-06-17
I got only files going from something.s01e08.r00 to something.s01e08.r23 and one .nfo and one .sfv file.
So when I try
```

unrar x *.rar

```
I get error:
```

No files to extract

```

I also tried:
```

sudo unrar e something.s01e08.r00.rar
sudo unrar x something.s01e08.r00.rar

```
But nothing seems to work.
When I double-click in the file browser on one of the files, I see the packed file but I can't extract it.
I have installed rar and unrar from the repositories.

I also know the files are ok because I can extract them in windows.

Thx for the help!

---

### Post by janfsd on 2008-06-17
Try with p7zip. You might need to install it from the repos (with the rar module). 
Maybe you need a password to extract those files. Sometimes the archive manager doesn't ask for password...

---

### Post by ZaiFox on 2008-06-17
> **geirha said:**
> The first file usually has .rar-extention. ```
unrar x *.rar
```

You are right, I accidently removed the .rar file.

Thx for the help!

---

### Post by Arkaman on 2009-06-10
This helped thanks.

---

### Post by Can+~ on 2009-06-10
you can open the first one, or the .rar that comes with it and extract it normally; it will automagically merge them.

---

### Post by Clancy_s on 2009-06-15
Alternatively if you have unrar installed, right click on the first file in nautilus and select "extract here"

This is particularly useful when there are gaps in the file name, which tends to cause problems in the terminal.

---

### Post by suitedaces on 2009-11-24
Thanks folks, this thread saved me a lot of time searching different programs!

---

### Post by whistlerspa on 2009-11-26
> **Clancy_s said:**
> Alternatively if you have unrar installed, right click on the first file in nautilus and select "extract here"

This is particularly useful when there are gaps in the file name, which tends to cause problems in the terminal.

However i found that I needed unrar to do this - unrar-free didn't work.

---

### Post by luismgl on 2011-04-25
> **whistlerspa said:**
> However i found that I needed unrar to do this - unrar-free didn't work.


sorry for reviving this old thread
I have the same issue. unrar-free does not merge files together.

---

### Post by hakermania on 2011-04-25
> **luismgl said:**
> sorry for reviving this old thread
I have the same issue. unrar-free does not merge files together.

Download unrar. It is free and I can use it as long as I want AFAIK

---

### Post by luismgl on 2011-04-25
I have unrar (non free version) and right clicking on the part 1 file and selecting Extract Here doesn't merge parts. Am I doing something wrong here?

---

### Post by lovetaart on 2011-12-26
> **geirha said:**
> The first file usually has .rar-extention. ```
unrar x *.rar
```

It works! Thanks dude :D

---

### Post by Wolfgang Griech on 2012-05-15
and exactly the same also works with standard graphical ark, just click on the first .rar (there can be more..) in dolphin (or whatsoever..) and open it, and everything is already there, just extract it graphically, no real difference to mickeymouse stuff..

---

