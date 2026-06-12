---
title: "Cropping images"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by PhalanxSec on 2012-08-06
The default image viewer is severely limited and I take 5+ screen shots daily and I need to crop & save each of them. I need to know a of a program or way to do it.

Note if it's a program, please add how to get it, thanks.

---

### Post by Wim Sturkenboom on 2012-08-06
mogrify will do the trick; can't remember how I installed it, probably by installing imagemagick using synaptic.

[http://www.linuxtutorialblog.com/post/cropping-multiple-images-the-same-way-short-tutorial](http://www.linuxtutorialblog.com/post/cropping-multiple-images-the-same-way-short-tutorial)

PS:
I have assumed you always have to crop the same part of the images

---

### Post by vasa1 on 2012-08-06
What is wrong with Shotwell?

---

### Post by pgmer6809 on 2012-08-06
> **PhalanxSec said:**
> The default image viewer is severely limited and I take 5+ screen shots daily and I need to crop & save each of them. I need to know a of a program or way to do it.

Note if it's a program, please add how to get it, thanks.

The Application Pinta will do the job nicely. Looks like its halfway between photoshop and MS Paint.
To install just start Synaptic, (or Ubuntu software Center) and look search for Pinta and then install it.
It will be under the 'graphics' section of your menu.

To crop you use the 'rectangle Select Tool' then Image and crop to selection.

There is probably a way to script something like this using GIMP but I don't know GIMP well enough.
pgmer6809
[IMG]file:///~/Pictures/Pinta-Crop.jpg[/IMG]

Well I tried to paste  an image into the post but it did not give an error and also did not work.

---

### Post by Wim Sturkenboom on 2012-08-06
> **pgmer6809 said:**
> 
Well I tried to paste  an image into the post but it did not give an error and also did not work.You have to put it somewhere on the web :) flickr, imageshack, your own website, ...

---

### Post by vasa1 on 2012-08-06
> **pgmer6809 said:**
> ...
Well I tried to paste  an image into the post but it did not give an error and also did not work.
How did you try that? Just clicking on the paper clip in the top row should guide you. (I hope you haven't disallowed javascript on this site.)

---

### Post by pgmer6809 on 2012-08-07
> **vasa1 said:**
> How did you try that? Just clicking on the paper clip in the top row should guide you. (I hope you haven't disallowed javascript on this site.)

I tried two ways.
1) click the icon in the toolbar. This does not allow an image, instead it allows a link to an image somewhere else on the net. I don't post to flickr, or facebook, or anywhere else. Something in me rebels at the thought of having to create an account on a cloud service just so I can make a post to the forum This forum server should allow upload of images.

2) Changed to advanced editor. This is supposed to be WSYWIG and allow pasting of images as say from the clipboard, That does not seem to work either.

pgmer6809

---

### Post by vasa1 on 2012-08-07
> **pgmer6809 said:**
> I tried two ways.
1) click the icon in the toolbar. This does not allow an image, instead it allows a link to an image somewhere else on the net. I don't post to flickr, or facebook, or anywhere else. Something in me rebels at the thought of having to create an account on a cloud service just so I can make a post to the forum This forum server should allow upload of images.

2) Changed to advanced editor. This is supposed to be WSYWIG and allow pasting of images as say from the clipboard, That does not seem to work either.

pgmer6809
Don't you see something like this?

---

### Post by stinkeye on 2012-08-07
If your editing your screenshots have a look at **shutter** for your screenshot tool.
After taking the screenshot use the inbuilt editor to crop the image
by choosing the edit icon and then crop in the tools dropdown or bottom icon in left panel.

Install through the software centre or install latest build through the shutter ppa
```
sudo add-apt-repository ppa:shutter/ppa
sudo apt-get update
sudo apt-get install shutter
```

---

### Post by stinkeye on 2012-08-07
> **pgmer6809 said:**
> I tried two ways.
1) click the icon in the toolbar. This does not allow an image, instead it allows a link to an image somewhere else on the net. I don't post to flickr, or facebook, or anywhere else. Something in me rebels at the thought of having to create an account on a cloud service just so I can make a post to the forum This forum server should allow upload of images.

2) Changed to advanced editor. This is supposed to be WSYWIG and allow pasting of images as say from the clipboard, That does not seem to work either.

pgmer6809
Use the paper clip icon to attach a a pic (or file) from your computer.

---

### Post by mastablasta on 2012-08-07
and then there is GIMP. which can do a lot more than crop....

---

### Post by SeijiSensei on 2012-08-07
If you spend a lot of time massaging images, you should become familiar with the GIMP.  For some simple editing tasks like resizing and cropping, the KDE graphics application Gwenview is quite easy to use.  Both are available from the standard repositories.

---

