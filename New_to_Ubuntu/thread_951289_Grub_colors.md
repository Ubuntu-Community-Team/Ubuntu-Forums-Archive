---
title: "Grub colors"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Niniel on 2008-10-18
Hello,

I'm using background images with Grub images (with the help of KGrubEditor), and depending on the image, the Grub menu can be hard to see. Yet changing the colours doesn't seem to have any effect, the menu frame, text and highlighting bar are white and black no matter what. 
Why is that and can something be done about it?
Are, perhaps, the colour settings incorrect?
Thanks.

> splashimage (hd2,0)/grub/splash/batux-tux.xpm.gz
default 1
fallback 3
timeout 10
color white/black black/light-gray

---

### Post by Artemis_Fowl on 2008-10-18
Colors do not stack with splash image. You have to use only one of these two. Not both together. (There should be a warning by kgrubeditor about this, btw)..

Now, if you want to change the background/foreground colors while using a splashimage, read this: [http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

1.3.3 is where explanation about what you want is given. Note however that kgrubeditor doesn't recognise the **background** and **foreground** commands. Thus, if you edit the file, kgrubeditor will silently reject them (aka remove them from the file). You should manually append them in the file after every time kgrubeditor edits the file, if you want them to take effect.

Support for these commands as well as the "colors-do-not-stack-with-splash-images" warning are planned to be included in the next release of KGRUBEditor..

---

### Post by Niniel on 2008-10-26
Ok, thanks.
I just didn't quite understand why you add will support for these commands and still want to add a warning about how splash images and background/foreground colours don't match.

---

