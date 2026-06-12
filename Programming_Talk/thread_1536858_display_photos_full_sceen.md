---
title: "display photos full sceen"
date: 2010-07-22
forum: Programming Talk
---

### Post by ssam on 2010-07-22
i have a digital camera tethered to a computer. i want the photos to be displayed on the screen as soon as they are taken, without any intervention.

i am using
```

gphoto2 --capture-tethered

```
to download the photos, which works well.

my first plan was to build an html page with the photos in the capture folder, which is easy enough. i can add a hook script that is triggered after the photo download
```

gphoto2 --capture-tethered --hook-script=/home/sam/bin/photo_page.py

```
now after each photo i get a fresh HTML page with the images as i want them. but in firefox i have to hit refresh to see them.

epiphany has a clever autorefresh that monitors the files on disk, which works well. but it's fullscreen mode still shows a location bar.

if my script triggered an image viewer then i would end up with lots of windows open, and would not, so thats no good.

so any ideas? is there a way to tell firefox to refresh? is there a better browser for this?

---

### Post by ssam on 2010-07-23
i found some gconf settings to hide the location bar.

---

