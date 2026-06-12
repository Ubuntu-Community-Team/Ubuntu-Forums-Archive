---
title: "Color to alpha in gimp batch mode (command line) for (python-)script"
date: 2007-10-24
forum: Programming Talk
---

### Post by meastp on 2007-10-24
Case:  color to alpha -effect on an image (for a script)

Anyone who knows how gimp batch mode works, and can help me?

plug-in-colortoalpha

run-mode INT32 Interactive, non-interactive
image IMAGE imput image (unused)
drawable DRAWABLE input drawable
color COLOR Color to remove


The official tutorial is here [http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/) , but I didn't understand what to change in the example script to achieve what I want.


meastp

---

### Post by cwaldbieser on 2007-10-24
I am not sure what your application is, but it seems to me that something like the ImageMagick suite might be easier.  The "-transparent" option to "convert" seeems to do what you are asking, I think.

---

### Post by Unterseeboot_234 on 2007-10-25
I, also like the ImageMagick libraries. Using the command line with a Python script just seems more straight-forward. For an excellent book on the features of  ImageMagick, check out "ImageMagick Tricks" [ ISBN 1-904811-86-8 ] [www.packtpub.com](www.packtpub.com). The GIMP Batch Mode is accomplished by putting a lot of options and all of the options together on one statement. With Python and ImageMagick I do this all the time:

```

# photo_convert.py

import os, sys

"""
A command-line tool to use imagemagick-lib, a free, open-source image 
manipulation software that is especially good doing bulk operations.

Put this script inside a folder of images. use a console window, > cd into that folder and run python photo_convert.py.  

In this case, the images are a folder of my digital camera .jpeg and I want to convert the whole folder of .jpeg into .gif file format.
"""

# -------------------------
"""	use Python method os.listdir() and 
	in this case the (.) directory, or cwd -- current working directory
	and where is the location of launching and running the script.
	"""
dlist = os.listdir('.')

# make an empty list var that will be a command-line list
converto = []

# use an itenerator, look at every item in list dlist

for filenam in dlist:

	# take each dlist element, split it where period is
	temp = filenam.split('.')

	# in this case, we're looking for file_xx.JPG
	# we want the portion of the string at the "."
	# and make it lower case to compare
	temp[1] = temp[1].lower()
	if temp[1] == 'jpg' or temp[1] == 'jpeg':
		converto.append(filenam)

# -------------------------------
""" imagemagick (not part of python) wants:   COMMAND filename filename
	in this case:
	convert filename.jpeg filename.gif
	'convert' is the command, a file.jpeg to a file.gif
"""
# ------------------------------
for filenam in converto:
	#split the filename again to make a name + .gif
	temp = filenam.split('.')

	# code is a string with two string placeholders
	code = 'convert %s %s.gif'

	# define two string values as a tuple
	values = (filenam, temp[0])

	# put the tuple into the code string
	# let the os.system accept the string as a terminal command
	os.system(code % values)

	# safety check
	print code % values

```

That is: using a Terminal, if we have ImageMagick installed, we can type

convert filename.tif xc:none -fill "RGB(rr,gg,bb,aa)" alpha_filename.png
convert alpha_filename.png –channel matte –negate –separate clear_mask_filename.png 

each time for each filename to do the conversion, or use a Python script that will do a wildcard for the files (and renaming). Besides Imagemagick, there is python-vipscc -- both libraries are in the repositories for Gutsy. It is just that I prefer the script with ImageMagick libraries because it is customizable. Python waits for the conversion to finish before doing the next loop. Batch mode in GIMP requires a whole new learning curve.

I'm assuming you have a set of graphic images in front of a bluescreen. The bluescreen drops out. The results is left over on a clear background, ready to composite. And, that too can be ImageMagick.

---

### Post by meastp on 2007-10-25
> 
| Note that using the -transparent option to convert does not quite do the 
| same thing. In, say, a two-color PNG image, consisting of black text on 
| a white bg, invoking 'convert -transparent white' will make the 
| background transparent but leave some gray pixels around the edges of 
| the letters. Gimp's color-to-alpha will make those pixels partially 
| transparent black instead.


From [http://studio.imagemagick.org/pipermail/magick-users/2005-October/016497.html](http://studio.imagemagick.org/pipermail/magick-users/2005-October/016497.html)


The other command suggested

> 
 convert image.png -matte -fill none -fuzz 1% -opaque white  result.png

Just replace that color, and those very close to that color with
a transparent color.


Will just make the areas completely transparent, instead of partially transparent, as the color to alpha in gimp.

Therefore I would like to know how to apply color-to-alpha on an image file from the command line.


meastp

---

### Post by Unterseeboot_234 on 2007-10-25
I did look at the GIMP way of doing this. I can't do it. GIMP uses an internal script called SCHEME. There is an internal console for Python. I get the following to work from the Ubuntu Linux Terminal and because I have ImageMagick libs installed.

```
user@user-desktop: $ **cd** ~/Desktop/picWork/
user@user-desktop:~/Desktop/picWork$ **convert -transparent 'RGB(35,248,85)' cake.tiff cakeNEW.png**

```

Note my 'RGB(35,248,85)' that is my chromakey -- a made-up green in the GIMP that I artificially layered into the background for a working image. I wished I could keep it all in GIMP for you, but this is the only thing that worked for me.

In the GIMP, in the tutorial you point to,  they define a batch (in the Glob def) and then use a command-line. You would save the Glob def somewhere inside the GIMP folders.

---

### Post by meastp on 2007-10-25
No worries. I want to do it in ImageMagick, since there are python bindings/library for it, but I couldn't figure out a way to do it.

If I set colour to black (250,250,250). Will grey be partially transparent?

If it doesn't do what I would like, does convert take an argument to set the specified colout partially transparent (in percent)?

---

### Post by Unterseeboot_234 on 2007-10-25
To do partial transparancy takes the next command in ImageMagick...

composite

If you do a 

convert -help
or
composite -help

you get a long list of the options. In this case, convert and composite, have almost the same list. If you look at my original Python script to this thread, it has a routine to read a whole folder of files, then call the ImageMagick command and write the new filename. So, I'm using Python and I like it better. More versatile.

I never have done a partial mask, which is what you are doing. I do know you can define an RGBA color -- the 'A' is the alpha value. Also, for masking, Black is a bad color, but it depends on your image subject matter.

ImageMagick also comes with 4 mixing modes like xon, xoff, xor and the porter-duff. These are features I've never used. In the book I mentioned, they show examples with a whole paragraph of command lines modifying colors, scale, mortification, and so forth.

---

### Post by meastp on 2007-10-25
thanks, I will have a closer look at it.

You see, I have downloaded the visible earth:blue marble, and found an image of earth's cloud cover, updated every three hours. However, the cloud cover image is not transparent. It is in greyscale (white being the coluds, obviously).

Thats why I want to do this.

---

### Post by cwaldbieser on 2007-10-25
Maybe something like this:

1) Find the dimensions of the cloud image
```

$ identify clouds.png
clouds.png PNG 640x298 640x298+0+0 DirectClass 27kb

```

2) Create a solid image the same size.
```

$ convert -size 640x298 xc:cyan cyan.png

```

3) Create a totally transparent image from the solid one.
```

$ convert cyan.png -transparent cyan clear.png

```

4) Dissolve the original image into the transparent one.
```

$ composite -dissolve 50% clouds.png clear.png out.png

```

That should make the clouds transparent.  

I am not entirely sure that is what you want.  Some actual pictures might make things clearer (no pun intended).

---

### Post by meastp on 2007-10-27
Example:

As the background, one of the images from visible earth: blue marble

[http://visibleearth.nasa.gov/view_set.php?categoryID=2355](http://visibleearth.nasa.gov/view_set.php?categoryID=2355)

As the foreground/overlay (the image I want to convert black to transparent), real time cloud cover:

[http://xplanet.sourceforge.net/clouds.php](http://xplanet.sourceforge.net/clouds.php)

Since compiz does not have fancy dynamic backgrounds yet, I thought of a "live" image of the earth. ;)

---

### Post by cwaldbieser on 2007-10-29
I took a couple of the images you linked and scaled them down.
The world image:
[ATTACH]48312[/ATTACH]
The clouds image:
[ATTACH]48313[/ATTACH]

I made sure the images were the same size.  I then made the cloud image semi-transparent:
```

$ convert -matte clouds.png -channel alpha -fx '0.5' clear_clouds.png

```
If you have a newer version of "convert", you probably want to user the "-alpha on" option instead of "-matte".

I then overlay the clouds on the world to get my final image:
```

composite -matte -compose src-over clear-clouds.png world.png map.png

```
[ATTACH]48314[/ATTACH]

The combination is not perfect, because the world map already seems to include some clouds, though.

---

