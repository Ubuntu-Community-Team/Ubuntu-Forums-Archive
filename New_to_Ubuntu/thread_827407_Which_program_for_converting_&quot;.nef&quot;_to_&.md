---
title: "Which program for converting &quot;.nef&quot; to &quot;.jpg&quot;?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Papa-san on 2008-06-12
All of our vacation photos are in RAW form. They are .NEF files. Is there a program that can convert these into standard formats? (Hopefully in bulk!) Like if I want to send a dozen to Wal-Mart to make prints.

---

### Post by miss.magenta on 2008-06-12
I do believe there is a RAW import plugin for GIMP.

---

### Post by ajmorris on 2008-06-12
hi there,
I dont know about converting the .nef to .jpg...
but you can use ExifTool to extract .jpg data from the raw .nef file:
[http://www.sno.phy.queensu.ca/~phil/exiftool/](http://www.sno.phy.queensu.ca/~phil/exiftool/)
(the top download on that page is the linux tarball)

then to use it, the syntax is:
```
[FONT=Arial]exiftool -b -JpgFromRaw orignal.NEF > output.jpg[/FONT]
```
[FONT=Arial]
Hope that helps

AJ
[/FONT]

---

### Post by kaptengu on 2008-06-12
I think you can use Imagemagick.
Try:
```
sudo apt-get install imagemagick
```
then
```
convert image.nef image.jpg
```
Should work.

---

### Post by KingTermite on 2008-06-12
You could also install the "imagemagick" package (in repositories) and use the command line tools, like "convert". It looks like "nef" files are supported.

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

main page:
[http://www.imagemagick.org](http://www.imagemagick.org)


edit:  doh! Kaptengu beat me to it!

---

### Post by Papa-san on 2008-06-13
LOL...

Thanks to all of you! I'll let you know how these ideas work...

---

### Post by gcs272 on 2008-10-31
To get imagemagick to work correctly for me (at least for a nikon d40 on  8.10) I had to also install ufraw-batch:

```
sudo apt-get install ufraw
```

---

### Post by madmcphil on 2011-05-08
Download RAWTHERAPEE.... worked like a charm for me.... also does batch processing!

---

### Post by Wim Sturkenboom on 2011-05-08
> **madmcphil said:**
> Download RAWTHERAPEE.... worked like a charm for me.... also does batch processing!I hope Papa-san was not waiting for your answer; after over 2 years he might have forgotten where he stored the photos. :guitar:

---

### Post by I2k4 on 2011-05-08
Reminded me that RawTherapee is available in Linux - I quite like the Windows version and will want to try it in Lubuntu.  So two years late for one user is just in time for another. 

For anybody else, I recommend the UFRAW rather than DCRAW plug-in for GIMP, that make for seamless processing from RAW through JPEG.

---

### Post by azelter on 2011-09-16
This command worked great for me:
ufraw-batch --out-type=jpg *
It will convert all raw files in the current working directory into jpg format.

---

### Post by branduren on 2011-12-29
> **azelter said:**
> This command worked great for me:
ufraw-batch --out-type=jpg *
It will convert all raw files in the current working directory into jpg format.

Thank you, this was very helpful.

---

### Post by oldos2er on 2011-12-29
Closed, necromancy.

---

