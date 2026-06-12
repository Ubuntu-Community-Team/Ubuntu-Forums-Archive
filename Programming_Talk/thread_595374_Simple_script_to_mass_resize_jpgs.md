---
title: "Simple script to mass resize jpgs??"
date: 2007-10-28
forum: Programming Talk
---

### Post by Guardian-Mage on 2007-10-28
I am looking for the easiest and quickest way to take 46 .jpg photos, resize them, say to 25%, and reduce their quality to say 65% and then save them. Is the best way with a shell script or C++ or what and how do I go about doing it?

---

### Post by arsenic23 on 2007-10-28
I use phatch for such things:
[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by jordilin on 2007-10-28
I would go for some scripting with Perl using the Image::Magick module. It should be quite easy. There are already some tools in the repositories to do that if I remember. If you want to do some Perl, just check this web page
[http://www.imagemagick.org/script/perl-magick.php](http://www.imagemagick.org/script/perl-magick.php)

---

### Post by aysiu on 2007-10-28
I would also recommend ImageMagick. It doesn't even have to be a script. It can just be a one-line command (supposing all the images are in the one folder).

---

### Post by meatpan on 2007-10-28
I Agree with the above users, and would like to add that the 'convert' program (which is from the ImageMagick package) will get the job done.  convert -resize <file-1.jpg> <file-resized.jpg>

---

### Post by rustalot on 2007-10-28
You should take a look here: [http://www.imagemagick.org/Usage/]("http://www.imagemagick.org/Usage/") . It will be very helpful.

I imagine if you want to resize all jpegs in directory foo, you could do something like 
```

#!/bin/bash
#script to resize jpegs

for i in *.jpeg
do
   (resize command)
done

```

If there's something wrong with my bash, let me know...

---

### Post by dwhitney67 on 2007-10-28
I uses this script to make my thumbnails:

[PHP]#!/bin/bash

FILES=*.jpg

mkdir -p ./thumbs

for i in $FILES
do
        echo "Processing image $i..."

        /usr/bin/convert -thumbnail 200 $i ./thumbs/thumb.$i

done
[/PHP]

---

### Post by trak87 on 2007-10-28
Install ImageMagick and do it as a one line command as aysiu says. I just tested this and it works:

```
for i in *.jpg; do convert -resize 25% -quality 75 "$i" "$i"_smaller.jpg; done
```

You will end up with a new set of files with the word "smaller" in them. To be on the safe side, back up the original images before doing running the command.

---

### Post by ThinkBuntu on 2007-10-28
Use the "mogrify" command in imagemagick. Works very, very well.

---

### Post by Guardian-Mage on 2007-10-29
for i in *.jpg; do convert -resize 450x400! -quality 65 "$i" thumb/"$i"; done


works fine thanks

---

