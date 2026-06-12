---
title: "I got .rar files i need to open..."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by projecthikari on 2008-11-01
How would I go about opening . rar files? It seems it's not supported.

---

### Post by nhasian on 2008-11-01
try:

```
sudo apt-get install unrar
```

that should install support for rar.

---

### Post by DeathWyrm on 2008-11-01
Best thing would be to install 7-zip and then you can extract it.  It's in the repositories and will open most compressed files including .RAR

---

### Post by Rhubarb on 2008-11-01
The easiest way (in my opinion) is to open up the terminal (Applications --> Accessories --> Terminal), and run this:
```
sudo aptitude install p7zip-full p7zip-rar
```
Then enter in your password when prompted.

Once done you can just double click on the rar file, and it'll open up for you so you can easily extract it.

---

### Post by rogkmyers on 2008-11-03
i just installed unrar

sudo  apt-get install unrar

Once it's installed just right click on your rar archive and select open with "archive manager".

Works like a charm!!

Roger

---

### Post by sjamedee on 2008-11-04
7zip does not work with .rar files at least not on my computer. i tried installing it several times and it would not open the .rar files. i finally had to use unrar.

---

### Post by aboud on 2008-11-04
i remmber i unziped rar file with the usual archive manager roller, but now it's not working i'm using unrar.

---

### Post by uarale on 2008-11-04
To deal with .rar files in Ubuntu, use rar package
$ sudo apt-get install rar

To extract a .rar file, just use
$ rar x file.rar
This command also be used to join several .rar files, like
$ rar x file.part1.rar

To compress
$ rar a filename
use -v param to split, like
$ rar a -v1M test.mp3

---

### Post by dzsulius on 2008-11-10
Thanks Rhubarb
I did it like you said and worked perfectly for me.Cool.
Thanks again

---

