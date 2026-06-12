---
title: "File info"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by Jose Ponteira on 2013-07-20
good afternoon
I am a photojournalist. Always worked with windows and photoshop.
I tried Linux, Ubuntu 13.4, I loved it. I'm with some difficulty adapting. Introduced in photoshop some information in the photographs taken by me. In linux how can I do?
Write the "file info" (IPTC) with the information that I want and the newspaper requires.

Thanks all who try to help me
José Ponteira

---

### Post by Jose Ponteira on 2013-07-20
Please someone help me. I need insert infornation in a image. Usualy i do it with photoshop by editing the file info. How can i do the same with Linux?

Thankyou
JP

---

### Post by david83 on 2013-07-30
Jose,

Does this helps you [http://www.linux-mag.com/id/8741/]("http://www.linux-mag.com/id/8741/") ?

---

### Post by oldfred on 2013-07-30
I found this. It is in (from terminal):
man exiv2

      exiv2 -pi image.jpg
              Prints the IPTC metadata of the image.

Also many other parameters to edit or change metadata. example:

>        in | insert
              Insert  metadata  from  corresponding *.exv, XMP sidecar (*.xmp)
              and thumbnail files.  Use option -S .suf to change the suffix of
              the input files. Since files of any supported format can be used
              as input files, this command can be used to  copy  the  metadata
              between files of different formats. Modification commands can be
              applied on-the-fly.



Also:
man exiftool
[http://owl.phy.queensu.ca/~phil/exiftool/](http://owl.phy.queensu.ca/~phil/exiftool/)

---

### Post by mbabar96 on 2013-07-30
1. Install Virtual Box
2. Install Windows
3. Install Photoshop
4. use it and enjoy!!

---

### Post by alan-pater on 2013-11-28
Try digiKam or Darkroom. They have a lot of tools for professional photgraphers. For directly editing photos, try the Gimp.

---

