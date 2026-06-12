---
title: "HOWTO: F-Spot - importing from camera's memory card to folder of your choice"
date: 2006-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by aleska on 2006-09-14
This is my very first howto (I think that is meant to be an apology in advance if it stinks).  Here is my [initial post on the subject]("http://www.skarulis.com/?p=34") at skarulis.com.  

**Situation**: you want to use f-spot to import and manage photos instead of gthumb or picasa
**Problem(s)**: 1) when you attach you camera's memory card to your pc, gthumb's photo importer starts not f-spot's 2) using f-spot's import function only allows files to be copied to a default folder /home/$username/Photos and not to the folder of your choice and 3) using Nautilus to delete may not actually free up memory from the card.
**Prerequisite**: you must have f-spot installed and functioning

**HOWTO**:
[B]Solving _Problem 1_.  
[/B]First, to change from gthumb's importer to f-spot's upon connecting your camera's memory card to your pc, you simply need to edit your preferences in System -> Preferences -> Removable Drives and Media.  Go to the Cameras tab.  Under the section Digital Camera, you will probably see
```
gnome-volume-manager-gthumb %h
```
Change this to
```
f-spot-import %h
```
Now, when you connect your camera's memory card to your pc, f-spot will pop up and ask you whether you want to import the photos from the card.  However, please note that you must keep the "Copy files to the Photos folder" selected to actually copy the the picture files from your memory card to your pc.  This raises _Problem 2_, which is that f-spot does not give you an option to copy the files to any other location other than a directory named "Photos" under your home directory (e.g. for me it is /home/aleska/Photos). 

[B]Solving _Problem 2_.
[/B]Assuming you don't already have a folder in your home directory called Photos that you actually want to keep and use, simply create a symbolic link under your home directory called "Photos" that links to the actual folder you want the photos to be saved under.  For me, the folder I save all my photos to is on an attached network storage device that I have mounted to my system (e.g. /mnt/linkstation/Pictures).  So, launch gnome terminal and create the symbolic link as shown below.
```
ln -s /mnt/linkstation/Pictures /home/aleska/Photos
```
Of course, you will need to replace "/mnt/linkstation/Pictures" with the folder on your system to which you want your pictures saved.  Also, you will need to change "aleska" with your username (i.e. your home folder).
So, now you should have things set up so that each time you connect your camera's memory card to your pc, f-spot will launch its import tool and provide you with an easy way to copy files to the picture folder of your choice.  
However, that brings us to _Problem 3_.   Because f-spot doesn't provide us with an option for deleting the originals, you have to launch nautilus so that you can delete the files from your card manually.  As much of a pain as that is, it still beats trying to delete the pictures through your camera, which can often be laborious and a waste of batteries.  The problem is that when you use nautilus to delete those files, it actually creates a trash folder on the card where the files are moved to.  So, basically you aren't really deleting, you are just moving the files on the card from one folder to another.  

[B]Solving _Problem 3_
[/B]The last part of this howto comes from directly from [Ubuntonista at Ubuntu Blog]("http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/").  The steps to enable nautilus to delete for real from the memory card rather than creating and moving the files to a trash folder are simple.
Launch nautilus.  Select Edit -> Preferences.  Click on the behavior tab.  Under the "Trash" section, select the option that reads "Include a Delete command that bypasses Trash".  Et voila!  Now when you locate your picture files on your memory card through nautilus, simply right click on the selection that you are deleting and select "Delete" as opposed to the "Move to Trash" option, and presto bango change-o, files disappear from the memory card.
Good luck and happy f-spot photo managing!

---

### Post by angrylittleman on 2006-09-26
Great howto!  Work excellent on my computer.  Thanks!

---

### Post by Shane10101 on 2006-10-06
Excellent!  Thank you.  

(It's the little things like this that would otherwise add days to my install time!)

Shane

---

### Post by nocturn on 2006-10-06
Just a quick note, I never clean my pictures of the SD card.
I reformat it (using the camera menu) everytime I clean it.

The reason is that the FAT system is very fragile, and doing this has resulted in much less problems with the card.

---

### Post by Sebastral on 2006-12-12
Whohoo, nice howto :). 

Btw; I migrated the ~/.gnome2/f-spot/photos.db from f-spot 0.1.11 (dapper version) to the 0.2.1 in my fresh edgy install and I was shocked not all thumbs were displayed. It appears you just have to scroll trough and restart a few times :)

---

### Post by cullwock on 2006-12-27
Thanks for the HOW-TO.

Btw., just holding Shift while pressing the DEL key will erase the selected pictures permanently, too.

---

### Post by neildarlow on 2007-05-17
For Feisty you will need to replace:```
gnome-volume-manager-gthumb %h
```
with```
f-spot --import %m
```

---

### Post by staubi on 2007-05-17
Hi, thanx for the HowTo!

I had just changed the **"gthumb %h"** for **"f-spot %h"** which of course didn't work..

But has someone a clue on how to prevent F-Spot from saving all files in that stupid **../2007/5/13/** folder structure? Would be great to have all files in the same folder...

Thanx staubi

---

### Post by bvanaerde on 2007-05-26
Nice howto, thanks :)
in reply to staubi: I kinda like the directory structure it creates.

But it would be better if you could choose how your files are stored (choose path, directory structure, filenames, ...)

---

### Post by RichardBronosky on 2007-06-23
Great how-to!

I too would love to change the directory structure used.  I've tried hacking f-spot but it is so freaking complicated it might as well be closed source.  (Especially if you have to use glade to do anything to the UI.)

My next attempt at circumventing the dated directory structure is going to have G-V-M call my bash script which does an 'rsync -av /media/usbdisk/ /myth/gallery/photos/ && rm /media/usbdisk/DCIM/100*/*'  To this script I will add '&& f-spot-import /myth/gallery/photos/' and if I do NOT check copy pictures to photo directory, It will import them into the DB and use their current location.

I keep my photos in the photo gallery of MythTV.

I post back with my results.

---

### Post by graigsmith on 2007-06-24
im having a problem with this,  it works great , i stick in my camera card, it pops up and gets all the jpg images. it's however not getting any of my pentax raw files off my camera.  Any thing with the .pef extension is left on the card, and i have to manually get it off.  is there anyway i can make f-spot get those images off?

---

### Post by justinjstark on 2007-07-10
> **neildarlow said:**
> For Feisty you will need to replace:```
gnome-volume-manager-gthumb %h
```
with```
f-spot --import %m
```

I tried this in feisty. When I plug in my camera it mounts.  Fspot import opens.  I select panasonic from the import dialog and it automatically unmounts my camera.  Gnome throws me a message about unsafe device removal.  Fspot fails with a message "Error connecting to camera."

On the other hand, when I plug in my camera and click ignore when it asks if I want to import photos, it mounts.  I open f-spot manually and go to import and I have the option to import the photos from the mounted camera (labeled "disk").

I have a panasonic fz8.

---

### Post by joe007 on 2007-10-18
Sweet thanks

---

### Post by qhaz on 2007-12-02
When uploading from my Nikon D70S memory card, I prefer to use gqview and for anyone else who would like to do this . . . .  this is how.

Make little script and put in /usr/local/bin

Mine looks like . . . 
 -------------------------------------------------------------------------------
#!/bin/bash
cp -ru "/media/NIKON D70S/DCIM/100ND70S" /home/username/nikon/
gqview /home/username/nikon/100ND70S

---------------------------------------------------------------------------------

I called mine import_gqview.
Then in System/Preferences/Removable Drives and Media/Cameras
in the Command field I put 

/usr/local/bin/import_gqview

---

### Post by Raval on 2008-01-17
> **justinjstark said:**
> I tried this in feisty. When I plug in my camera it mounts.  Fspot import opens.  I select panasonic from the import dialog and it automatically unmounts my camera.  Gnome throws me a message about unsafe device removal.  Fspot fails with a message "Error connecting to camera."

On the other hand, when I plug in my camera and click ignore when it asks if I want to import photos, it mounts.  I open f-spot manually and go to import and I have the option to import the photos from the mounted camera (labeled "disk").

I have a panasonic fz8.

Ubuntu 7.10
Go to system->preferences->removable Drives and Media->Cameras and turn off the auto import feature to the right of Digital Camera.

The camera will mount as a USB device. Now you can  open whatever image program you want and select disk under import to import your photos.

 Also, you can  switch your camera mode from PC to PictBridge (PTP) under Menu->setup->USB mode and pictures will be auto imported.

This should work for many other cameras until a better solution is found.

---

### Post by HunkirDowne on 2008-06-08
Many thanks!!  Your how-to helped me with a different problem: I don't want F-Spot to run automatically-- I'm doing a little "nike" networking with my USB drive and don't want to have to let F-Spot load every time I plug it in to my Ubuntu box (from a WinXP box that doesn't connect to my printer-- long story ;-).

Thanks again.  Write more How-To's!  You're good at it!

---

### Post by Raval on 2008-06-09
> **HunkirDowne said:**
> Many thanks!!  Your how-to helped me with a different problem: I don't want F-Spot to run automatically-- I'm doing a little "nike" networking with my USB drive and don't want to have to let F-Spot load every time I plug it in to my Ubuntu box (from a WinXP box that doesn't connect to my printer-- long story ;-).

Thanks again.  Write more How-To's!  You're good at it!

Happy to help.


For the record in case anyone is wondering, the problem has been solved in Ubuntu 8.04

Cameras do not USB automount. F-spot automatically opens and starts reading the images in the camera and once completed allows you to select what to import. This is when the camera is set to PicBridge.

---

### Post by pmaconi on 2008-07-08
I haven't read this entire thread, so forgive me if this is already posted. The location of the photo folder can be changed by opening gconf-editor and going to apps -> f-spot -> import and changing the storage path to whatever you want. This way the home folder doesn't need to be cluttered with symlinks.

---

### Post by Raval on 2008-07-08
> **pmaconi said:**
> I haven't read this entire thread, so forgive me if this is already posted. The location of the photo folder can be changed by opening gconf-editor and going to apps -> f-spot -> import and changing the storage path to whatever you want. This way the home folder doesn't need to be cluttered with symlinks.

It can be set in Ubuntu 8.04 from within the menu in F-Spot

---

### Post by bford16 on 2008-11-27
...But you still can't change the folder naming convention.  There is a Bugzilla thread about this issue.

[http://bugzilla.gnome.org/show_bug.cgi?id=329040](http://bugzilla.gnome.org/show_bug.cgi?id=329040)

---

### Post by Admoseley on 2009-02-08
> **staubi said:**
> Hi, thanx for the HowTo!

I had just changed the **"gthumb %h"** for **"f-spot %h"** which of course didn't work..

But has someone a clue on how to prevent F-Spot from saving all files in that stupid **../2007/5/13/** folder structure? Would be great to have all files in the same folder...

Thanx staubi

My gripe is similar, I already had a folder structure of /Year/Year_MM_DD, It's great that F-Spot makes these folders based on the day that I took the photo,and not on the day taht I sync my camera... This is exactly what I want, but can I change f-spot settings to match my existing folder structure when I sync my camera?? Many thanks in advanced.

---

### Post by mvpereira on 2010-01-21
Actually I import my pictures using Windows Media Gallery, as I still keep WinXP (for my wife) and Ubuntu for me.
The problem is that I got used to the YYYY-MM-DD model for folder names. I couldn't find yet a replacement for that in Ubuntu, and I don't want to start a different way of naming folders, or I may get my 17000+ photos messed.

Is there any script or software that allows me to import photos and videos from my card, using a custom folder name, and which deletes already imported files?

---

### Post by Raval on 2010-01-23
> **Admoseley said:**
> My gripe is similar, I already had a folder structure of /Year/Year_MM_DD, It's great that F-Spot makes these folders based on the day that I took the photo,and not on the day taht I sync my camera... This is exactly what I want, but can I change f-spot settings to match my existing folder structure when I sync my camera?? Many thanks in advanced.

You can have it the other way around. If you first move your existing photos/folders to another location and then re-import those photos with F-Spot all the old photos would be structured the F-Spot way.

I use to use the Picassa way but I got use to the F-spot was and am happy with it.

Sometimes its a lot easier to accept the way a program does it instead of trying to pull your hair out because it won't do it the way you are accustomed too.

---

