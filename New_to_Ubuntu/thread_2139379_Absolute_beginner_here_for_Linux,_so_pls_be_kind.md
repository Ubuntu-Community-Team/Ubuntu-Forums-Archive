---
title: "Absolute beginner here for Linux, so pls be kind"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Hextejas on 2013-04-26
I am trying to get Ubuntu running so I can use it for a home theater PC using XBMC.

Ubuntu is running and I have an external IDE HDD, connected via USB.
The HDD has a lot of junk on it from windows plus multiple partitions.
So, I would like to format it, and partition it for use by XBMC.
pPrior to this I had tried to get OpenElec with XBMC running and that was a futile exercise.

The specs that was recommended to me was a 2 partition HD, #1=250mb, name=boot, FAT32.
#2=what's left,  name=storage, EXT4.

At this point, I am going to leave the internal HDD alone and try and make the USB HD usable.
So, I need to format it as EXT4 and perhaps name it =storage.

How silly of me to think that I would find something relating to disk drives and I could call up a right key menu that would let me do all that. It sure don't look that way unless there is a handy utility that I can't find.

Another thing and I mean no offense but I think I have Gnome 3.x and it's terrible.
All that real estate on the desktop and the app icons are jammed together in a tight column on the left.
you would think that I would be able to click and drag them out into the desktop.
luckily, this PC won't be used much or I would look around for something better.

So, will I need to get out to a command prompt to do the formatting and partitioning ?

and thanks

---

### Post by Feathers McGraw on 2013-04-26
Try using "disk utility" to format the disk.

[This link](http://askubuntu.com/questions/68809/how-to-format-a-usb-or-external-drive) should be useful, if you have any further questions just ask!

Feathers

---

### Post by squakie on 2013-04-26
+1.

For getting icons to the desktop:

go to the very top of the right hand side menu - this will open another larger menu on your screen

if that menu takes up the entire screen, "unmaximize" it to a window and adjust it's size so you have part of the desktop showing

in the menu itself, search for the item(s) you want either by something in the name or by expanding options on the menu, then hold down the left mouse button on the icon and drag it to your desktop.

---

### Post by Mopar1973Man on 2013-04-26
You could just change the desktop environment and move to something that you like to use more. Personally I like LXDE desktop more than Unity or Gnome.

As for setting up hard drives I typically like to use gparted more so. I know gparted is not part of the Ubuntu package but...

```

sudo apt-get install gparted

```

Just fire it up and you can create, delete, move and resize partitions then you can format in any format you wish.

---

