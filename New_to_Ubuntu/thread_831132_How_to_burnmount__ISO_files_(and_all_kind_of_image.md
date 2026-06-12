---
title: "How to burn/mount  ISO files (and all kind of images, in general)?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Johnnie_Walker on 2008-06-16
I guess there is a dedicated command(scrip) for doing this, but I am asking, whether there is some kind of tool helping us do this more easily(like DaemonTOOLS in Winooz).

---

### Post by rraj.be on 2008-06-16
you ca burn any image using basero or default cd burner.

type this in browser adress 

burn:///


it will open the cd burner.

Just copy and past your image here and click burn.

it will ask you to burn as image or file.

If you want the image to be still image on cd select file.

Else if you want image to be converted to cd select image

---

### Post by renfrew on 2008-06-16
If you're using Gnome try brasero or gnome-baker for ripping/burning iso's
if you're using KDE try k3b for ripping/burning...

There are other packages available but those 3 seem to be the most popular for their respective Desktop Environments.

if you need to mount an iso like you would with Daemon tools or Alcohol in Windows try the following from a terminal:

sudo mkdir /media/loop # just an example .. 
                       # you can call the 
                       # mount point whatever you want to...
mount -o loop -t 1so9660 /path/to/iso/file /media/loop # just make sure
                                                       # that you use the 
                                                       # same mount point 
                                                       # name here...

---

### Post by robertchahine on 2008-06-16
look at this guide 

[www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

it's so easy and works great

and about burning (supposing that you're using ubuntu 8.04)
use brasero (application pannel>sound and video>brasero disc burning or just type brasero in a terminalb)

---

### Post by sam_delta on 2008-06-16
aplications>sound and video>brasero disc burning

on the menu that appears , select "Burn image"

also, check out this link
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

to mount an iso file, create a mounting point (a folder) and  mount it with the following commands
```
cd Desktop
mkdir iso_mount
mount -o loop -t iso9660 myiso.iso iso_mount
```
now all the contect from the iso will be inside iso_mount folder
this is assuming you have the iso in the desktop

if you prefer to mount iso's with a script, check out this link
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

sam

---

### Post by Johnnie_Walker on 2008-06-16
> **robertchahine said:**
> look at this guide 

[www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

it's so easy and works great

and about burning (supposing that you're using ubuntu 8.04)
use brasero (application pannel>sound and video>brasero disc burning or just type brasero in a terminalb)
The script stuff is really kewl and works fine and easy :) 10x, m8!

---

### Post by noobuntu_ger on 2008-06-16
which file types can i mount with the described method ?

---

### Post by cariboo on 2008-06-16
If you have any other type of disk image formats, it would be best to convert them to iso.

Jim

---

### Post by sam_delta on 2008-06-16
> **noobuntu_ger said:**
> which file types can i mount with the described method ?
".iso" files, those files are "image files", image files are files which contain all the data of a drive or CD, 

for example, when you download ubuntu, you download ubuntu.iso, which is the image that contains all the files that ubuntu CD neads, thus, when you burn the iso into a cd, it burns all the data that the image file has.
if your going to use a CD iso image in you own computer, Some people would not like to burn a CD image just to acess the files it has, and thats why we mount iso images.

mounting a CD image is like having a virtual CD inserted into your cd drive, with the contents of the "iso cd image" (the iso file)

i duno if i was clear enough, if you have questions, feel free to ask

sam

---

### Post by robertchahine on 2008-06-17
> **Johnnie_Walker said:**
> The script stuff is really kewl and works fine and easy :) 10x, m8!
glad to hear that

---

### Post by Johnnie_Walker on 2008-06-17
> **noobuntu_ger said:**
> which file types can i mount with the described method ?
No it can't mount .mdf, .mds, .nrg and e.t.c files. I believe there is a convenient way of achieving this.

---

### Post by rraj.be on 2008-06-17
for me too its not mounting.

Its getting the error "Cannot mount iso"

Is there any specific **application** that can monubt

---

### Post by kpkeerthi on 2008-06-17
Try [acetoneiso]("http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html")

> 
**AcetoneISO Features**

    * Mount and Unmount ISO, MDF, NRG (if iso-9660 standard)
    * Convert / Extract / Browse to ISO : *.bin *.mdf *.nrg *.img *.daa *.cdi *.xbx *.b5i *.bwi *.pdi
    * Play a DVD Movie ISO with most used media players
    * Generate an ISO from a Folder or CD/DVD
    * Generate MD5 file of an image
    * Encrypt an image
    * Split image in X megabyte
    * Compress with High Ratio an image
    * Rip a PSX cd to *.bin to make it work with epsxe/psx emulators
    * Service-Menu support for Konqueror
    * Restore a lost CUE file of *.bin *.img


---

### Post by rraj.be on 2008-06-17
i used gisomount and it too worked fine for me.

```
sudo apt-get install gisomount
```

---

### Post by Johnnie_Walker on 2008-06-17
> **rraj.be said:**
> i used gisomount and it too worked fine for me.

```
sudo apt-get install gisomount
```
However, it doesn't work with .mdf and .mds.

---

### Post by bulletxt on 2008-06-17
AcetoneISO2. very simple. [www.acetoneiso.netsons.org/](www.acetoneiso.netsons.org/)

---

### Post by ogromano on 2008-08-19
I would like to know if gisomount's gui can only be called from root or is there a way to change it so that a launcher in main menu can call it directly? I ended up putting gksudo gisomount in the command field of the launcher properties so that it would ask me for the root password everytime I want to mount an ISO, but the strange thing is that it doesn't ask for the password when I put in a CD or when I connect a flash drive... so what's the difference??

---

### Post by dayosh on 2008-08-21
I'm a fairly new user myself, but as far as GmountIso goes, I've found that every time I install it (using the "Add/Remove Programs" feature in your main menu), that it automatically places it within my Main Menu, listed underneath the "Applications -> System Tools" heading.

If you are not seeing the program beneath this heading (or any headings), there is a way to put it into the Applications menu. I shall list that way below:

1. Go to "System -> Preferences -> Main Menu"

2. A window will pop up, showing you all the headings and sub-headings of your menu (i.e. "Accessories," "Games," "Sound & Video," etc."

3. Decide where to put your launcher (under which heading), and select that heading.  All sub-headings will appear in the window to the right.

4. Once your heading is selected, press the "New Item" button.  A "Create Launcher" window will open.

5. Type in a name for the program.  Mine is "Gmount-iso".

6. In the command line, mine also says, "Gmount-iso".  Unsure (being a new user) if you must supply the full file path or not.

7. You can (if you wish) select an icon for your launcher, by clicking the springboard picture and selecting a different one from the browser window which pops up.

8. Once you're all done, click "Close" and the new menu item will be listed.  Be sure the item is checked, or else it won't be listed in the menu.

*Whew!*  Sorry for all the typing.  Anyways, that's the basics.  Hope that helps.  Everything above (as far as I can tell) is correct, but if any of you Ubu vets sees an error, feel free to correct it.  Thanks a heap, and hope that helps!   :)

---

### Post by ogromano on 2008-08-22
That's pretty much  exactly what I did to put it in the Accessories menu. I haven't tried gmountiso yet, only gisomount and when I got it with synaptic, it didn't make any menu shortcuts. The biggest questions I have are why did it install it automatically with root privileges only? And if there's a way to change that from synaptic during or before the install? 

Right now it works except for the fact that because it needs root I had to put gsksudo gisomount on the launcher and so I get asked for my password everytime which is annoying. Thankfully, I don't use it so much. It's more a question of tweaking Ubuntu for future programs I'll install so that they don't also require a password everytime.

---

