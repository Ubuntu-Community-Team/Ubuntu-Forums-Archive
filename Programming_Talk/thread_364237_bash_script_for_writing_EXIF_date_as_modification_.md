---
title: "bash script for writing EXIF date as modification date"
date: 2007-02-18
forum: Programming Talk
---

### Post by KhaaL on 2007-02-18
I wonder if someone would be kind and tell me how to write the modification date on all *.jpg files in the current folder to their exif creation date?

I like to browse my photos chronogically directly in the filebrowser and it's a hassle to have to rewrite it manually every time I make them go through a enhancement filter...


Thanks

---

### Post by ssam on 2007-02-18
there a few command line tools for getting and setting exif data. one is exiftool

---

### Post by KhaaL on 2007-02-22
> **ssam said:**
> there a few command line tools for getting and setting exif data. one is exiftool

Thanks! exiftool was exactly what I was looking for, however, I have a hard time to get my pictures done the way i want them... I open my pictures in a image editing program and make a batch filter run, then open a console and go to the folder and run:

exiftool '-DateTimeOriginal>FileModifyDate' ./

The problem is that this program removes the images EXIF data... so what I was thinking is, how do I write a script that records the files EXIF data, and write them to the files once the filtering is done?

Help would be greatly appriciated!

---

### Post by KhaaL on 2007-03-04
Still looking for help on this issue...

---

### Post by Mr. C. on 2007-03-04
Review the documentation for how to run the command and to understand its arguments.

[http://owl.phy.queensu.ca/~phil/exiftool/#running](http://owl.phy.queensu.ca/~phil/exiftool/#running)

MrC

---

### Post by marciano#1 on 2008-06-11
I want to set modified date to created date but I get an error.
Thanks in advance for any help.

# exiftool -FileModifyDate dscf9562.jpg
File Modification Date/Time     : 2008:06:10 16:15:16
# exiftool -createdate dscf9562.jpg
Create Date                     : 2006:12:17 05:58:06

# exiftool -FileModifyDate=DateTimeOriginal dscf9562.jpg
Error converting value for File:FileModifyDate (ValueConvInv)
Nothing to do.

---

