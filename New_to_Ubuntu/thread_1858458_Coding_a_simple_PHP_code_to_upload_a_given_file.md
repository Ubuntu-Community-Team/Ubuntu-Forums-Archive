---
title: "Coding: a simple PHP code to upload a given file?"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by honeybear on 2011-10-12
Hello,

Onto my website, I use apache, I would like that users get a button:

"UPLOAD"

then  it browse on the local, and you click , and then it'll copy it on the root of the upload.php file. 

Please could you help me?  (please no link since I tried most PHP website and it is far too complicated, or not well working)

Thank you so much in advance,

---

### Post by SeijiSensei on 2011-10-12
It's complicated because it is, well, complicated.

The PHP site's [section on uploading files]("http://www.php.net/manual/en/features.file-upload.post-method.php") gives a sample <form> that you can copy and edit to fit your needs.  The form will generate the standard file upload box with the Browse button next to it.

After the content has been POSTed to the site, the relevant information is stored in the two-dimensional array $_FILES.  You extract the needed items from the array and process them as required.  The linked page explains what is contained in the $_FILES array.

---

### Post by stoogiebuncho on 2011-10-12
Yeah, there's no way to do this without doing a little coding.

If you want to learn, there's a great tutorial on working with files in php here:
[http://www.tuxradar.com/practicalphp/8/0/0]("http://www.tuxradar.com/practicalphp/8/0/0")

---

### Post by 11jmb on 2011-10-12
You may get a better audience to field this question in the "Programming Talk" thread

---

### Post by stmiller on 2011-10-12
If it helps, here is a simply php upload form I made to then run an imagemagick command to strip exif data from an uploaded jpeg:

[http://pastebin.com/TSdAS1UF](http://pastebin.com/TSdAS1UF)


It uploads / puts the processed file all in the same local directory where this html page exists.

---

