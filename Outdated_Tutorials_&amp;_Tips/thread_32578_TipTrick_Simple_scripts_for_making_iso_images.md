---
title: "Tip/Trick: Simple scripts for making iso images"
date: 2005-05-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Monkey_See on 2005-05-08
I thought I would share a couple really quick scripts that I think are useful for making basic iso images easily.  I made these mostly so I don't need to refer to the man pages for dd and mkisofs every time I used them for making a simple iso.

This one makes an iso image from any directory(s) on the hard drive that you want.  

```
#! /bin/bash

echo -n "File name for iso image (ie. CdName.iso): "
read -e isoName

echo -n "What is(are) the directory path(s) you want use to make the iso (ie. IsoDir1 IsorDir2 ...):"
read -e dirName

mkisofs -o $isoName $dirName
```

Just copy this code into a blank text file with no extension, and save it as something like dir2iso.  Then copy into your /usr/bin/ directory and finally do a "sudo chmod +x /usr/bin/dir2iso" to make it executable

to run, in a terminal "dir2iso" or whatever you decided to name it and follow the prompts.

The second script creates an iso from /dev/cdrom

```
#! /bin/bash
##Creates an iso image from /dev/cdrom

echo -n "File name for iso image (ie. CdName.iso): "
read -e isoName

echo "please wait, reading CD..."
dd if=/dev/cdrom of=$isoName
```

Again copy into an empty text file, and name it something like cd2iso. copy to /usr/bin and "sudo chmod +x /usr/bin/cd2iso"

Thats all, hopefully someone finds these useful beside myself.

Cheers.

---

### Post by Nu-Buntu on 2005-05-08
Monkey_See,

GREAT! Very useful indeed. I thank you for sharing these with us.

One quick question . . .

If the directory is larger than a CD, will K3B burn it across more than one CD? Or will it not create ISOs larger than a CD will hold?

---

### Post by Monkey_See on 2005-05-09
Nu-Buntu,

For the size of the iso I don't think you are really limited to the size that can be created, because I created one that was just under 4 gigabytes and burned to a DVD-R for a test.

As for K3B I'm not so sure, as I've only really played around with it once or twice (right clicking an iso and going "burn iso" is much easier as I mostly just burn plain data cd/dvds anyway) and liked it but just havent really used it.  Although I think I might give it a go when I get home tonight and see if anything comes out of it.

Maybe a cool thing for the scripts would be to check the size of the directory(s) to see if you can burn them safely to a cd/dvd or even split them up into multiple iso images... although that is a bit beyond my abilities at this moment, it might be a fun project.

Glad you liked these :)

Cheers,

Monkey_See

---

### Post by caquino on 2005-05-16
Hi,
   I have written one version of your script using nautilus scripts integration

   Here we go

```
gedit ~/.gnome2/nautilus-scripts/Create\ an\ iso
``` 

paste this code inside gedit

```

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
    mkisofs -o "`basename ${uri:7}`.iso" "${uri:7}" 2>&1 | zenity --progress --pulsate --text="Creating `basename ${uri:7}`.iso"
done

``` 

Now just right click on the directory you want to make a iso from..  Scripts->Create an iso
You can select one or more directories

---

### Post by Heliode on 2005-05-17
Really cool, thanks! I'm sure this'll come in handy!

---

### Post by ejb331 on 2008-03-11
This is similar to the second script. However, if you don't want to write a script/don't know how, you can just use the "dd if=/dev/dvd of=Name_of_DVD.iso"  in the command line.

Here is a how-to [http://wlmtips.com/2008/03/07/saving-a-dvd-iso-in-ubuntu-linux/]("http://wlmtips.com/2008/03/07/saving-a-dvd-iso-in-ubuntu-linux/")

---

