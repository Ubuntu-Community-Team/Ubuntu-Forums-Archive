---
title: "ps2pdf chops right half of the file"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-06-11
I seems like ps2pdf does not work for picture post script. I saved one picture from gimp to ps format and then tried to convert it into pdf format using ps2pdf. I always get only left half of the picture in the pdf format, the right half is just gone somewhere. 
I tried using option -sPAPERSIZE=a4 but it just enlarges the picture and nothing more. 
After using gs -v I got that I am using GPL version of the gs but I really don't know the difference between the esp and gpl version. Any help, how to get the right half of the picture in pdf??

---

### Post by _sphinx_ on 2008-06-11
Please reply geeks, I am in urgent need of this thing.

---

### Post by kaibob on 2008-06-11
> **_sphinx_ said:**
> Any help, how to get the right half of the picture in pdf??

I don't have a direct answer to your question, but I do have an alternative suggestion. After opening the picture in Gimp, I would try to save it in TIFF or similar format and then convert the TIFF file to PDF using the convert utility from the Imagemagick package. The following page shows the file formats supported by Imagemagick:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

As an aside, you don't mention the file format of the source picture file. You may be able to convert it directly to PDF without Gimp.

---

