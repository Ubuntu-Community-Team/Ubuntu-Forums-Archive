---
title: "Where does linux store files?"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by labchimp on 2013-01-19
So I'm a complete newbie, 

I was wondering where linux stores files when I run it from my usb. If I create a document and save it, is it stored on the usbe drive or somewhere else on my hard drive. Thanks.

---

### Post by irv on 2013-01-19
Linux uses a /home/[your user name] and then different files type go in different folder under that. Take for example picture and photos go in the picture folder. All your downloads go in a Download folder, all your documents go in Documents folder.
Now if you open a file from a USB drive and then go to save it after making changes it will save it to the same place where you opened it. The best way to do this is when you save a file do a save as and then watch where it is going.
[ATTACH]230347[/ATTACH]

---

### Post by KdotJ on 2013-01-19
That's true in general. But not all things go to your home directory (or subdirectory of). For example, when you install software it may distribute files in a few places. This kind of thing sometimes seems all a bit odd to a new user.

If you want to know a bit more about the file system, check out [this wikipedia article]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") about where stuff generally gets put.

---

### Post by grahammechanical on 2013-01-19
> If I create a document and save it, is it stored on the usbe drive or somewhere else on my hard drive.

The document would not be stored on the hard drive unless you specifically directed the application to store it on the hard drive.

If we use the Ubuntu utility Startup Disk Creator we get an option to set aside a portion of the USB space where we can store files. It is called a USB with persistence. If we do not create a USB live disk with persistence then the USB stick will act like a CD and anything stored will be lost unles we specifically stored it somewhere else.

Regards.

---

### Post by irv on 2013-01-19
> **labchimp said:**
> So I'm a complete newbie, 

I was wondering where linux stores files when I run it from my usb. If I create a document and save it, is it stored on the usbe drive or somewhere else on my hard drive. Thanks.

I'm sorry, I read your post wrong. If you are just running the live OS from the USB that is where it will save your files.
The advice I gave was if you have installed Ubuntu on your hard drive.
When you shut down your live session it will ask you to save any files or changes you made to that session before shutting down. This will take awhile to shut down because it has to do some writing to the USB OS.

---

### Post by MyTinFoilHat on 2013-01-19
In addition to what others have mentioned above, I'd like to offer this, which is helping me (also a noobie) understand the directory structure.  This is a link to tuxfiles.org, specifically their page on Linux Directory Structure. Here you will find a summary for each of the folders you're likely to see and wonder about:  [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by ajgreeny on 2013-01-19
As others have said, if you are using a live usb with persistence, any files you create and save will be on the usb, but not in a form that you can read from windows or another OS.

All saved files from a persistent live usb will be saved in folders the encrypted file named **casper.rw** which you will see on the usb.  It is possible to mount and open that using another linux OS.

See [http://ubuntuforums.org/showthread.php?t=1980406](http://ubuntuforums.org/showthread.php?t=1980406)

---

### Post by labchimp on 2013-01-19
Ok thank you so much guys, I used the ubuntu installer and allowed linux to take up as much space as possible. I'll be running this as a dual boot so my files will get saved on the stick...Got it!

---

### Post by jerome1232 on 2013-01-19
> **labchimp said:**
> Ok thank you so much guys, I used the ubuntu installer and allowed linux to take up as much space as possible. I'll be running this as a dual boot so my files will get saved on the stick...Got it!

FYI, Ubuntu can see, and write to Windows NTFS partitions just fine. The reverse is not true. Often people use a separate "data" partition formated as NTFS to share data between Ubuntu and Windows.

---

### Post by MadmanRB on 2013-01-19
> **labchimp said:**
> Ok thank you so much guys, I used the ubuntu installer and allowed linux to take up as much space as possible. I'll be running this as a dual boot so my files will get saved on the stick...Got it!

Except when you actually install Ubuntu of course, then you can store files into Ubuntu on your actual hard drive.
Keep in mind most files are stored in your home directory, the windows equivalent if coming from 7 is users.
Actually figuring out how linux is set up via its directory structure will be easy for a windows 7 user as windows 7 is very simular to Ubuntu/linux in its folder layout for the most part.

---

