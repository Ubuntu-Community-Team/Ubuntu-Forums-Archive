---
title: "[SOLVED] Reduce picture size to e-mail"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by bob brazie on 2008-11-09
Is there a quick and easy way in 8.10 to reduce the resolution of one or multipliable pictures to either save to disk (less space) or e-mail?

Maybe a plug-in or small application?

I am an old dos/windows user looking to break away.

Thanks in advance. Bob.

---

### Post by keplerspeed on 2008-11-09
I know you can do this in the gimp, after opening the image, save it as a jpg or something, with a lower quality.

CONFIRMED: yes this works. open the gimp, applications>graphics>the gimp then open the appropriate image. then save as, a different file name if you dont want the old one replaces, and reduce the image quality when prompted.

Cheers

---

### Post by zzHanks on 2008-11-09
I don't know about multiple picture re-sizing, but you can re-size pictures in Gimp.

Image > Scale Image...

---

### Post by ad_267 on 2008-11-09
If you install the gimp-plugin-registry package you can use the Gimp for batch processing of images with David's Batch Processor.

---

### Post by fooman on 2008-11-09
there is a plug-in for nautilus that will allow you to resize images from the right-click context menu.  i believe it will do multiple images:

```
sudo apt-get install nautilus-image-converter
```

---

### Post by bob brazie on 2008-11-09
I am not sure what nautilus is and soes it need to be installd before the cammand is given?

Could you please tell me a little more?

Thanks in advance. Bob.

---

### Post by ad_267 on 2008-11-09
> **bob brazie said:**
> I am not sure what nautilus is and soes it need to be installd before the cammand is given?

Could you please tell me a little more?

Thanks in advance. Bob.

Nautilus is the file browser. If you install that package you can select a picture or multiple pictures in the file browser and then right click and select resize. That's definitely the best solution so far, I didn't know about that.

---

### Post by fooman on 2008-11-09
nautilus is the default file browser in ubuntu,  like windows explorer.

in your top panel,  click on places > home folder

that is nautilus.  with the plug-in i referred to above,  you can go to the folder/directory where your pictures are stored. right-click on one and in the menu will be an option to "resize images"

very handy. :)

---

### Post by bob brazie on 2008-11-09
I copyed your code into terminal and it seemed to exicute alright.

However when I open a folder with pictures in it and right click on a picture I do not see the option to sesize.

Do I need to turn it on somehow?

---

### Post by fooman on 2008-11-09
you may have to log out and back in again first...  press alt-ctrl-backspace  to log out.  when you log back in,  the option should be there.

sorry i didn't mention that the first time.

---

### Post by the.phantom on 2008-11-09
add/remove search for 
"showfoto"

with one click i bring up a resize menu, can auto adjust color and bright and crop !
was designed for quick camera photo edit but works great for me and not as complicated as gimp

---

### Post by bob brazie on 2008-11-09
yup, that did the trick!

Thanks again!

---

### Post by JEREMIAHBARLOW on 2010-03-26
> there is a plug-in for nautilus that will allow you to resize images from the right-click context menu. i believe it will do multiple images:

Code:
sudo apt-get install nautilus-image-converter


[B]Fooman hit it right on!  That is a quick and easy way.

I just did ran that code in Ubuntu 9.10 and worked good after I logged out and back in.

Thank You so much.

[/B]

---

### Post by barinov2000 on 2010-10-02
[http://gnome-look.org/content/show.php/Mailpictures?content=115991&PHPSESSID=6](http://gnome-look.org/content/show.php/Mailpictures?content=115991&PHPSESSID=6)
better then anything mentioned above

---

