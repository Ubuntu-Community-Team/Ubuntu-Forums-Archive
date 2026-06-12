---
title: "BASH: Extracting pieces of a command output."
date: 2010-06-19
forum: Programming Talk
---

### Post by Krupski on 2010-06-19
Hi all,

I'm trying to get a particular part of the output of a program into a variable inside BASH to operate on it.

Here's what I have so far (from hours of Google searching):

First, the program and what it does:

```

root@storage:/dev/shm# identify sv-left.png
sv-left.png PNG 171x180 171x180+0+0 8-bit DirectClass 38.8KiB 0.000u 0:00.000

```

"Identify" is part of Imagemagick and it reads the header of a graphics file and prints the data to STDOUT.

Next, I have a script:

```

#!/bin/bash
DAT=`identify sv-left.png`
for b in $DAT;
do
    echo $b
done

```

...and it properly outputs:

```

root@storage:/dev/shm# sh script
sv-left.png
PNG
171x180
171x180+0+0
8-bit
DirectClass
38.8KiB
0.010u
0:00.010

```

NOW, what I want to do is get and isolate the image size (the third line - "171x180").

This is where I'm stuck.

Any help will be greatly appreciated.

-- Roger

---

### Post by diesch on 2010-06-19
Assuming your file name doesn't contain spaces:

```
DAT=`identify sv-left.png | cut -d ' ' -f 3`
```

---

### Post by kaibob on 2010-06-19
Another way to do what you want is to use the identify -format option. For example, with a PNG file named testfile.png,

> $ width=$(identify -format %w testfile.png) ; echo $width
1280

$ height=$(identify -format %h testfile.png) ; echo $height
960

$ width_height=$(identify -format "%wx%h" testfile.png) ; echo $width_height
1280x960

---

### Post by Krupski on 2010-06-19
> **kaibob said:**
> Another way to do what you want is to use the identify -format option. For example, with a PNG file named testfile.png,

THANK YOU!!! To both **diesch** and yourself!

What I want to do is make a resize script for animated .GIF files and do it with a simple "resize filename.gif 1.5" meaning "make the file "filename.gif" 1.5 times it's normal size.

I know that Imagemagick has resize built in, but I do it a different way (which I found on the web) it produces better results [**[COLOR="Blue"]_LINK_[/COLOR]**](https://fosswiki.liip.ch/display/BLOG/Resizing+animated+GIFs+with+ImageMagick).

All the rest I can figure out.

Thanks again for the help! [IMG]http://three-dog.homelinux.com/phpBB3/images/smilies/thumbspbig.gif[/IMG]

---

