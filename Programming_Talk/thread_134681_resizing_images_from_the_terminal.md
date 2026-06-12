---
title: "resizing images from the terminal"
date: 2006-02-22
forum: Programming Talk
---

### Post by alexus on 2006-02-22
I need to resize all the images from my digital camera to thumbnails, and I kind of got it working with this:

```
find . -iname "*.jpg" | xargs -l -i convert -resize 50% -gravity center -crop 150x170+0+0 {} /home/alexis/forsite/thumbs{}
```

of course I'm running that in my forsite directoy -- these are photos getting uploaded to my directory. I like how it makes the thumbnails and it works fine, but I'm just wondering why in the terminal it says

```
convert: unable to open image 'home/alexis/forsite/thumbs/./.cache/1.jpg': No such file or directory.
```

I probably shouldn't be nitpicking but I'm interested -- I just started with linux a few days ago and love it! thanks :grin: Alexis

---

### Post by jerome bettis on 2006-02-22
try apt-get install webmagick , it does exactly what you want.

---

### Post by alexus on 2006-02-22
nope, I tried it, all I want is the command line resize ;-)

this works absolutely perfectly as far as input/output; I'm just curious where the error is

thanks,
Alexis:cool:

---

### Post by hod139 on 2006-02-22
Instead of trying to debug your command, I wrote this quick bash script that should work.  The script lets you define the source folder of the images, the destination folder, and the image type.  It then saves the thumbnail image as filename_thumb.ext in the destination folder.

```

#!/bin/bash

SRC=/home/alexis/forsite/
DEST=/home/alexis/forsite/thumbs
EXT=jpg

for filename in $SRC/*.$EXT
do 
  t=${filename##/*/}       ## strip off prefixes
  t=${t%.$EXT}_thumb.$EXT  ## set name of thumbnail image file to filename_thumb.ext
  convert -resize 50% -gravity center -crop 150x170+0+0 $filename $DEST/$t ## make the thumbnail
done

```

---

