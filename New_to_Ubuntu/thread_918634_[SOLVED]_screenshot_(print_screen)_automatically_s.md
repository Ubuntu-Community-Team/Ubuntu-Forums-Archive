---
title: "[SOLVED] screenshot (print screen) automatically saves png :("
date: 2008-09-13
forum: New to Ubuntu
---

### Post by eru777 on 2008-09-13
Can i make it save automatically on JPEG? thankies (:

---

### Post by iaculallad on 2008-09-13
> **eru777 said:**
> Can i make it save automatically on JPEG? thankies (:

I don't think so. But you can always convert the PNG file to JPG format. Or you could use GIMP to get screenshot giving you the option to any format you want.

---

### Post by SriLankanBoy on 2008-09-13
Press your Print Screen button. A popup will appear. In that pop-up name the file and change the extension from .png to .jpg.

You are good to go :D

---

### Post by scotcella on 2008-09-13
> **SriLankanBoy said:**
> Press your Print Screen button. A popup will appear. In that pop-up name the file and change the extension from .png to .jpg.

You are good to go :D

+1

just type in the file name you want it saved as and add .jpg pr .jpeg at the end of it..

ie screenshot.jpg

easy as abc

---

### Post by eru777 on 2008-09-13
thanks . i dunno why , but i thought it wouldnt accept it if i just switched file extension.

---

### Post by iaculallad on 2008-09-13
> **SriLankanBoy said:**
> Press your Print Screen button. A popup will appear. In that pop-up name the file and change the extension from .png to .jpg.

You are good to go :D


> **scotcella said:**
> +1

just type in the file name you want it saved as and add .jpg pr .jpeg at the end of it..

ie screenshot.jpg

easy as abc

This might work but it will not save the image as a true JPG format file. All it did was to save it using a fake extension. As a sample, I pressed the "Print Screen" key and save the file as "Screenshot.jpg" (as you suggested), and when I issued the command:

```
file Screenshot.jpg
```

Output is:

> Screenshot.jpg: PNG image data, 1280 x 1024, 8-bit/color RGBA, non-interlaced


But when I opened GIMP and took a screenshot and save it as Screenshot.jpg (w/o changing the file extensio manually), the output of:

```
file Screenshot.jpg
```

> jpg: JPEG image data, JFIF standard 1.01

This file contains the true JPG format.

---

### Post by _khAttAm_ on 2009-05-16
This might be of help:
[http://www.khattam.info/2009/05/12/save-screenshots-in-ubuntu-automatically-when-printscreen-key-is-pressed/](http://www.khattam.info/2009/05/12/save-screenshots-in-ubuntu-automatically-when-printscreen-key-is-pressed/)

---

