---
title: "photo edit software?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by not_yet on 2008-06-18
what is available to convert a group of photos for sending over the internet?

are there any programs that provide a slide show like elements does?

thanks

---

### Post by Martje_001 on 2008-06-18
You can use imagesmagick in the terminal. Usage:

```
cd /home/user/photo\'s
mkdir converted
convert -quality 100 *.jpg converted/photo.png
```
The first command takes you to the photo-directory on you're hard drive. Then the second command makes the directory 'converted'.

At last the third command converts all jpg photo's (*.jpg) with 100% quality to **converted/photo.png**. The ouput in the folder 'converted' will be something like:

```
photo-1.png
photo-2.png
photo...

etc.
```

---

### Post by not_yet on 2008-06-18
thanks Martje_001:)

---

### Post by Martje_001 on 2008-06-19
I don't know how elements displays slideshows, but you might want to take a look at this:

[https://help.ubuntu.com/community/Photos/Slideshows](https://help.ubuntu.com/community/Photos/Slideshows)

---

### Post by timcredible on 2008-06-19
digikam does slideshows, does TONS of editing and management.  it's as good as photoshop for most people.  install digikam, mpg123, mjpegtools, vorbis-tools, and kipi-plugins from synaptic (and any dependencies it says it needs).  you can add music to your mpeg slideshows too, i use that for putting pictures on dvds.  no transition is the default, change it to 1 or 2 seconds if you want a transition.

---

### Post by cariboo on 2008-06-19
Almost every picture viewing program has a slideshow option, usually it is under the view menu.

Jim

---

### Post by jbaerbock on 2008-06-19
Why in blazes would you want to tell someone to use the terminal to mess with pics, lol? Anyways I use digikam and for any more indepth editting or conversion I use GIMP. GIMP is 100% as good as photoshop if not better in some areas. It does work a tad differently but after getting used to it you can do exactly the same things.

---

### Post by Zill on 2008-06-19
Not exactly FOSS but take a look at [JAlbum]("http://jalbum.net/").  It may do what you want.

---

### Post by fenian on 2008-06-19
Attached is are three  nautilus scripts 1- (imageresize) for resizing images to put on he web or make thumbnails 2-To convert to .png 3-To convert to .jpg. To use put them in /home/username/.gnome2/nautlius-scripts
(make sure they are executable by right clicking the file and selecting properties then the Permissions tab make sure the executing as programs box is checked).
You will also need to have imagemagick installed...

> sudo apt-get install imagemagick

to use a script simply select the file or group of files to convert right click and select the script to use from the scripts option.

---

### Post by fenian on 2008-06-19
> **jbaerbock said:**
> Why in blazes would you want to tell someone to use the terminal to mess with pics, lol?

 If you have a directory of hundreds or thousands of images that you need to convert from one format or another (i.e.:jpg. to .png) or that need to be resized for the web it is more effecient to do this from the command line with imagemagick.

---

### Post by Victormd on 2008-06-19
I'm not on my ubuntu box but is imagemagick in the repos?
I agree with you! This is a great way to convert several images at once.
1. Does it recognize subdirectories as well?
2. Can I use wildcards (i.e., *.png) so that it maintains the same file name in a different format?

---

### Post by fenian on 2008-06-19
Yes it's in the repos

> sudo apt-get install imagemagick

I don't believe it works recursively with directories,you have to convert one at a time or write a script to automate it.
Yes it supports *.png etc...

The commands can be a little confusing you should read the[ basic usage guide here]("http://www.imagemagick.org/Usage/basics/#mogrify")

---

### Post by not_yet on 2008-06-20
just a note...........

I'm always amazed by the "depth" of the replys!:):):)

you guys (gals) rock!

---

### Post by kaibob on 2008-06-20
> **Victormd said:**
> I'm not on my ubuntu box but is imagemagick in the repos?
I agree with you! This is a great way to convert several images at once.
1. Does it recognize subdirectories as well?
2. Can I use wildcards (i.e., *.png) so that it maintains the same file name in a different format?

You can use the mogrify utility from the Imagemagick package to convert a series of image files to another format while retaining the base file name. To do this, open a terminal window and change to the directory that contains the image files. Then, enter the following:

```
mogrify -format tif *.png
```

In the above, change png to the extension of the existing image files and tif to the desired format of the new image files. 

The above command only works on image files in the current directory. The following command works recursively:

```
find /source/folder -iname *.png -type f -exec \
/usr/bin/mogrify -format tif -path /destination/folder '{}' \;
```

You need to change /source/folder, png, tif, and /destination/folder to meet your needs.

---

