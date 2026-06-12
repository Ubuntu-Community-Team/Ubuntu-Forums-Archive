---
title: "How To: Add folder image / folder thumbnails like windows xp"
date: 2007-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by JNik on 2007-01-14
I was trying to find a way to easily add images to a folder like windows xp do. I couldn't find anything so I wrote a little program that does that myself.

SetFolderIcon looks for an image called _Folder.jpg_ or _Folder.png_ if it finds one then it changes the folder icon to that image. If it doesn't find an image called Folder.jpg or Folder.png then it looks for photos and videos in the folder and creates a folder image with 4 small thumbnails (like win xp).

**[COLOR="DarkRed"]WARNING[/COLOR]**
**This is my first C# code. That means I had to google every single command/function. It doesn't look nice but it works (most of the times). I'm sure/know there are cases I haven't covered and lot of error handling to be done but the program as is works for ~95% of cases. I have tested the program only under Ubuntu Edgy. I've no idea if it works in older/newer versions.**

**_Instructions:_**
**1.** Extract archive in a folder

**2.** Create a folder in your home directory called .FolerIcons (/home/yourlogin/.FolerIcons) and copy bg.png in it.

**3.** make sure you have mono, imagemagick and zenity installed
- sudo apt-get install imagemagick, mono-runtime, zenity

**4.** edit SetFolderIcon.sh and replace the path to setfoldericon.exe with the one on your system.

**5.** copy SetFolderIcon.sh to /home/yourlogin/.gnome2/nautilus-scripts

**6.** Now you can right click a folder -> Scripts -> SetFolderIcon 

In order to view the folder image you must _restart nautilus_. You can restart nautilus by typing in a terminal: **nautilus -q**
I usually **sudo killall nautilus**

The source code is included in the archive. if you want to complile it use gmcs.

---

### Post by PriceChild on 2007-01-14
Please be careful when using others 3rd party scripts. I do advise you to understand they work first by reading the source and checking you understand it... maybe even compiling the source yourself.

---

### Post by airtonix on 2007-01-14
i dont understand?.....  wit ha default ubuntu dapper install, i can right clikc on a folder, click the big square button that holds the folder icon,......wallah! i can select .....  a custom icon  .....small wonders.  so what is the purpose of your 'thingy' again?  ok...i see now, your genrerating icons from folder contents.

---

### Post by JNik on 2007-01-14
> **airtonix said:**
> i dont understand?.....  wit ha default ubuntu dapper install, i can right clikc on a folder, click the big square button that holds the folder icon,......wallah! i can select .....  a custom icon  .....small wonders.  so what is the purpose of your 'thingy' again?  ok...i see now, your genrerating icons from folder contents.

and it can do a batch of folders... no need to do one by one.

---

### Post by Duranxl on 2008-07-16
This one automatically uses a picture if available.
I have artist music folders, i'm not gonna change them all manually::confused:

---

### Post by cataclysmic on 2009-09-18
Hey folks

I upgraded to Karmic and gnome 2.27 is coming with it.

They changed the metafile system of nautilus to the gvfs system which makes inserting additional meta-infos pretty easy.

I put together a small python script which automatically takes an image from within the folder and sets it to be the folder image.

```

#!/usr/bin/python

import os

cwdir = str(os.popen('pwd').readline()).replace('\n','')

for folder in os.listdir(cwdir):         # iterating through current DIR
    if os.path.isdir(folder) == True:        # check if is folder
        for pic in os.listdir(folder):                # iterating over folder content to find usuable picture
            if pic.lower().find('.jpg') != -1 or pic.lower().find('.gif') != -1 or pic.lower().find('.png') != -1: #checking for image
                os.system('gvfs-set-attribute "'+folder+'" metadata::custom-icon "'+pic+'"')    #setting metadata
                print folder+": using "+pic             #console output if used in console
        

```

Just put the code in a python file in the nautilus script folder.
e.g.:

 ~/.gnome2/nautilus-scripts/Dir Pictures.py

Make it executable.
You can then run it from the right click menu of nautilus.
After running you just have to reload the folder.

It works nicely for me.

Perhaps it's of use for someone.   :popcorn:

---

### Post by ShadowDeath on 2009-09-27
> **cataclysmic said:**
> Hey folks

I upgraded to Karmic and gnome 2.27 is coming with it.

They changed the metafile system of nautilus to the gvfs system which makes inserting additional meta-infos pretty easy.

I put together a small python script which automatically takes an image from within the folder and sets it to be the folder image.

```

#!/usr/bin/python

import os

cwdir = str(os.popen('pwd').readline()).replace('\n','')

for folder in os.listdir(cwdir):         # iterating through current DIR
    if os.path.isdir(folder) == True:        # check if is folder
        for pic in os.listdir(folder):                # iterating over folder content to find usuable picture
            if pic.lower().find('.jpg') != -1 or pic.lower().find('.gif') != -1 or pic.lower().find('.png') != -1: #checking for image
                os.system('gvfs-set-attribute "'+folder+'" metadata::custom-icon "'+pic+'"')    #setting metadata
                print folder+": using "+pic             #console output if used in console
        

```

Just put the code in a python file in the nautilus script folder.
e.g.:

 ~/.gnome2/nautilus-scripts/Dir Pictures.py

Make it executable.
You can then run it from the right click menu of nautilus.
After running you just have to reload the folder.

It works nicely for me.

Perhaps it's of use for someone.   :popcorn:


Ehm... Nice mate really useful, but i have a little problem... Is there anyway to make it look a bit larger? The thumbnail is very small and there is no outline to indicate that this is a folder and not an image like all the others in the folder?

---

### Post by cataclysmic on 2009-10-21
Hi Shadowdeath.

I use it for my movie folders. So I want to see the posters instead of a folder icon. But I consider that idea.

The size of the image, that is pretty simple:
Ctrl + + or CTRL + Scroll up

You can simply zoom the icons in the folder. Nautilus remembers the icon size independently for each folder.

I hope it helps.

PS: I think it might be easier just to tag the folder with an emblem. But there is non for "folder" yet. Maybe you have an idea.

---

### Post by rodrigocorsi on 2009-11-07
New nautilus script!

Unzip ImageFolder.zip on folder "~/.gnome2/nautilus-scripts"
	
I would like to make the icons bigger.
I also want to make an auto-refresh in nautilus. 

```
#!/usr/bin/python

import os, sys
import Image

folders = sys.argv[1:]
im=[]
crop=[]

def create_bg(p):
    bg = Image.open(os.environ["HOME"]+"/.gnome2/nautilus-scripts/bg.png")
    bg.paste(crop[0],(4,35,64,80))
    bg.paste(crop[1],(64,35,124,80))
    bg.paste(crop[2],(4,80,64,125))
    bg.paste(crop[3],(64,80,124,125))
    bg.save(p+"/.folder_bg.thumbnail","PNG")
    os.system('gvfs-set-attribute "'+p+'" metadata::custom-icon ".folder_bg.thumbnail"')

def get_img(p):
    i = 0
    if os.path.isdir(folder) == True:
        for pic in os.listdir(folder):
            if pic.lower().find('.jpg') != -1 or pic.lower().find('.gif') != -1 or pic.lower().find('.png') != -1:
                im.insert(i, Image.open(p+"/"+pic))
                im[i].thumbnail((60, 45))
                crop.insert(i, im[i].crop((0,0,60,45)))
                i=i+1
            if i>=4: 
                create_bg(p)
                return
                
 
for folder in folders:
    get_img(folder)


```

---

### Post by pmorton on 2009-12-05
My albums are arranged in folders by artist and album, and I have a hidden thumbnail .artist.png in each artist folder and another .album.png thumbnail in each album folder. The attached python script, run from the root folder, will walk the tree attaching each thumbnails to the icon of the folder above. Change .png to whatever graphic format you're using.

```
#!/usr/bin/python

import os
from os.path import join

cwdir = str(os.popen('pwd').readline()).replace('\n','')

for root, dirs, files in os.walk(cwdir):
	for name in files:
		if name.lower().find('.png') != -1:
			os.system('gvfs-set-attribute "'+root+'" metadata::custom-icon "'+name+'"')
```

---

### Post by paul kinell on 2010-02-04
Hi, try this guys.
Cover Thumbnailer
[http://software.flogisoft.com/cover-thumbnailer/en/](http://software.flogisoft.com/cover-thumbnailer/en/)
Cheers.

---

### Post by akha666 on 2010-11-17
> **paul kinell said:**
> Hi, try this guys.
Cover Thumbnailer
[http://software.flogisoft.com/cover-thumbnailer/en/](http://software.flogisoft.com/cover-thumbnailer/en/)
Cheers.

thank you
it's very nice solution and so easy I looking for

---

### Post by rndlusr on 2011-06-15
Cover Thumbnailer works nicely. However when I opened a USB drive with lots of movie files it completely froze my machine -- I had to reboot. So I don't recommend enabling it for "other directories" (other than music and images).

---

