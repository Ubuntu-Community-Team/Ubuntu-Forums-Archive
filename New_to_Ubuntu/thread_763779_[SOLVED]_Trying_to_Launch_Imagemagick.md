---
title: "[SOLVED] Trying to Launch Imagemagick"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Andavane on 2008-04-23
I have been trying to launch the "ImageMagick" program.
The program is listed as installed in the synaptic package manager.
If I type "imagemagick" into a terminal I get the message:
>  andavane@andavane-desktop:~$ imagemagick
bash: imagemagick: command not found
andavane@andavane-desktop:~$ 
I have looked and found what I think is the program in
> /usr/share/ImageMagick-6.2.4
I see there is a folder and two files.
I have put what I think is the correct file into the menu via alacarte but it won't run, as by this stage I am no longer understanding what I am doing.

The reason I am trying to use this is because I have a photo which I want to reduce to a thumbnail to use as a logo.

Thanks in advance for help.

Regards

John

---

### Post by Andavane on 2008-04-23
PS:
Googling my query generates items with script which I simply do not understand.
Regards
John

---

### Post by markjensen on 2008-04-23
Try typing **mogrify** into your terminal.

---

### Post by .nedberg on 2008-04-23
Imagemagick is not a gui program, but programs you can run from the command line.

convert
compose
mogrify

are some of the commands I remember. Have a look at imagemagick.org if you want to learn more.

I you want a gui program try Gimp or Krita

---

### Post by Can+~ on 2008-04-23
Please refer to the manual

```
man imagemagick
```

---

### Post by gug@fnal.gov on 2008-04-23
Hi,
   There should be one gui application that comes with imagemagic, at least in the rpm distro there is (I am not at my Ubuntu machine at the moment). The application is called "display".

bash$ display &

---

### Post by .nedberg on 2008-04-23
> **gug@fnal.gov said:**
> Hi,
   There should be one gui application that comes with imagemagic, at least in the rpm distro there is (I am not at my Ubuntu machine at the moment). The application is called "display".

bash$ display &

Hum, I didn't know about that one. It is in Ubuntu too, but it wasn't as easy to use as Gimp. I would still prefer Gimp if I should make a thumbnail from one image. If I were to make thumbs from several images then I would use imagemagick.Imagemagick is great for scripts and batch processing of images. I use it a lot for my Amarok script (see sig).

---

