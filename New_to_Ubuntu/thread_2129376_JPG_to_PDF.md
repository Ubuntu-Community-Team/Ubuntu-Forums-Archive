---
title: "JPG to PDF"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by czgirb on 2013-03-26
I have a folder contains a 18 JPGs and I wish to print it as 1-PDF file, which contains 18 JPGs.
Is it possible? Please guide me ...

---

### Post by carl4926 on 2013-03-26
You can insert the images into a office document then export as pdf

---

### Post by sea_dawg on 2013-03-26
Try this in terminal:

```
convert *.JPG images.pdf
```

---

### Post by siddharth007 on 2013-03-26
OpenOffice Writer is just what you need.(it comes default with the Ubuntu variant).Put those 18 images in 1 new doc and under *File *option use 'Export as PDF'.

---

### Post by SeijiSensei on 2013-03-26
> **sea_dawg said:**
> Try this in terminal:

```
convert *.JPG images.pdf
```

+1

[Imagemagick convert]("http://www.imagemagick.org/script/convert.php") is an awesome piece of software.  Why bother importing the images into a document one-by-one when you can run a simple command and do it all in a second?

---

### Post by czgirb on 2013-03-26
> **sea_dawg said:**
> Try this in terminal:

```
convert *.JPG images.pdf
```

How can **The Terminal** know which folder's jpg we want to convert to?
I placed the folder in **Download** ... and name it a [B]Book.
[/B]Is the following command is right?
> $ cd Downloads
$ cd Book
$ convert  *.jpg *.pdf
Please correct me if its wrong
THank you

---

### Post by carl4926 on 2013-03-26
No you have to list each image

eg:

```
convert 1.jpg 2.jpg 3.jpg 4.jpg images.pdf
```

---

### Post by schragge on 2013-03-26
If *all *jpg files in the folder are to be converted then globbing will work just as fine:
```
convert ~/Downloads/Book/*.jpg images.pdf
```

---

### Post by SeijiSensei on 2013-03-26
If you use a "glob" like *.jpg, then the files will be processed in alphanumeric order.  If you need to control the order in which the files appear in the PDF, then you must name them appropriately like 1.jpg, etc.

---

