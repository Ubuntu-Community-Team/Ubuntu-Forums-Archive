---
title: "HOWTO : View and edit RAW image files"
date: 2006-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by jmoisan on 2006-07-20
So you started playing around with the RAW image mode on your digital camera ou dSLR ? Good for you !

Unfortunately, you probably noticed that Ubuntu has no RAW image support whatsoever... gThumb, gqView, Eye of Gnome, none of these image viewers will let you preview your RAW image files.

After hours of research on the subject, I came up with 3 solutions :
[LIST=1]
[*]Wait for Apple Aperture or Adobe Lightroom to be available for Linux :rolleyes: 
[*]Give up and run Photoshop CS2 from a separate Windows partition ](*,) 

OR

[*]**Download and install Bibble Pro for Linux @ [http://www.bibblelabs.com]("http://www.bibblelabs.com/products/bibble/bibble4.html")** 
[/LIST]

[IMG]http://www.bibblelabs.com/images/main_browser_800.jpg[/IMG]

Bibble is a full-featured RAW image editor/converter available for Linux, Windows and Mac. Basically, it does the same work as Aperture or Lightroom, but it is much cheaper and gives you even more control over your images (see attached screenshot).

The latest version of Bibble provides support for all the most popular cameras, including models from Canon, Nikon, Olympus, Kodak, Pentax, Minolta, Epson, Fuji, Sony and Panasonic.

I recommend you to give it a try:

**Bibble Pro 4.8 Trial Edition**
[http://mirror.worldwind.net/pub/bibble/BibblePro/4.8a/bibblepro_4.8.0-1_i386.deb](http://mirror.worldwind.net/pub/bibble/BibblePro/4.8a/bibblepro_4.8.0-1_i386.deb)

**Bibble [COLOR="SlateGray"]Lite[/COLOR] 4.8 Trial Edition**
[http://mirror.worldwind.net/pub/bibble/BibbleLite/4.8a/bibblelite_4.8.0-1_i386.deb](http://mirror.worldwind.net/pub/bibble/BibbleLite/4.8a/bibblelite_4.8.0-1_i386.deb)

Installation procedures (works for any .DEB package file):
[LIST]
[*]Open Terminal
[*]Browse to the directory where you downloaded your .DEB file
[*]Type: ```
sudo dpkg -i package_file.deb
```
[*]Enter the root password when asked
[/LIST]

---

### Post by PuleX on 2006-07-21
Thanks for the tip.  :-)
Bibble does indeed look nice.

I am planning to try RAW with my new Nikon D50, and all the buzz about Lightroom almost convinced me to boot back to Windows just to try it. (I haven't seen anyone run it inside Wine)

But Bibble looks like a good alternative. How does it feel on your desktop (integration, speed)? What did you like and what didn't you like about it?

---

### Post by javierfh on 2006-07-21
Have you tried ufraw?
i guess that it does very nice job. I have Nikon D70 and i can open the raw files with it and looks good enought to me.
Of course i havent tried much and i guess you have to convert them to tiff or other format and then edit them using gimp,gimpshop or cinepaint, but still i think it is quite nice tool considering it comes for free.
Here in this post you can see some screen shots.
[http://www.ubuntuforums.org/showthread.php?t=157065&highlight=ufraw](http://www.ubuntuforums.org/showthread.php?t=157065&highlight=ufraw).

There is one thing though, that im not quite sure and it is the thumbnails in the nautilus. Im not sure, if it was my camera that messed the files or well i still have things to configure in nautilus.

Hope that this helps.


Javi

---

### Post by jmoisan on 2006-07-21
I didn't know about UFRaw or LightZone, thanks for the tip ! I will try them out and come back with more info and a side-by-side comparison.

---

### Post by andy_cowman on 2006-09-07
I'm currently trying out lightzone after using Ufraw&GIMP and  Picasa2. Must say so far I am very impressed, especially at its speed in handling canon CR2 files which in digikam i found to slow to be usable and occasionally picasa would crawl a bit.

Definitly worth a look!

---

### Post by -::Bas::- on 2006-11-14
I have used UFraw in the past, and for me it lacks some options that I do have in Photoshop.
Tonight I'll try out Lightzone, and post my experiences. It seems to be free for linux users. Or am I wrong here?

---

### Post by andy_cowman on 2007-04-18
I know this has been dead a long time but if others search for info on this then they should also try Raw Studio at [http://rawstudio.org/](http://rawstudio.org/) as its really good!

ANdy

---

### Post by tturrisi on 2007-04-18
afaik there are gimp plugins in the repos that enable raw image import.

---

### Post by PuleX on 2007-04-19
I am currently trying out Bibble Pro, as per jmoisan's recommendation. I must say that it looks like a great alternative to (some of) the functionality Lightroom provides on WIndows.

---

### Post by Ted_Smith on 2007-05-13
Anyone wanting to use UFRAW with GIMP ; 

sudo apt-get install gimp-ufraw

or

sudo apt-get install ufraw

for the standalone version

I too am about to try out LightZone. UFRAW with Gimp is fine but seems to lack ease of use when it comes to processing lots of images. I was looking at Aodbe Lightroom but figured there must be a Linux equivalent. LightZone and Bibble both look like worthy contenders. And yes, LightZone is free for Linux users - Windows users take the hit. Good for them ;-) 

Ted

---

### Post by mkoyle on 2007-07-07
another suggestion:  the gnome-raw-thumbnailer package allows nautilus to display thumbnails of raw images.  I have little doubt it works with Nikon and Canon images because it works with my Fuji S5100 (and support for .RAF images used to be really sparse).

--Matthew

---

