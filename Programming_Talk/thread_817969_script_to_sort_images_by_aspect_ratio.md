---
title: "script to sort images by aspect ratio"
date: 2008-06-04
forum: Programming Talk
---

### Post by Adam590 on 2008-06-04
Any ideas for a simple bash script?

I googled and googled, but I can't figure out how to get the values for the width or height of an image. :confused:

---

### Post by yota on 2008-06-04
It's easy! Well... once you know the trick ;-)

```

yota@box:/share/immages$ **identify** wallpaper_xtal_02_07.jpg 
wallpaper_xtal_02_07.jpg JPEG 1280x1024 1280x1024+0+0 DirectClass 8-bit 150.666kb

```

identify is one of the super-handy command line image handling commands contained in the "imagemagick" package: install it and you are done.

Hope it helps!

---

### Post by Bichromat on 2008-06-04
If you have ImageMagick, use 'identify':
```

$ identify -format '%w %h' ~/image.jpg
540 480

```

See [http://www.imagemagick.org/script/identify.php](http://www.imagemagick.org/script/identify.php)

Edit : hmm, a bit late...

---

### Post by Adam590 on 2008-06-04
Fantastic, thanks!


Edit: well, I've gotten so far as to having the script print the width and height for all of the files in a directory (using a for/do command). Unfortunately, I can't figure out how to set those values as variables in order to do a "if width > height" check for each file.

Any more help would be appreciated. I really do try to find the answers on my own first. :biggrin:

---

### Post by siouzi on 2008-06-04
> **Adam590 said:**
> 
Edit: well, I've gotten so far as to having the script print the width and height for all of the files in a directory (using a for/do command). Unfortunately, I can't figure out how to set those values as variables in order to do a "if width > height" check for each file.


Like this
```

DIMENSIONS=(`identify -format "%w %h" $FILENAME`)

# use like this
WIDTH=${DIMENSIONS[0]}
HEIGHT=${DIMENSIONS[1]}
echo "Width $WIDTH Height $HEIGHT"

```

---

### Post by geirha on 2008-06-04
identify can do a little arithmetic for you, so try this:

```
identify -format "%[fx:w/h] %w %h %f\n" *.png *.jpg | sort -g
```
It should sort by aspect (width/height) first, then width, height and filename.

---

### Post by Adam590 on 2008-06-04
Thanks for all the suggestions. I ended up slogging through it in a different, kind of clunky way before I saw that last post, so I'll have to see if I can streamline the script later.


Anyway, here's what I ended up with:

```
#!/bin/bash

#navigate to image folder first

mkdir ./portraits/
mkdir ./landscapes/

for f in *jpg; do

	identify -format %w "$f" > wvalue
	identify -format %h "$f" > hvalue
	HEIGHT=$(cat hvalue)
        WIDTH=$(cat wvalue)
     	if [ "$HEIGHT" -lt "$WIDTH" ] ; then
		mv ./${f} ./landscapes/
	else 
		mv ./${f} ./portraits/
	fi
done
rm ./wvalue
rm ./hvalue
```

---

### Post by ghostdog74 on 2008-06-04
```

#!/bin/bash

#navigate to image folder first

mkdir ./portraits/
mkdir ./landscapes/

for f in *jpg; do
        set -- $(identify -format "%w %h" "$f")
    	if [ "$2" -lt "$1" ] ; then
		mv ./${f} ./landscapes/
	else 
		mv ./${f} ./portraits/
	fi
done
rm ./wvalue
rm ./hvalue

```

---

### Post by Adam590 on 2008-06-04
Wish I'd seen **set** sooner - I like that one very much. :-D

---

### Post by Domitori3 on 2012-01-25
For those, who need some powerful tool for searching images by resolutions, aspect ratios and such, I wrote an [img-find python]("http://useful-scripts.blogspot.com/2012/01/advanced-image-searching-and-organizing.html") script.

---

