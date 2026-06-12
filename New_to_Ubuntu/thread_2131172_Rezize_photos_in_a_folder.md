---
title: "Rezize photos in a folder"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by czgirb on 2013-03-31
Currently I use Pangolin.
I have a folder, which contains **100 photos**, which taken directly from my **12MP digicam**.
I wish to re-size all photos to **1024x768** ... is Ubuntu able to do that with just one step process?
If YES ... Would you mind to guide me how can we able to do that?
[SIZE=4][B]Thank you


PS:
[/B][/SIZE]Accordance to my friends, in Windows ... they used **AsCDSee** ... but I'm not sure, cos I never use it.

---

### Post by MrSlugInfinite on 2013-04-01
I don't know how to do it exactly, but I will just re-write the things from this link:
[http://bdhacker.wordpress.com/2011/01/04/resize-multiple-images-in-a-folder-batch-image-resize-in-ubuntu/](http://bdhacker.wordpress.com/2011/01/04/resize-multiple-images-in-a-folder-batch-image-resize-in-ubuntu/)

You need to install imagemagick:
```

sudo apt-get install imagemagick

```

Navigate to the directory with the pictures:
```

cd <directory-location>

```

Then, use either of these 2 commands, depending on your intentions:
```

mogrify -resize 50% -format jpg *

```
```

mogrify -resize 800x600 -format jpg *

```
You would replace 800x600 with your dimensions and then .jpg with your image type, obviously.

---

### Post by GrouchyGaijin on 2013-04-01
> **MrSlugInfinite said:**
> I don't know how to do it exactly, but I will just re-write the things from this link:
[http://bdhacker.wordpress.com/2011/01/04/resize-multiple-images-in-a-folder-batch-image-resize-in-ubuntu/](http://bdhacker.wordpress.com/2011/01/04/resize-multiple-images-in-a-folder-batch-image-resize-in-ubuntu/)



I do pretty much the same thing, except I am using graphicsmagick which seems to be basically the same thing as imagemagick.
Since I have to resize frequently I added an alias to my ~/.bash_aliases file
```
alias imgresize='gm mogrify -resize 720x720 *.jpg *.JPG'
```

To invoke the command I open a terminal in the folder that contains all of the .jpg or .JPG files I want to resize. Then I type imgresize and hit enter.

---

