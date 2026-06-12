---
title: "Python batch image confusion."
date: 2012-12-30
forum: Programming Talk
---

### Post by timsdeepsky on 2012-12-30
Hi....I am having a problem understanding the simplest thing in Python....In terminal,,i cd to my script directory....Then call my Python script with this```
./myscript.py
```....
This is my script....
```
#!/usr/bin/python
import Image
import ImageChops

background = Image.open("bg.jpg")
overlay = Image.open("ol.jpg")

background = background.convert("RGBA")
overlay = overlay.convert("RGBA")

new_img = ImageChops.lighter(background, overlay)
new_img.save("new.png","PNG")
```....
This script takes 2 images and stacks them and creates a new image showing everything the 2 single images did,,and it works perfect for me....
But i have changed this code a hundred times,,to try and batch process more than 2 images at a time(like stack 20 images) and it fails....I am not understanding the language i need to simply add more images to the stack....I have searched python sites,and google,and forums and just got more confused with python....Can anyone steer my to a place that will help me understand more what i need to do for this..??..Thanks for any help....
*Release 12.04 (precise) 64-bit*
*Kernel Linux 3.2.0-35-generic*
*GNOME 3.4.2*
*Python version 2.7.3*

---

### Post by gnush on 2012-12-30
I have no idea what you're talking about.

First of all, ImageChops.lighter() doesn't do what you're claiming it does. Either you posted the wrong script, or you're very ambiguous.

Secondly, you're not really explaining how you want to modify the script. Do you want to let the user specify which files should be used? Should it use two files at a time recursively? Do you want it to take files from a directory? Etc.

If you want me to help you, explain in detail what exactly you want to do. Also upload the two original images, and the resulted image, because I want to know how you want the result to look like.

---

### Post by timsdeepsky on 2012-12-30
Sorry for the confusion gnush....
Let me re-write....
I have been working on a python script for batch image stacking....
I need it to stack all my meteor shower images in one stack,,and show all meteors in the final image....I can make this code below work on 2 images perfectly....
```
#!/usr/bin/python
import Image
import ImageChops

background = Image.open("bg.jpg")
overlay = Image.open("ol.jpg")

background = background.convert("RGBA")
overlay = overlay.convert("RGBA")

new_img = ImageChops.lighter(background, overlay)
new_img.save("new.png","PNG")
```
I can take these 2 images,,
[IMG]http://timcline.org/python_script/bg.jpg[/IMG]
[IMG]http://timcline.org/python_script/ol.jpg[/IMG]
And stack them,,and the meteor from each original shows....Like the final image below....
[IMG]http://timcline.org/python_script/new.png[/IMG]
But i need to stack more images than 2(sometimes as many as 50),,and am struggling to find the right code to simply add images to the stack....The "ImageChops.lighter" works for me perfect in my Ubuntu 12.04 box(it is the only way i have found to make the meteors stay bright)....So basically i need help figuring out how to add more images to this stack....Thank you for your help....

---

### Post by gnush on 2012-12-30
Thanks for the clarification. Here's the script; tell me if it's what you were looking for.

```
#!/usr/bin/python

import Image
import ImageChops
import sys
import glob
import os


try:
    dir_images = sys.argv[1]
    dir_results = sys.argv[2]
except IndexError:
    print "No directories specified."

images = []
os.chdir(dir_images)
os.mkdir(dir_results)

for files in glob.glob("*.jpg"): 
    images.append(files)
    if len(images) is 2: 
        print images[0]
        background = Image.open(images[0])
        overlay = Image.open(images[1])
        
        print images[1]
        background = background.convert("RGBA")
        overlay = overlay.convert("RGBA")
        
        ImageChops.lighter(background, overlay).save(dir_results+"result.jpg")
        
        images = []
        images.append(dir_results+"result.jpg")
```Syntax:
```
$ ./script.py directory1 directory2
```For example:
```
$ ./script.py /home/user/pictures/ /home/user/pictures/results/
```This is an updated and working version. You need two directories; directory1 is where the images are, directory2 is where the resulting image will be saved. Directory2 _can not_ exist, because then the program will fail (at least on Windows).

---

### Post by gnush on 2012-12-30
Updated my previous post with a working version.

I spent quite a lot of time on it, but it seems to be working. It's probably far from optimal, so if anyone else has a better solution, by all means provide one.

---

### Post by timsdeepsky on 2012-12-30
Thank you gnush....I am trying it now....

---

### Post by gnush on 2012-12-30
> **timsdeepsky said:**
> Thank you gnush....I am trying it now....

No problem. I've tried it extensively now with 7 images at most, and it has worked every time. If it doesn't work for you, then it's most likely because I'm on Windows. I can't help you further since I'm going on a trip tomorrow and I'm heading to bed now, but you might be able to figure out how to port it to Linux yourself should it not work.

---

### Post by timsdeepsky on 2012-12-30
gnush,
Thanks a million....After i changed the paths for
```
os.chdir(dir_images)
os.mkdir(dir_results)
```
to
```
os.chdir('/home/tim/Desktop/keep' )
os.mkdir('/home/tim/Desktop/keep/final')
```
I was able to get it to work perfectly....
I am not sure what ```
os.mkdir
```actually does,because it just seems to make an empty folder with nothing in it....It did not affect the outcome anyway....
This was the final result and it works well on my Ubuntu 12.04 system....
In terminal i cd to my desktop folder with the script and images..
Then i launch the script with this```
/script_2.py
```....
It launches this script

```
#!/usr/bin/python

import Image
import ImageChops
import sys
import glob
import os


try:
    dir_images = sys.argv[1]
    dir_results = sys.argv[2]
except IndexError:
    print "No directories specified."

images = []
os.chdir('/home/tim/Desktop/keep' )
os.mkdir('/home/tim/Desktop/keep/final')

for files in glob.glob("*.jpg"): 
    images.append(files)
    if len(images) is 2: 
        print images[0]
        background = Image.open(images[0])
        overlay = Image.open(images[1])
        
        print images[1]
        background = background.convert("RGBA")
        overlay = overlay.convert("RGBA")
        
        ImageChops.lighter(background, overlay).save('/home/tim/Desktop/keep/final'+"result.jpg")
        
        images = []
        images.append('/home/tim/Desktop/keep/final'+"result.jpg")


```
Here was the final image after stacking 7 meteor images.
[IMG]http://timcline.org/python_script/finalresult.jpg[/IMG]
I am curious where you go online to learn your python....
Thanks a million....It was perfect....

---

### Post by trent.josephsen on 2012-12-30
Mine's to be used slightly differently than gnush's.

```
#!/usr/bin/python

from sys import argv,exit
from Image import open as iopen # avoid conflict with built-in open()
from ImageChops import lighter

if len(argv) < 2:
    print "Usage: {} file1 [file2 [...]]".format(argv[0])
    exit(1)

files = argv[1:]

composite = iopen(files.pop()).convert("RGBA") # load the first image

for name in files:
    img = iopen(name).convert("RGBA")    # load the next image
    composite = lighter(composite, img)  # and compose it with the rest

last.save("result.jpg", "JPEG")
```

Simpler?

Can't test it because I don't have PIL, so all remaining bugs are left as an exercise to the reader.

---

### Post by gnush on 2012-12-30
> **trent.josephsen said:**
> Mine's to be used slightly differently than gnush's.

After some minor tweaking, I got it running. The problem is the same that I previously had - it only actually merges two images, and ignores the rest. Nevertheless, it was nicely written.

The reason I dug through the directory was because the OP said he was going to merge up to 50 images, so it wouldn't be viable to manually specify each and everyone of them.

---

### Post by trent.josephsen on 2012-12-30
> **gnush said:**
> The reason I dug through the directory was because the OP said he was going to merge up to 50 images, so it wouldn't be viable to manually specify each and everyone of them.

That's the shell's job.

```
$ script.py *.jpg
```

---

### Post by timsdeepsky on 2012-12-30
Thanks for all the help gnush and trent....
Trent,,,,i want to experiment with your method too....Do i just run your script in terminal from the same folder as the images??

---

### Post by trent.josephsen on 2012-12-30
You can run it from anywhere, but instead of giving it the name of the folder to operate on, tell it where to find the files. If you save it in your home directory, you can run it from any directory like so:
```
$ ~/scriptname file1.jpg file2.jpg file3.jpg ...
(or, if you want)
$ ~/scriptname *.jpg
```

It's not uncommon to put custom scripts like this in $HOME/bin or some other appropriate directory, and add it to the $PATH environment variable, so you don't have to provide a path for it every time. For instance, save it as /home/user/bin/compose, and add PATH="$PATH:/home/user/bin" to .bashrc, and then you can call it "compose" no matter what your working directory happens to be, just like ls, cat, etc.

---

### Post by timsdeepsky on 2013-01-08
Thanks for all your help gnush and trent....This was perfect....I am marking this closed....

---

