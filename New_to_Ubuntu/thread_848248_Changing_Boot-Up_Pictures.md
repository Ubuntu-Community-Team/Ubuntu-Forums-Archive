---
title: "Changing Boot-Up Pictures"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Johnathannn on 2008-07-03
I was wondering... I have Ubuntu installed on my laptop, when it boots up, I get this black screen that says "Grub Loading" and a few other things, then a countdown on the bottom... After that, there's another screen that says "Starting Up", then I get to the screen that has the Ubuntu Logo and the Loading Bar... Everything works fine, but I was wondering if there was a way that I could get rid of those first two screens (or replace them with some other picture)...THANKS:guitar:

---

### Post by ledzeppelin on 2008-07-03
you can get rid of the countdown, but not start up. this link will show you multiple ways to make the ubuntu startup faster.

link: [http://lirent.net/ubuntu/change-waiting-time-on-grub-menu-boot-select-on-ubuntu.html](http://lirent.net/ubuntu/change-waiting-time-on-grub-menu-boot-select-on-ubuntu.html)

---

### Post by ajgreeny on 2008-07-03
You can put a picture behind the grub menu if you want to; it's known as a grub splash and instructions are below.  They sound a bit complicated but are quite easy if you follow them closely.

GRUB SPLASH

Get splash from net or produce your own picture
 [1] The image needs to be in xpm format.
[2] The image needs to be 640x480 in size.
[3] The image must have only 14 colors.

The xpm file can be left as is or gzipped; grub seems to load gzipped images a bit faster. The thinking on this is that grub can load a gzipped image and decompress it faster than it can load the full size image, due to hard drive access times.

You can still change the foreground and background colors of grub's menu if you're using a splash image, but the image itself won't be affected, only the menu overlay.

Here are a couple ways to get an image in the format you want it:

The quick way: (using convert from imagemagick)

convert -resize 640x480 -colors 14 whatever.xpm newwhatever.xpm && gzip newwhatever.xpm

The slow way: (using gimp)

Open the image you want to use in the gimp, click the "Image" menu, then "Mode", then "Indexed". Select "Generate Optimum Palette:" and enter 14 for the maximum number of colors. It's also recommended that you check the "No Color Dithering" option.
After the conversion, save the file as whatever.xpm. The gimp should automatically create the correct format when it saves the file.

After you've got the image into the correct format and gzipped it (or not, your choice), all you need to do is add it to your /boot/grubfolder and point to it in the config file, menu.lst

Look for :-
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
splashimage (hd0,1)/boot/grub/filename.xpm.gz

The bottom line is the one relating to you new splashimage and the partition in brackets is the same as in the line 
#groot=(hdx,x)

---

### Post by philinux on 2008-07-03
I'm not to bothered about the grub bit, I've got the countdown timer set to 2 seconds.

But i do like this.

[http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468&PHPSESSID=7a9fb9d63cb13a3b004aad9c2c07180a](http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468&PHPSESSID=7a9fb9d63cb13a3b004aad9c2c07180a)

---

### Post by Johnathannn on 2008-07-06
Thanks so much ajgreeny, but when I try moving my image to that folder, it just says permission denied, and it couldn't be copied! Please help!!

---

### Post by Johnathannn on 2008-07-09
How can I put it in the folder??? It keeps saying Permission Denied! How to I pass this? Anyone!?:(

---

