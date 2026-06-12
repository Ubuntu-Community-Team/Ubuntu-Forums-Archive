---
title: "How to capture a series of screenshots from a movie"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by uarale on 2008-11-04
The capture tool of VLC media player works fine, but i lacks the options to choose the series of screenshots through the movie, just one capture at a time :(

Do you know how to extract series of images from a movie for illustrating in a review? And all those images combined in a large image finally.

In Windows, do it simply with Media Player Classic.
[IMG]http://www.b3ta.cr3ation.co.uk/data/jpg/thumbs20080928225033.jpg[/IMG]

---

### Post by EdThaSlayer on 2008-11-04
The only way to do that, to my knowledge is to use Avidemux program.It can easily be found in the repositories. You would have to import the movie file(it only works with .avi, .xvid, and the like) and change the frame rate to 1 fps, and then save selection as jpeg(you will need the gtk version of that program though for this "save as jpeg" option).

---

### Post by billgoldberg on 2008-11-04
I don't know, but would also like to know this.

Either way, it shouldn't be that hard to create (that's a presumption), maybe someone will be up to it should it not exist yet.

---

### Post by mindwarp on 2008-11-04
Depends on what you want the interval of screenshots to be, but you can do this using the program 'ffmpeg' and your shell.

Ie:
```

#!/bin/bash
i=0
# Interval is specificed in seconds
interval=800

while [ $? -eq 0 ]
do
     ffmpeg -y -i yourmovie.avi -f singlejpeg -ss $i -vframes 1 -s 640x480 -an shot-$i.jpg
     i=$[$i + $interval]
done

```

---

