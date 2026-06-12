---
title: "Shell Script Problem"
date: 2009-07-08
forum: Programming Talk
---

### Post by tm222 on 2009-07-08
I made a shell script to convert images to splash images for GRUB. (.xpm.gz)
They convert to xpm and are compressed into .gz, but the image isn't resized. I am attaching the shell script. It requires ImageMagick, which can be installed using this command without the quotes "sudo apt-get install imagemagick" and gzip, which comes with Ubuntu.

---

### Post by CrazyMonkeyFox on 2009-07-08
I'm sorry i can't help you but i laughed when you said:
> 
It requires ImageMagick, which can be installed using this command without the quotes "sudo apt-get install imagemagick" and gzip, which comes with Ubuntu.


I'm pretty sure that anyone who can help you with your bash script has pretty much mastered "sudo apt-get install" at this stage.

---

### Post by tm222 on 2009-07-08
I was just saying what program it was. Sometimes I don't know what the package name is, but this one is pretty obvious.

---

### Post by stroyan on 2009-07-08
You didn't actually attach your script.

---

### Post by tm222 on 2009-07-08
Sorry, I attached it to the 1st post after editing.

---

### Post by MadCow108 on 2009-07-08
it works with me
maybe the aspect ratio of your image is wrong. then use
-resize 640x480**!**
force the size, otherwise it keeps the aspect ratio

also its more convienient to use command line options instead of read so you can use tab completion

---

### Post by geirha on 2009-07-09
$what should be quoted in your convert command, or else it will fail if it contains spaces or other special characters.
```
convert -resize 640x480! -colors 14 "$what" xpm:- | gzip > "${what%.*}.xpm.gz"
```

---

### Post by tm222 on 2009-07-09
Here is the new download site: [Click here]("http://tinyurl.com/grubsplash")

---

