---
title: "Help with converting images."
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Slime mold on 2008-11-22
Hello, ubuntuforums! I have several thousand family photos in the JPG format, and I wanted to switch it to something lossless. I was thinking PNG, but if there is an Open Source format with similar features/compression, please illuminate me!

Anyways, to the core of my question, I was wondering if there was a program in the terminal that would allow me to convert them and then dump the converted versions to folders with the same name as the originals, but at a different location on-disk.

Thank you in advance!

---

### Post by Bodsda on 2008-11-22
Hi. Theres a very simple utility calle imagemagick that should be installed on your system already that can convert all your jpg's to png's

the following commands will convert every file that 'is' a jpg and 'ends' in '.jpg' to a png

first we need to change the directory to the one where your pictures are

```
cd /path/to/mydir/of/pictures
```

you will need to change '/path/to/mydir/of/pictures' to the actual path to your pictures

when your there this next command should convert everything.

```
convert *.jpg *.png
```
I think this should work. If it doesnt post again and someone will help you

Bodsda

---

### Post by Slime mold on 2008-11-22
This worked to an extent. Only two problems: It must will go into sub-folders as well and It needs to preserve the names of the files.

Thank you!

---

### Post by pp. on 2008-11-22
> **Slime mold said:**
> photos in the JPG format, and I wanted to switch it to something lossless.

Once the photos have been written in the JPG format, any losses already have incurred. Converting them back into a lossless format will not recover the lost information.

---

### Post by Slime mold on 2008-11-22
> **pp. said:**
> Once the photos have been written in the JPG format, any losses already have incurred. Converting them back into a lossless format will not recover the lost information.

Of course not. The advantage of a PNG is that you can edit it and save it as much as necessary without worrying about further cumulative damage. I know how it works.

---

